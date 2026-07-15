TRIGGER: HTTP endpoint returns unexpected status code, times out, auth fails despite correct credentials, or payload contract mismatch between services
OUTPUT: detailed — request path traced per hop, failure category, auth/payload check result, fix with successful request verification
SKIP: frontend network inspection in browser (use chrome-devtools-debugging instead)

---

# Network / API Debugging

Use for backend HTTP failures: unexpected status codes, timeouts, auth errors, malformed payloads, CORS (from server perspective), retry storms, and contract mismatches between services.

For frontend network inspection use `chrome-devtools-debugging`. This skill covers the server and client-to-server layer.

## When to Use

- API returns unexpected status code (400, 401, 403, 500, 503).
- Request times out or hangs indefinitely.
- Auth fails despite credentials appearing correct.
- Payload sent/received does not match expected schema.
- Behavior differs between environments (dev/staging/prod).
- Downstream service calls fail silently.
- Rate limiting or quota errors appear unexpectedly.

## Process

### 1. Isolate the Request
- Reproduce the failure with the smallest possible request (curl, httpie, or minimal code).
- Capture: method, URL, headers (redact secrets), body, response status + body + headers, latency.
- Confirm failure is reproducible before investigating.

### 2. Classify the Failure

| Signal | First suspect |
|---|---|
| 4xx from own service | Request validation, auth middleware, routing |
| 4xx from downstream | Auth token, rate limit, schema mismatch, wrong endpoint |
| 5xx from own service | Unhandled exception, missing dependency, DB error |
| 5xx from downstream | Downstream instability — check their status page |
| Timeout | Network path, slow query, missing connection pool limit, deadlock |
| Connection refused | Wrong host/port, service not running, firewall |
| Intermittent failure | Retry logic, circuit breaker, load balancer sticky sessions, race |

### 3. Trace the Request Path
- Identify every hop: client → gateway/proxy → service → downstream → DB.
- Check logs at each hop for the correlation ID / request ID.
- Confirm where the failure originates — do not assume the first error surface is the root.

### 4. Check Auth Separately
- Token present? Correct format (Bearer, Basic, API key header)?
- Token expired? Check expiry, clock skew between services.
- Correct scope/permissions for the endpoint?
- If OAuth: check token exchange, not just the access token.

### 5. Validate Payload Contract
- Compare actual request body/headers against the API schema (OpenAPI/Swagger, source code).
- Check content-type header matches body encoding.
- Check for encoding issues (double-encoded JSON, wrong charset).
- For binary/multipart: verify boundary and part headers.

### 6. Check Environment-Specific Config
- Base URL, port, protocol (http vs https) correct for the environment?
- TLS cert valid and trusted?
- Proxy or VPN required?
- Firewall rule blocking the port?

### 7. Apply Minimal Fix
- Fix only the confirmed root cause.
- Do not add retry logic to mask a correctness bug.
- Do not increase timeouts without understanding the cause of slowness.

## Partial Findings Rule

If root cause is unconfirmed, still report:
- Exact failure signal (status, error message, latency).
- Hops traced and what each returned.
- Failure category identified or narrowed.
- Best hypothesis with supporting evidence.
- Next diagnostic step.

## Output Contract

Every response must include:

- **Failure signal**: method, URL (sanitized), status/error, latency.
- **Request path traced**: each hop and what was observed.
- **Failure category**: from the classification table, or "not yet classified."
- **Auth check result**: pass / fail / not applicable.
- **Payload check result**: valid / invalid / not checked.
- **Fix applied** (if any): exact change + verification (successful request after fix).
- **Next step** if unresolved.

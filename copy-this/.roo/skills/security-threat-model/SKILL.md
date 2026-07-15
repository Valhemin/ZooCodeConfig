TRIGGER: feature involves auth, payments, uploads, external integrations, multi-tenant data, secrets, or user-generated content
OUTPUT: compact — trust boundaries, auth/authz, input validation, secret handling, rate limits, data exposure, audit logging assessed
SKIP: internal admin tools with no external access or sensitive data

---

# Security Threat Model

Use for auth, payments, uploads, external integrations, multi-tenant data, secrets, or user-generated content.

Check:
- Trust boundaries.
- Authentication and authorization.
- Input validation and output escaping.
- Secret handling.
- Rate limits and abuse cases.
- Data exposure and tenant isolation.
- Audit/logging implications.

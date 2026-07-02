# Zoo Pro Setup

Bộ cấu hình drop-in cho Zoo Code/Roo-style coding agent trong VS Code.

Mục tiêu của setup này là biến Zoo Code thành workflow coding agent chất lượng cao cho nhiều loại dự án khác nhau: từ bắt đầu project mới, viết spec, thiết kế kiến trúc, implement production-ready, debug, self-review, đến kiểm tra readiness trước khi release.

## Cấu trúc

```text
.
├── .roomodes
├── .roo/
│   ├── mcp.json
│   ├── rules/
│   ├── rules-spec/
│   ├── rules-implement/
│   ├── rules-debug/
│   ├── rules-lead/
│   ├── skills/
│   ├── skills-spec/
│   ├── skills-implement/
│   ├── skills-debug/
│   └── skills-lead/
├── .rooignore
├── AGENTS.md
├── DESIGN.md
├── templates/
├── MODE_GUIDE.md
├── README_INSTALL.md
├── CHANGELOG.md
└── CORE_EXTRACTION_REPORT.md
```

## Modes

Setup này dùng 4 mode chính:

| Mode             | Vai trò                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------ |
| 📋 Spec Pro      | Tạo spec, docs, architecture, requirements, implementation plan, test plan, risk analysis  |
| ⚒️ Implement Pro | Implement theo spec/tasks, tự review từng scope, verify liên tục, hướng production-ready   |
| 🐞 Debug Pro     | Nắm context, reproduce lỗi, tìm root cause, fix nhỏ nhất an toàn, thêm regression coverage |
| 🧭 Lead Pro      | Dùng cho project lớn: chia phase, điều phối Spec/Implement/Debug, giữ roadmap và readiness |

## Cách dùng trong project

Giải nén folder setup này, sau đó copy toàn bộ file/folder bên trong vào root project cần dùng.

Ví dụ root project sau khi copy:

```text
your-project/
├── .roomodes
├── .roo/
├── .rooignore
├── AGENTS.md
├── DESIGN.md
├── templates/
└── ...
```

Sau đó reload VS Code/Zoo Code. Không cần chạy lệnh setup.

## Flow khuyên dùng

### Bắt đầu project mới

```text
Use Lead Pro. Start a new production-ready project: [mô tả dự án]. Collect context, identify critical unknowns, create a delivery roadmap, and delegate Spec Pro to produce the first spec pack before implementation.
```

### Tạo spec cho feature

```text
Use Spec Pro. Create a production-ready spec pack for [feature]. Clarify only critical gaps, research current official docs when uncertain, create requirements, architecture, tasks, checklist, and consistency analysis.
```

### Implement feature

```text
Use Implement Pro. Implement docs/specs/[feature]/10-tasks.md scope by scope. Self-review each scope, verify with project-native checks, mark tasks done only after actual completion, and continue until production-ready or I stop you.
```

### Debug bug/issue

```text
Use Debug Pro. Reproduce or narrow the issue, identify root cause with evidence, fix the smallest safe scope, add regression coverage where practical, and verify.
```

## Nguyên tắc chính

* Quality-first, không minimal-answer-first.
* Luôn collect đủ context trước khi sửa code.
* Không bịa kết quả test/build/lint.
* Không báo production-ready nếu chưa verify.
* Không tự ý rewrite rộng nếu không cần.
* Không thêm dependency nếu không có lý do rõ ràng.
* Khi không chắc về API/library/framework, phải research bằng nguồn mới nhất.
* UI/web phải dựa vào `DESIGN.md`, design tokens, visual QA, accessibility và responsive behavior.
* Tasks phải rõ ràng, có acceptance criteria, có file path, có dependency và verification.
* Implement theo scope nhỏ, self-review sau từng scope, không dồn tới cuối mới review.

## MCP

Project MCP nằm ở:

```text
.roo/mcp.json
```

Mặc định nên giữ ít MCP để tránh tốn token và giảm rủi ro tool sai. Các MCP thường dùng:

* `context7`: tra docs/version-specific API.
* `fetch`: đọc URL/research web.
* `sequential-thinking`: hỗ trợ phân tích nhiều bước.
* `playwright`: visual QA/UI testing nếu bật.
* `figma`: lấy design context nếu project có Figma.
* `serena`: semantic code navigation cho repo lớn.
* `github`/`gitlab`: issue/PR/CI khi cần.

Chỉ bật MCP thật sự cần cho project.

## Ghi chú khi commit

Nên commit:

```text
.roomodes
.roo/
.rooignore
AGENTS.md
DESIGN.md
templates/
MODE_GUIDE.md
README_INSTALL.md
CHANGELOG.md
CORE_EXTRACTION_REPORT.md
```

Không commit:

```text
.env
.env.*
API keys
local credentials
node_modules/
build output
cache
logs
local database
```

## Lưu ý

Đây là setup generic cho nhiều dự án, không phụ thuộc team/framework cụ thể. Có thể chỉnh `AGENTS.md`, `DESIGN.md`, `.roo/rules-*`, `.roo/skills-*` theo convention riêng của từng repo.

Nếu project có convention đặc biệt, nên ghi vào `AGENTS.md` hoặc thêm rule/skill riêng trong `.roo/`.

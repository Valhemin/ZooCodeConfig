# Zoo Pro Setup v6 — Drop-in Project Setup

Bản này được đóng gói để dùng theo kiểu copy/paste giống `.claude`.

## Cách dùng nhanh

1. Giải nén `zoo-pro-setup-v6.zip`.
2. Mở folder `zoo-pro-setup-v6/` vừa giải nén.
3. Copy **toàn bộ file/folder bên trong** vào root project muốn dùng.
4. Reload VS Code / Zoo Code.
5. Chọn mode trong Zoo Code:
   - 📋 Spec Pro
   - ⚒️ Implement Pro
   - 🐞 Debug Pro
   - 🧭 Lead Pro

Không cần chạy lệnh setup nào.

## Sau khi copy, root project sẽ có

```text
your-project/
  .roomodes
  .roo/
    mcp.json
    rules/
    rules-spec/
    rules-implement/
    rules-debug/
    rules-lead/
    skills/
    skills-spec/
    skills-implement/
    skills-debug/
    skills-lead/
  .rooignore
  AGENTS.md
  DESIGN.md
  templates/
    SPEC_PACK/
  README_INSTALL.md
  MODE_GUIDE.md
```

## Những file Zoo tự nhận

- `.roomodes`: 4 custom modes cấp project.
- `.roo/rules/`: global project rules.
- `.roo/rules-{mode}/`: rule riêng từng mode.
- `.roo/skills/` và `.roo/skills-{mode}/`: skills dùng khi task cần.
- `.roo/mcp.json`: MCP config cấp project.
- `.rooignore`: file/folder nên tránh đọc/sửa.

## File hỗ trợ

- `AGENTS.md`: project instruction tổng quan cho agent.
- `DESIGN.md`: design system ground truth cho UI/web project.
- `templates/SPEC_PACK/`: template spec pack để Spec Pro tham khảo hoặc tạo docs mới.
- `MODE_GUIDE.md`: hướng dẫn dùng từng mode.
- `CHANGELOG.md`: thay đổi chính của bản setup này.
- `CORE_EXTRACTION_REPORT.md`: phần lõi được rút từ các workflow SpecKit/review command.

## Flow khuyên dùng

### Dự án mới

```text
Use Lead Pro. Start a new production-ready project: [mô tả]. Collect context, identify critical unknowns, create a delivery roadmap, and delegate Spec Pro to produce the first spec pack before implementation.
```

### Feature mới

```text
Use Spec Pro. Create a production-ready spec pack for [feature]. Clarify only critical gaps, research current official docs when uncertain, create requirements, architecture, tasks, checklist, and consistency analysis.
```

### Implement

```text
Use Implement Pro. Implement docs/specs/[feature]/10-tasks.md scope by scope. Self-review each scope, verify with project-native checks, mark tasks done only after actual completion, and continue until production-ready or I stop you.
```

### Debug

```text
Use Debug Pro. Reproduce or narrow the issue, identify root cause with evidence, fix the smallest safe scope, add regression coverage where practical, and verify.
```

## Ghi chú

Bản này không chứa `.roo/commands/`, không phụ thuộc team/project cụ thể, và không cần slash command. Workflow quan trọng đã được hấp thụ vào rules, skills và templates.

# ClaudeKit Engineer - Learning & Use Cases

Repo này dùng để **học cách sử dụng ClaudeKit Engineer** và tổng hợp các **use case thực tế** khi làm việc với AI-powered development workflow.

## Mục đích

- Tìm hiểu 76+ skills có sẵn trong ClaudeKit Engineer
- Thực hành các workflow phát triển phần mềm với AI agents
- Tổng hợp use cases thực tế cho từng loại task
- Tham khảo nhanh cách dùng từng skill

## ClaudeKit là gì?

**ClaudeKit Engineer** là bộ framework cho [Claude Code](https://claude.com/product/claude-code) — CLI tool của Anthropic. Nó mở rộng Claude Code với 76+ specialized skills, hooks, và agent orchestration patterns, biến Claude thành một team phát triển phần mềm hoàn chỉnh.

- [Claude Code Docs](https://docs.claude.com/en/docs/claude-code/overview)
- [ClaudeKit Docs](https://docs.claudekit.cc)
- [ClaudeKit CLI](https://github.com/mrgoonie/claudekit-cli)

## Tài liệu trong repo

| File | Nội dung |
|------|----------|
| [summary.md](./summary.md) | Tổng hợp toàn bộ 76+ skills, phân loại theo nhóm |
| [frontend-usecase.md](./frontend-usecase.md) | 10 use cases thực tế chi tiết với workflow step-by-step |
| [docs/](./docs/) | Documentation kỹ thuật (architecture, code standards, roadmap) |
| [plans/](./plans/) | Implementation plans và reports |

## Quick Start

### Cài đặt
```bash
npm install -g claudekit-cli
mkdir my-project && ck new --dir my-project --kit engineer
```

Hoặc thêm vào project có sẵn:
```bash
cd /path/to/project && ck init --kit engineer
```

### Bắt đầu dùng
```bash
claude                                          # Mở Claude Code
/ck:cook "add user dashboard"                   # Implement feature end-to-end
/ck:fix "login bug" --auto                      # Fix bug tự động
/ck:code-review --pending                       # Review code
/ck:deploy --auto                               # Deploy
```

## Skills Overview (10 nhóm chính)

Xem chi tiết tại [summary.md](./summary.md).

| Nhóm | Skills tiêu biểu | Mục đích |
|------|-------------------|----------|
| **Core Development** | `cook`, `plan`, `fix`, `debug` | Implement features, fix bugs, debug |
| **Code Quality** | `code-review`, `security`, `test`, `simplify` | Review, audit, testing |
| **Frontend** | `frontend-design`, `ui-styling`, `tanstack`, `threejs` | React, Tailwind, 3D web |
| **Backend** | `backend-development`, `databases`, `better-auth` | API, database, auth |
| **DevOps** | `deploy`, `devops`, `git`, `ship` | Deploy, CI/CD, git workflow |
| **Design** | `design`, `ai-artist`, `stitch`, `copywriting` | Brand, UI gen, copy |
| **Docs** | `docs`, `docs-seeker`, `preview`, `journal` | Documentation, visual aids |
| **Project Mgmt** | `project-management`, `team`, `kanban`, `retro` | Tracking, collaboration |
| **Specialized** | `chrome-devtools`, `mcp-builder`, `mobile-development` | Browser, MCP, mobile |
| **Utility** | `scout`, `find-skills`, `skill-creator`, `worktree` | Scouting, tooling |

## Use Cases phổ biến

Xem chi tiết tại [frontend-usecase.md](./frontend-usecase.md).

| Use Case | Lệnh | Mô tả |
|----------|-------|--------|
| Feature end-to-end | `/ck:cook add-dashboard --auto` | Plan → code → test → review tự động |
| Fix bug production | `/ck:fix api-timeout --auto` | 6-step diagnosis pipeline |
| Redesign UI component | `/ck:scout` → `/ck:ui-styling` → `/ck:frontend-design` | Giữ logic, đổi UI theo design system |
| Security audit | `/ck:security --stride --owasp --fix` | Scan + auto-fix vulnerabilities |
| Parallel team | `/ck:team cook "feature" --devs 3` | 3 agents code song song |
| Research | `/ck:research "topic" --max 5` | 4-phase technical research |
| Deploy | `/ck:deploy --auto` | Auto-detect → deploy 15+ platforms |
| Sprint retro | `/ck:retro` | Data-driven report từ git metrics |

## Cấu trúc Project

```
├── .claude/                # ClaudeKit configuration
│   ├── hooks/              # Automation hooks
│   ├── skills/             # 76+ specialized skills
│   └── rules/              # Development rules & workflows
├── docs/                   # Technical documentation
├── plans/                  # Implementation plans & reports
├── summary.md              # Skills summary (tổng hợp 76+ skills)
├── frontend-usecase.md     # 10 use cases thực tế
├── CLAUDE.md               # Project instructions for AI agents
└── README.md               # File này
```

## Nguyên tắc phát triển

- **YAGNI** — You Aren't Gonna Need It
- **KISS** — Keep It Simple, Stupid
- **DRY** — Don't Repeat Yourself

## Tài nguyên

- [Claude Code](https://claude.com/product/claude-code) | [Docs](https://docs.claude.com/en/docs/claude-code/overview)
- [ClaudeKit Docs](https://docs.claudekit.cc) | [ClaudeKit CLI](https://github.com/mrgoonie/claudekit-cli)
- [ClaudeKit Discord](https://claudekit.cc/discord)
- Gemini API key (cho AI skills): https://aistudio.google.com/apikey

## License

MIT — see [LICENSE](LICENSE)

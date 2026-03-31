# ClaudeKit Engineer - Skills Summary

Tổng hợp **76+ skills** covering toàn bộ software development lifecycle.

---

## 1. Core Development

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **cook** | `/ck:cook [feature]` | Orchestrator chính — tự động plan → code → test → review |
| **plan** | `/ck:plan [scope]` | Lên kế hoạch implementation với dependency detection |
| **fix** | `/ck:fix [issue]` | Pipeline sửa bug 6 bước: Scout → Diagnose → Assess → Implement → Verify → Finalize |
| **debug** | `/ck:debug [issue]` | Debug hệ thống với 10 kỹ thuật (tracing, hypothesis, binary search...) |
| **research** | `/ck:research [topic]` | Nghiên cứu kỹ thuật 4 pha với Gemini + WebSearch |
| **bootstrap** | `/ck:bootstrap [type]` | Scaffold dự án mới từ đầu |
| **brainstorm** | `/ck:brainstorm [problem]` | Brainstorm giải pháp với phân tích trade-off |

**Usecase thực tế:**
- `/ck:cook add-payment-integration` — Triển khai tính năng thanh toán end-to-end
- `/ck:fix login-returns-500 --auto` — Tự động phân tích và fix bug login
- `/ck:plan migrate-to-postgresql --parallel` — Lên kế hoạch migration song song
- `/ck:bootstrap saas-app --fast` — Khởi tạo SaaS project nhanh

---

## 2. Code Quality & Security

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **code-review** | `/ck:code-review [#PR\|COMMIT\|--pending]` | Review adversarial 3 giai đoạn |
| **security-scan** | `/ck:security-scan` | Quét secrets, dependencies, OWASP patterns |
| **ck-security** | `/ck:security [scope] --fix` | Audit STRIDE + OWASP với auto-fix |
| **test** | `/ck:test [context]` | Chạy unit/integration/e2e tests |
| **simplify** | `/simplify` | Review code đã thay đổi, tối ưu reuse & quality |

**Usecase thực tế:**
- `/ck:code-review #42` — Review PR #42 trên GitHub
- `/ck:security --stride --fix` — Audit bảo mật và tự fix vulnerabilities
- `/ck:test ui https://localhost:3000` — Test UI với browser automation
- `/ck:code-review --pending` — Review tất cả changes chưa commit

---

## 3. Frontend Development

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **frontend-development** | `/ck:frontend-development` | React/TypeScript với Suspense, MUI v7, TanStack |
| **frontend-design** | `/ck:frontend-design` | Tạo UI polished từ designs/screenshots |
| **ui-styling** | `/ck:ui-styling` | shadcn/ui + Tailwind CSS components |
| **tanstack** | `/ck:tanstack` | TanStack Start, Form, AI integration |
| **threejs** | `/ck:threejs` | 3D web apps (556 examples, VR/XR) |
| **react-best-practices** | `/ck:react-best-practices` | Performance optimization từ Vercel Engineering |

**Usecase thực tế:**
- `/ck:frontend-design` + screenshot — Replicate UI từ Figma/screenshot
- `/ck:ui-styling` — Xây design system với shadcn/ui + dark mode
- `/ck:threejs` — Tạo 3D product viewer cho e-commerce

---

## 4. Backend & Database

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **backend-development** | `/ck:backend-development` | NestJS, FastAPI, Django, Go |
| **databases** | `/ck:databases` | Schema design, queries, migrations (Postgres, MongoDB) |
| **payment-integration** | `/ck:payment-integration` | Stripe, Polar, SePay, Paddle, Creem |
| **better-auth** | `/ck:better-auth` | Authentication (OAuth, 2FA, passkeys, RBAC) |

**Usecase thực tế:**
- `/ck:backend-development --nodejs` — Xây REST API với NestJS
- `/ck:databases` — Thiết kế schema và optimize queries
- `/ck:payment-integration` — Tích hợp Stripe checkout + webhooks
- `/ck:better-auth` — Thêm auth system với OAuth + 2FA

---

## 5. DevOps & Deployment

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **deploy** | `/ck:deploy [target]` | Auto-detect deploy lên 15+ platforms |
| **devops** | `/ck:devops` | Cloudflare Workers, Docker, GCP, K8s |
| **git** | `/ck:git` | Git operations + conventional commits + security scan |
| **ship** | `/ck:ship` | Pipeline: merge → test → review → commit → push → PR |

**Usecase thực tế:**
- `/ck:deploy vercel --auto` — Deploy lên Vercel tự động
- `/ck:ship` — Ship feature từ branch → PR một lệnh
- `/ck:git --split` — Auto-split commits theo type/scope

---

## 6. Design & Creative

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **design** | `/ck:design` | Brand identity, logo (55 styles), CIP mockups, slides, banners |
| **ai-artist** | `/ck:ai-artist` | Generate images (129 prompts, Ukiyo-e, cyberpunk, cinematic...) |
| **ai-multimodal** | `/ck:ai-multimodal` | Vision analysis, image/video/speech generation |
| **stitch** | `/ck:stitch` | AI UI design generation → Tailwind/HTML export |
| **copywriting** | `/ck:copywriting` | Conversion copy, headlines, email, landing pages |
| **shader** | `/ck:shader` | GLSL fragment shaders cho procedural graphics |

**Usecase thực tế:**
- `/ck:design --brand` — Tạo brand identity hoàn chỉnh
- `/ck:ai-multimodal --vision` — Phân tích screenshot UI để extract design
- `/ck:stitch` — Generate UI từ text prompt → export code

---

## 7. Documentation & Knowledge

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **docs** | `/ck:docs` | Analyze codebase, init/update documentation |
| **docs-seeker** | `/ck:docs-seeker` | Tìm docs library/framework qua context7.com |
| **llms** | `/ck:llms` | Generate llms.txt cho AI-friendly docs |
| **journal** | `/ck:journal` | Viết journal phân tích changes & reflections |
| **preview** | `/ck:preview` | Visual explanations, slides, diagrams (HTML/Markdown) |

**Usecase thực tế:**
- `/ck:docs --init` — Khởi tạo docs cho project mới
- `/ck:docs-seeker nextjs app router` — Tra docs Next.js mới nhất
- `/ck:preview --html --diagram auth-flow` — Tạo interactive architecture diagram

---

## 8. Project Management & Collaboration

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **project-management** | `/ck:project-management` | Track progress, update plans, generate reports |
| **team** | `/ck:team [template]` | Orchestrate Agent Teams song song |
| **kanban** | `/ck:kanban` | Task visualization board |
| **retro** | `/ck:retro` | Sprint retrospective với git metrics |
| **plans-kanban** | `/ck:plans-kanban` | Plans dashboard với progress tracking |

**Usecase thực tế:**
- `/ck:team cook "payment feature" --devs 3` — 3 agents code song song
- `/ck:retro` — Tạo sprint retro report từ git data
- `/ck:project-management` — Review tiến độ dự án

---

## 9. Specialized & Integration

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **chrome-devtools** | `/ck:chrome-devtools` | Browser automation (Puppeteer) |
| **mcp-builder** | `/ck:mcp-builder` | Xây MCP servers cho LLM integration |
| **shopify** | `/ck:shopify` | Shopify apps, Liquid templates, Polaris UI |
| **mobile-development** | `/ck:mobile-development` | React Native, Flutter, Swift, Kotlin |
| **web-testing** | `/ck:web-testing` | Playwright, Vitest, k6 (e2e/load/a11y) |
| **sequential-thinking** | `/ck:sequential-thinking` | Deep reasoning cho complex problems |
| **claude-api** | `/ck:claude-api` | Build apps với Claude API/SDK |
| **mintlify** | `/ck:mintlify` | Documentation sites với Mintlify |
| **remotion** | `/ck:remotion` | Video creation trong React |
| **media-processing** | `/ck:media-processing` | FFmpeg + ImageMagick + RMBG |

---

## 10. Utility Skills

| Skill | Lệnh | Mô tả |
|-------|-------|--------|
| **scout** | `/ck:scout` | Fast codebase scouting song song |
| **find-skills** | `/ck:find-skills` | Tìm và cài skill mới |
| **skill-creator** | `/ck:skill-creator` | Tạo custom skills mới |
| **loop** | `/loop 5m /ck:test` | Chạy skill lặp lại theo interval |
| **schedule** | `/schedule` | Cron jobs cho remote agents |
| **worktree** | `/ck:worktree` | Git worktree isolation |
| **context-engineering** | `/ck:context-engineering` | Monitor context usage & optimize tokens |
| **coding-level** | `/ck:coding-level` | Set level cho tailored output |
| **problem-solving** | `/ck:problem-solving` | Systematic techniques khi bị stuck |

---

## Common Workflows

**Feature mới end-to-end:**
```
/ck:cook add-user-dashboard --auto
```
→ Tự động: plan → implement → simplify → test → review

**Debug production bug:**
```
/ck:fix api-timeout-on-large-queries --auto
```
→ Scout codebase → Diagnose root cause → Fix → Verify

**Parallel team implementation:**
```
/ck:team cook "e-commerce checkout" --devs 3
```
→ 3 agents code song song trong worktrees riêng biệt

**Security audit trước release:**
```
/ck:security --stride --owasp --fix
```
→ Scan → Report → Auto-fix vulnerabilities

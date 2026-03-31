# ClaudeKit Engineer - Use Cases

Các usecase thực tế và workflow đề xuất khi sử dụng ClaudeKit skills.

---

## Use Case 1: Redesign UI Component theo Design System hiện tại

**Bài toán:** Có sẵn component (full logic + UI) từ nguồn khác, muốn redesign UI cho match design system hiện tại mà giữ nguyên logic.

### Skills cần dùng

| Bước | Skill | Mục đích |
|------|-------|----------|
| 1. Scan design system | `/ck:scout` | Map toàn bộ design tokens, components, patterns đang dùng trong project |
| 2. Phân tích UI gốc | `/ck:ai-multimodal --vision` | Đọc screenshot component gốc → extract layout, spacing, colors, typography |
| 3. Match design system | `/ck:ui-styling` | Áp dụng shadcn/ui + Tailwind tokens đúng theo design system hiện tại |
| 4. Generate UI mới | `/ck:stitch` hoặc `/ck:frontend-design` | Tạo UI mới từ prompt/screenshot → export Tailwind/HTML |
| 5. Optimize | `/ck:react-best-practices` | Đảm bảo performance patterns (memo, lazy load, Suspense) |
| 6. Clean up | `/simplify` | Tối ưu code quality, loại bỏ redundancy |
| 7. Review | `/ck:code-review --pending` | Adversarial review kết quả cuối cùng |

### Workflow chi tiết

**Step 1 — Hiểu design system hiện tại:**
```
/ck:scout design-system --fast
```
→ Scan nhanh codebase để hiểu tokens (colors, spacing, typography), component library đang dùng (shadcn, MUI, custom...), naming conventions.

**Step 2 — Phân tích component gốc:**
```
/ck:ai-multimodal --vision
```
→ Cung cấp screenshot component gốc. AI sẽ extract: layout structure, color palette, spacing, typography, interactive states. Giúp hiểu component cần những gì về mặt visual.

**Step 3 — Redesign với design system:**
```
/ck:ui-styling
```
→ Map visual elements từ Step 2 sang design tokens hiện tại. Thay thế custom CSS bằng Tailwind utilities + shadcn/ui components. Đảm bảo dark mode, responsive, accessibility.

**Step 4 — Generate hoặc implement UI:**

*Option A — Nếu muốn AI generate:*
```
/ck:stitch
```
→ Describe component cần tạo → AI generate UI → export Tailwind/HTML code.

*Option B — Nếu muốn replicate chính xác:*
```
/ck:frontend-design
```
→ Cung cấp screenshot + design specs → tạo polished component match pixel-perfect.

**Step 5 — Optimize & Review:**
```
/simplify
/ck:code-review --pending
```
→ Clean up code → adversarial review để catch issues.

### Tips

- **Giữ logic tách biệt khỏi UI**: Tách business logic vào custom hooks, chỉ redesign phần render/JSX
- **So sánh visual**: Dùng `/ck:chrome-devtools` để screenshot trước/sau, đảm bảo không mất functionality
- **Test UI**: Dùng `/ck:test ui` để verify interactive states hoạt động đúng sau redesign

---

## Use Case 2: Feature mới End-to-End

**Bài toán:** Implement tính năng mới hoàn chỉnh từ A-Z.

### Workflow
```
/ck:cook add-feature-name --auto
```

### Skills tự động kích hoạt
1. `/ck:plan` — Lên kế hoạch implementation
2. `/ck:research` — Nghiên cứu technical approach (nếu cần)
3. Code implementation
4. `/simplify` — Clean up code
5. `/ck:test` — Chạy tests
6. `/ck:code-review` — Review code

---

## Use Case 3: Fix Bug Production

**Bài toán:** Bug trên production cần fix nhanh và chính xác.

### Workflow
```
/ck:fix api-returns-500-on-large-payload --auto
```

### Pipeline 6 bước tự động
1. **Scout** — Scan codebase tìm related code
2. **Diagnose** — Root cause analysis
3. **Assess** — Đánh giá impact và approach
4. **Implement** — Fix code
5. **Verify** — Chạy tests, đảm bảo không regression
6. **Finalize** — Clean up và summary

---

## Use Case 4: Security Audit trước Release

**Bài toán:** Kiểm tra bảo mật trước khi deploy production.

### Workflow
```
/ck:security --stride --owasp --fix
```

### Kết quả
- STRIDE threat model analysis
- OWASP Top 10 vulnerability scan
- Auto-fix cho các findings có thể fix tự động
- Report với severity ratings

---

## Use Case 5: Parallel Team Implementation

**Bài toán:** Feature lớn cần nhiều agents làm song song.

### Workflow
```
/ck:team cook "e-commerce checkout system" --devs 3
```

### Cơ chế
- Mỗi agent làm việc trong git worktree riêng → không conflict
- Task coordination qua Claude Tasks
- Lead agent merge results cuối cùng

---

## Use Case 6: Nghiên cứu Technical Decision

**Bài toán:** Cần đánh giá technology choice hoặc architecture decision.

### Workflow
```
/ck:research "compare PostgreSQL vs MongoDB for e-commerce" --max 5
```

### Kết quả
- 4-phase research report (Scope → Gather → Analyze → Report)
- Pros/cons comparison
- Recommendation với evidence

---

## Use Case 7: Tạo Documentation cho Project

**Bài toán:** Project mới hoặc project thiếu docs.

### Workflow
```
/ck:docs --init
```

### Tự động tạo
- `project-overview-pdr.md`
- `code-standards.md`
- `codebase-summary.md`
- `system-architecture.md`
- `deployment-guide.md`

---

## Use Case 8: Brand Identity & Design System

**Bài toán:** Cần tạo brand identity hoàn chỉnh cho project mới.

### Workflow
```
/ck:design --brand --auto
```

### Kết quả
- Logo (55 styles)
- Color palette & typography
- Design tokens
- Component library guidelines
- CIP mockups (50 deliverables)

---

## Use Case 9: Sprint Retrospective

**Bài toán:** Review sprint vừa qua với data-driven insights.

### Workflow
```
/ck:retro
```

### Metrics tự động thu thập
- Commit frequency, LOC changes
- Hotspot files (most changed)
- Code churn analysis
- Health indicators

---

## Use Case 10: Deploy Multi-platform

**Bài toán:** Deploy project lên hosting platform.

### Workflow
```
/ck:deploy --auto
```

### Hỗ trợ 15+ platforms
Vercel, Netlify, Cloudflare, Railway, Render, Heroku, GitHub Pages, GCP, AWS, Digital Ocean, Fly.io...

Auto-detect project type → recommend platform → configure → deploy.

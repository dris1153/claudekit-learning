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
→ Scan nhanh codebase để hiểu tokens (colors, spacing, typography), component library đang dùng, naming conventions.

**Step 2 — Phân tích component gốc:**
```
/ck:ai-multimodal --vision
```
→ Cung cấp screenshot component gốc. AI extract: layout structure, color palette, spacing, typography, interactive states.

**Step 3 — Redesign với design system:**
```
/ck:ui-styling
```
→ Map visual elements sang design tokens hiện tại. Thay custom CSS bằng Tailwind utilities + shadcn/ui components. Đảm bảo dark mode, responsive, accessibility.

**Step 4 — Generate hoặc implement UI:**

*Option A — AI generate:*
```
/ck:stitch
```

*Option B — Replicate chính xác:*
```
/ck:frontend-design
```

**Step 5 — Optimize & Review:**
```
/simplify
/ck:code-review --pending
```

### Tips
- **Giữ logic tách biệt khỏi UI**: Tách business logic vào custom hooks, chỉ redesign phần render/JSX
- **So sánh visual**: Dùng `/ck:chrome-devtools` để screenshot trước/sau
- **Test UI**: Dùng `/ck:test ui` để verify interactive states

---

## Use Case 2: Feature mới End-to-End

**Bài toán:** Implement tính năng mới hoàn chỉnh từ A-Z.

```
/ck:cook add-feature-name --auto
```
→ Tự động: plan → implement → simplify → test → review

---

## Use Case 3: Fix Bug Production

**Bài toán:** Bug trên production cần fix nhanh và chính xác.

```
/ck:fix api-returns-500-on-large-payload --auto
```
→ Scout → Diagnose → Assess → Implement → Verify → Finalize

---

## Use Case 4: Security Audit trước Release

```
/ck:security --stride --owasp --fix
```
→ STRIDE threat model + OWASP Top 10 scan + auto-fix

---

## Use Case 5: Parallel Team Implementation

```
/ck:team cook "e-commerce checkout system" --devs 3
```
→ 3 agents code song song trong git worktrees riêng biệt

---

## Use Case 6: Nghiên cứu Technical Decision

```
/ck:research "compare PostgreSQL vs MongoDB for e-commerce" --max 5
```
→ 4-phase research report với pros/cons + recommendation

---

## Use Case 7: Tạo Documentation cho Project

```
/ck:docs --init
```
→ Tự động tạo project-overview, codebase-summary, code-standards, system-architecture

---

## Use Case 8: Brand Identity & Design System

```
/ck:design --brand --auto
```
→ Logo (55 styles) + color palette + design tokens + CIP mockups

---

## Use Case 9: Sprint Retrospective

```
/ck:retro
```
→ Data-driven report từ git metrics (commits, LOC, hotspots, churn)

---

## Use Case 10: Deploy Multi-platform

```
/ck:deploy --auto
```
→ Auto-detect project → recommend platform → configure → deploy (15+ platforms)

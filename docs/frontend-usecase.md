# Frontend Use Cases

Tổng hợp các use case thực tế cho frontend development khi sử dụng ClaudeKit skills.
Mỗi use case bao gồm bài toán, skills cần dùng, và workflow step-by-step.

---

## Use Case 1: Redesign UI Component theo Design System hiện tại

**Bài toán:** Có sẵn component (full logic + UI) từ nguồn khác (thư viện, project cũ, hoặc copy từ internet), muốn redesign lại UI cho match design system hiện tại mà giữ nguyên toàn bộ business logic.

### Skills cần dùng

| Bước | Skill | Mục đích |
|------|-------|----------|
| 1. Scan design system | `/ck:scout` | Map toàn bộ design tokens, components, patterns đang dùng trong project |
| 2. Phân tích UI gốc | `/ck:ai-multimodal --vision` | Đọc screenshot component gốc → extract layout, spacing, colors, typography |
| 3. Context + Redesign | `/ck:ui-styling` | Cung cấp path code → AI tự đọc, phân tích, redesign bằng components/tokens có sẵn |
| 4. Generate UI mới (optional) | `/ck:stitch` hoặc `/ck:frontend-design` | Chỉ khi cần tạo UI từ đầu, không redesign component có sẵn |
| 5. Optimize | `/ck:react-best-practices` | Đảm bảo performance patterns (memo, lazy load, Suspense) |
| 6. Clean up | `/simplify` | Tối ưu code quality, loại bỏ redundancy |
| 7. Review | `/ck:code-review --pending` | Adversarial review kết quả cuối cùng |

### Workflow chi tiết

**Step 1 — Hiểu design system hiện tại:**
```
/ck:scout design-system --fast
```
→ Scan nhanh codebase để hiểu tokens (colors, spacing, typography), component library đang dùng (shadcn, MUI, custom...), naming conventions.

Prompt mẫu:
```
Hãy scan codebase và tổng hợp design system hiện tại: 
- Component library đang dùng (shadcn, MUI, Ant Design, custom?)
- Color tokens, spacing scale, typography scale
- Naming conventions cho CSS classes/components
- Layout patterns (grid system, breakpoints)
- Có dark mode không? Dùng CSS variables hay Tailwind?
```

**Step 2 — Phân tích component gốc:**
```
/ck:ai-multimodal --vision
```
→ Cung cấp screenshot component gốc. AI sẽ extract: layout structure, color palette, spacing, typography, interactive states.

Prompt mẫu:
```
Phân tích screenshot component này và extract:
- Layout structure (flex/grid, columns, spacing)
- Color palette sử dụng (primary, secondary, background, text)
- Typography (font sizes, weights, line heights)
- Interactive states (hover, active, disabled, focus)
- Responsive behavior nếu nhìn thấy được
- Các icon/image placeholders
```

**Step 3 — Cung cấp context và redesign:**
```
/ck:ui-styling
```

Chỉ cần cung cấp đường dẫn tới code — AI sẽ tự đọc, phân tích logic, và redesign luôn trong một bước.

Prompt mẫu (copy và điền path):
```
Tôi có component [TÊN COMPONENT] từ [NGUỒN].
Code nằm ở: [RELATIVE_PATH] (VD: src/components/checkout/ hoặc src/components/user-form.tsx)

Hãy đọc toàn bộ code trong path trên, tự phân tích logic và structure, rồi redesign UI.

Yêu cầu:
1. Giữ nguyên 100% business logic (hooks, state, handlers, API calls)
2. Chỉ redesign phần UI/JSX cho match design system hiện tại
3. Thay các component đang dùng bằng component có sẵn trong project (scan project để biết)
4. Dùng lại color tokens, spacing, typography đã setup trong project
5. Đảm bảo dark mode compatible
6. Thêm responsive nếu có thể (không bắt buộc)
7. Giữ accessibility (aria labels, keyboard navigation)
```

Nếu có Figma Devmode, thêm link MCP để AI tham khảo design chính xác:
```
Tôi có component [TÊN COMPONENT] từ [NGUỒN].
Code nằm ở: [RELATIVE_PATH]
Figma design reference: [FIGMA_MCP_LINK]

Hãy đọc code, tham khảo Figma design, rồi redesign UI cho match design system của project.
Thay các component đang dùng bằng component có sẵn trong project.
Dùng lại color tokens đã setup. Giữ nguyên logic.
```

**Step 4 — Generate UI mới (optional, chỉ khi cần tạo từ đầu):**

*Option A — AI generate từ mô tả:*
```
/ck:stitch
```
Prompt mẫu:
```
Generate UI component [TÊN] với specs:
- Layout: [mô tả layout - VD: 2-column grid, left sidebar + main content]
- Style: match design system (shadcn/ui + Tailwind)
- States: [loading, empty, error, success]
- Responsive: mobile stack, desktop side-by-side
- Dark mode: support via CSS variables
```

*Option B — Replicate từ screenshot:*
```
/ck:frontend-design
```
Prompt mẫu:
```
Replicate UI từ screenshot đính kèm, nhưng dùng design system hiện tại:
- Dùng shadcn/ui components thay vì custom elements
- Dùng Tailwind classes thay vì custom CSS
- Match layout và spacing chính xác
- Adapt colors sang color tokens của project
```

**Step 5 — Optimize:**
```
/ck:react-best-practices
```
Prompt mẫu:
```
Review component vừa redesign và optimize:
- Có cần React.memo() không?
- Có expensive computation nào cần useMemo()?
- Event handlers có cần useCallback()?
- Có thể lazy load phần nào không?
- Bundle size impact?
```

**Step 6 — Clean up & Review:**
```
/simplify
/ck:code-review --pending
```
→ Clean up code → adversarial review để catch issues.

### Prompt phụ trợ hữu ích

**So sánh trước/sau redesign:**
```
/ck:chrome-devtools
Screenshot component trước và sau redesign. So sánh:
- Layout có đúng không?
- Colors match design system?
- Spacing consistent?
- Responsive behavior?
- Dark mode hoạt động?
```

**Verify logic không bị break:**
```
/ck:test ui
Verify component sau redesign:
- Tất cả interactive states hoạt động (click, hover, focus, disabled)
- Form submission hoạt động đúng
- API calls vẫn trigger đúng
- Error handling vẫn hiển thị đúng
- Loading states vẫn hoạt động
```

**Khi gặp component phức tạp (nhiều sub-components):**
```
Tôi cần redesign [COMPONENT] gồm các sub-components:
1. [SubComponent1] - [mô tả]
2. [SubComponent2] - [mô tả]
3. [SubComponent3] - [mô tả]

Hãy redesign từng sub-component một, bắt đầu từ leaf components (không có children) 
rồi tiến lên parent components. Giữ nguyên props interface.
```

### Tips

- **Giữ logic tách biệt khỏi UI**: Tách business logic vào custom hooks, chỉ redesign phần render/JSX
- **So sánh visual**: Dùng `/ck:chrome-devtools` để screenshot trước/sau, đảm bảo không mất functionality
- **Test UI**: Dùng `/ck:test ui` để verify interactive states hoạt động đúng sau redesign
- **Chia nhỏ nếu component lớn**: Redesign từng sub-component riêng, test từng phần trước khi ghép lại
- **Giữ props interface**: Không thay đổi props interface để tránh break nơi component được import

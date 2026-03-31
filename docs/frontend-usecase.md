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

**Step 3 — Cung cấp context cho AI trước khi redesign:**

Đây là bước quan trọng nhất — cung cấp đầy đủ context để AI hiểu cả component gốc lẫn design system target.

Prompt mẫu (copy và điền thông tin):
```
Tôi có component [TÊN COMPONENT] từ [NGUỒN] (đã paste code bên dưới).
Component này có logic: [MÔ TẢ NGẮN LOGIC - VD: form validation, data fetching, drag-drop...].

Design system hiện tại của project dùng:
- UI Library: [shadcn/ui | MUI | Ant Design | custom]
- CSS: [Tailwind | CSS Modules | styled-components]
- Color tokens: [liệt kê hoặc reference file, VD: globals.css, theme.ts]
- Component patterns: [VD: Card dùng rounded-lg shadow-sm, Button dùng variant props...]

Yêu cầu:
1. Giữ nguyên 100% business logic (hooks, state, handlers, API calls)
2. Chỉ redesign phần UI/JSX cho match design system hiện tại
3. Thay thế inline styles/custom CSS bằng [Tailwind classes | design tokens]
4. Đảm bảo dark mode compatible
5. Đảm bảo responsive (mobile-first)
6. Giữ accessibility (aria labels, keyboard navigation)

[PASTE CODE COMPONENT Ở ĐÂY]
```

**Step 4 — Thực hiện redesign:**
```
/ck:ui-styling
```
→ Map visual elements sang design tokens hiện tại. Thay custom CSS bằng Tailwind utilities + shadcn/ui components.

Prompt mẫu nếu dùng shadcn/ui:
```
Redesign component này dùng shadcn/ui components:
- Thay <button> bằng <Button variant="..." size="...">
- Thay custom input bằng <Input>, <Select>, <Textarea>
- Thay custom modal bằng <Dialog>
- Thay custom dropdown bằng <DropdownMenu>
- Dùng cn() utility cho conditional classes
- Follow shadcn/ui patterns: composition over configuration
```

**Step 5 — Generate UI mới (nếu cần tạo từ đầu):**

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

**Step 6 — Optimize:**
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

**Step 7 — Clean up & Review:**
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

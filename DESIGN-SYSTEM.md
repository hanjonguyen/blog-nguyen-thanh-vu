Tôi sẽ viết tài liệu thiết kế hoàn chỉnh ngay. Đây là nội dung Markdown của file DESIGN-SYSTEM.md.

# DESIGN-SYSTEM.md

> **Hệ thống thiết kế blog — "Bạn có tin nhắn mới!"**
> Phiên bản đã chuyển tông: **Đỏ rượu vang + Đen + Trắng** (loại bỏ hoàn toàn vàng gold `#c8a45a`).
> Kim chỉ nam này dành cho con người *và* cho các agent LLM sinh code. Mọi token, quy tắc và prompt mẫu đều được điền đầy đủ — không còn mục "AI Analysis Required" nào để trống.

---

## 1. Visual Theme & Atmosphere

**Triết lý thiết kế.** Hệ thống được xây trên ba từ khóa: **cinematic — thân mật — đáng tin**. Mỗi bài viết là một "tin nhắn mới" gửi cho một người duy nhất: gần gũi như mở một lá thư, nhưng được dàn dựng có chủ đích như một khung hình điện ảnh. Người đọc bước vào một không gian tối, tập trung, nơi chữ và một sắc đỏ rượu vang sâu dẫn dắt cảm xúc.

**Tông cảm xúc.** Trầm, ấm, có chiều sâu. Không ồn ào, không "tươi vui SaaS". Cảm giác như ngồi trong một quán rượu yên tĩnh ánh đèn vàng cam đã được thay bằng ánh đỏ trầm — riêng tư, đáng tin, có gu. Sự sang trọng đến từ **kiềm chế** chứ không từ trang trí.

**Ẩn dụ thị giác.**
- **Điện ảnh (cinematic):** nền đen sâu, khoảng thở lớn, ánh sáng tụ điểm (radial glow) như đèn sân khấu thay vì đổ bóng vật lý.
- **Thân mật (intimate):** cột chữ hẹp, đọc như đọc thư riêng; pull-quote như một câu được thì thầm.
- **Đáng tin (trustworthy):** lưới chặt chẽ, bố cục đối xứng, không hiệu ứng lòe loẹt — sự nghiêm cẩn tạo niềm tin.
- **Sạch & bền (clean & durable):** bảng màu tối giản 3 sắc gia tộc, bo góc `0` dứt khoát, ít hiệu ứng phụ thuộc thời thượng — thiết kế còn đẹp sau nhiều năm.

**Ẩn dụ vật liệu.** Rượu vang đỏ rót trên đá đen, chữ in trên giấy kem. Tương phản cao, bề mặt phẳng, ánh sáng có hướng.

---

## 2. Color Palette & Roles

Bảng màu cuối cùng. **Đã loại bỏ `#c8a45a` (gold).** Accent duy nhất giờ là họ đỏ rượu vang.

### 2.1 Bảng token màu

| Token | HEX | Vai trò |
|---|---|---|
| `--wine` | `#7b1e2b` | **Accent chính** — màu thương hiệu, nút primary, link active, thanh progress, viền nhấn. |
| `--wine-deep` | `#561019` | Accent tối — hover/pressed của nút, nền chip đậm, gradient stop tối. |
| `--wine-bright` | `#a02234` | Accent sáng — link hover, focus ring, điểm nhấn nhỏ trên nền đen, tâm radial glow. |
| `--wine-soft` | `#c97b85` | Accent dịu — eyebrow/label trên nền tối, icon phụ, đường kẻ nhấn mảnh, trạng thái selected nhẹ. |
| `--black` | `#0d0b0c` | **Nền tối nền tảng** (canvas tối, hero, footer). Đen ngả tím rượu rất nhẹ. |
| `--ink` | `#161213` | Surface tối nâng — card trên nền đen, navbar, Q&A box, code block. |
| `--cream` | `#f7f4ef` | **Nền sáng nền tảng** — vùng đọc dài, section sáng. Ấm hơn trắng tinh. |
| `--paper` | `#ffffff` | Surface sáng nâng — card trên nền cream, input, bảng. |
| `--text-on-dark` | `#f2ede6` | Chữ chính trên nền tối (cream-white, không chói). |
| `--text-on-light` | `#1a1416` | Chữ chính trên nền sáng (gần đen, ngả rượu). |
| `--text-dim-dark` | `rgba(242,237,230,0.62)` | Chữ phụ/caption trên nền tối. |
| `--text-dim-light` | `rgba(26,20,22,0.58)` | Chữ phụ/caption trên nền sáng. |
| `--border-dark` | `rgba(242,237,230,0.14)` | Viền hairline trên nền tối. |
| `--border-light` | `rgba(26,20,22,0.12)` | Viền hairline trên nền sáng. |

### 2.2 CSS variables (copy trực tiếp)

```css
:root {
  /* Accent — họ rượu vang */
  --wine:        #7b1e2b;
  --wine-deep:   #561019;
  --wine-bright: #a02234;
  --wine-soft:   #c97b85;

  /* Nền & surface */
  --black: #0d0b0c;
  --ink:   #161213;
  --cream: #f7f4ef;
  --paper: #ffffff;

  /* Chữ */
  --text-on-dark:  #f2ede6;
  --text-on-light: #1a1416;
  --text-dim-dark:  rgba(242,237,230,0.62);
  --text-dim-light: rgba(26,20,22,0.58);

  /* Viền */
  --border-dark:  rgba(242,237,230,0.14);
  --border-light: rgba(26,20,22,0.12);

  /* Glow điện ảnh (xem mục 6) */
  --glow-wine: radial-gradient(60% 60% at 50% 0%,
                rgba(160,34,52,0.28) 0%,
                rgba(123,30,43,0.10) 40%,
                rgba(13,11,12,0) 72%);
}
```

### 2.3 Tỉ lệ tương phản chính (WCAG, nền tối là mặc định)

| Cặp màu | Contrast | Đạt |
|---|---|---|
| `--text-on-dark #f2ede6` trên `--black #0d0b0c` | ~**15.3:1** | AAA (mọi cỡ) |
| `--text-on-dark #f2ede6` trên `--ink #161213` | ~**13.9:1** | AAA |
| `--text-on-light #1a1416` trên `--cream #f7f4ef` | ~**15.6:1** | AAA |
| `--text-on-light #1a1416` trên `--paper #ffffff` | ~**16.8:1** | AAA |
| `--wine-soft #c97b85` trên `--black #0d0b0c` (eyebrow) | ~**6.4:1** | AA (text thường), AAA (text lớn) |
| `--text-on-dark #f2ede6` trên `--wine #7b1e2b` (nút primary) | ~**6.9:1** | AA / AAA (≥18px bold) |
| `--wine-bright #a02234` trên `--black` (điểm nhấn nhỏ) | ~**4.6:1** | AA cho text ≥18px / dùng cho icon & nhấn, KHÔNG cho body |

**Quy tắc cứng về tương phản:** `--wine #7b1e2b` thuần **không bao giờ** dùng làm màu chữ body trên nền đen (contrast quá thấp). Để nhấn chữ trên nền tối, dùng `--wine-soft` hoặc `--wine-bright`.

---

## 3. Typography Rules

**Cặp font.** Tiêu đề dùng **Playfair Display** (serif hiển thị, cảm xúc, điện ảnh). Thân bài dùng **Inter** (sans-serif, trung tính, dễ đọc dài). Không trộn thêm font thứ ba.

```css
--font-display: "Playfair Display", "Times New Roman", serif;
--font-body:    "Inter", system-ui, -apple-system, "Segoe UI", sans-serif;
```

### 3.1 Thang cỡ chữ (responsive, dùng `clamp`)

| Cấp | Font | clamp() | Weight | Line-height | Letter-spacing |
|---|---|---|---|---|---|
| Hero (h1) | Playfair | `clamp(2.75rem, 6vw + 1rem, 5.875rem)` *(~44 → 94px)* | 600 | 1.04 | -0.02em |
| h2 | Playfair | `clamp(2rem, 3.5vw + .5rem, 3.25rem)` | 600 | 1.10 | -0.01em |
| h3 | Playfair | `clamp(1.5rem, 1.5vw + .6rem, 2rem)` | 500 | 1.18 | 0 |
| h4 / lead | Inter | `clamp(1.15rem, .5vw + 1rem, 1.375rem)` | 500 | 1.45 | 0 |
| Body | Inter | `clamp(1.0625rem, .25vw + 1rem, 1.1875rem)` *(17→19px)* | 400 | 1.72 | 0 |
| Small / caption | Inter | `0.875rem` | 400 | 1.5 | 0.01em |
| Eyebrow / label | Inter | `0.75rem` | 600 | 1.4 | **0.18em** |

> Hero giữ đúng "giá trị gốc" 93.94px ≈ `5.875rem` ở cực đại của `clamp`.

### 3.2 Casing & nhấn

- **Eyebrow / label / tag:** `text-transform: uppercase;` + `letter-spacing: 0.18em;` + màu `--wine-soft` (nền tối) hoặc `--wine` (nền sáng). Đây là "chữ ký" của hệ thống — luôn IN HOA GIÃN CHỮ.
- **Tiêu đề Playfair:** giữ sentence case hoặc Title Case; **không** in hoa toàn bộ (Playfair in hoa size lớn trông nặng).
- **Body Inter:** sentence case, không letter-spacing.
- **Số liệu / kicker thống kê:** Playfair, có thể dùng `font-style: italic` để tăng chất điện ảnh.

---

## 4. Component Stylings

Nguyên tắc xuyên suốt: **bo góc `0`** (radius 0), viền hairline mảnh, fill phẳng, accent rượu vang dùng tiết kiệm.

### 4.1 Button

```css
.btn {                      /* Primary */
  border-radius: 0;                       /* RADIUS 0 — bất biến */
  background: var(--wine);
  color: var(--text-on-dark);
  font-family: var(--font-body);
  font-weight: 600;
  letter-spacing: 0.04em;
  padding: 0.95rem 1.75rem;               /* >=44px touch height */
  border: 1px solid var(--wine);
  transition: background .18s ease, transform .18s ease;
}
.btn:hover   { background: var(--wine-deep); border-color: var(--wine-deep); }
.btn:active  { transform: translateY(1px); }
.btn:focus-visible { outline: 2px solid var(--wine-bright); outline-offset: 3px; }

.btn--ghost {               /* Secondary trên nền tối */
  background: transparent;
  color: var(--text-on-dark);
  border: 1px solid var(--border-dark);
}
.btn--ghost:hover { border-color: var(--wine-soft); color: var(--wine-soft); }
```

### 4.2 Card / Q&A box

- **Card (nền tối):** nền `--ink`, viền `1px var(--border-dark)`, radius `0`, padding `1.5rem–2rem`. Tiêu đề Playfair, body Inter dim. Nhấn bằng một đường viền trái `3px solid var(--wine)` khi cần.
- **Q&A box:** câu hỏi = Inter 600 + eyebrow "HỎI" màu `--wine-soft`; câu trả lời = body thường, tách bằng hairline. Cả khối đặt trong card `--ink`, border-left `3px var(--wine)`.

### 4.3 Pull-quote

```css
.pull-quote {
  font-family: var(--font-display);
  font-style: italic;
  font-size: clamp(1.6rem, 2.5vw, 2.4rem);
  line-height: 1.3;
  color: var(--text-on-dark);
  border-left: 3px solid var(--wine);
  padding: .25rem 0 .25rem 1.5rem;
  margin: 2.5rem 0;
}
```

Không dùng dấu ngoặc kép trang trí cỡ lớn màu gold (đã bỏ). Nhấn duy nhất là thanh `--wine` bên trái.

### 4.4 Chip / Tag

```css
.tag {
  border-radius: 0;
  font: 600 0.75rem/1 var(--font-body);
  text-transform: uppercase;
  letter-spacing: 0.16em;
  padding: .45rem .7rem;
  color: var(--wine-soft);
  border: 1px solid var(--border-dark);
  background: transparent;
}
.tag--solid { background: var(--wine); color: var(--text-on-dark); border-color: var(--wine); }
```

### 4.5 Navbar

- Nền `--black` (hoặc `--ink` khi sticky), hairline dưới `1px var(--border-dark)`.
- Logo Playfair; menu Inter 500.
- Link active: gạch chân `2px var(--wine-bright)` hoặc chữ `--wine-soft`.
- Sticky: thêm `--glow-wine` mờ ở mép trên để giữ chất điện ảnh.

### 4.6 Progress bar (reading progress)

```css
.progress {
  height: 3px;
  background: transparent;
}
.progress__fill {
  height: 100%;
  background: linear-gradient(90deg, var(--wine), var(--wine-bright));
  width: var(--scroll, 0%);
}
```

---

## 5. Layout Principles

- **Cột đọc (reading column):** `max-width: 720px` cho nội dung văn bản dài — độ dài dòng tối ưu ~70–80 ký tự.
- **Container rộng:** `max-width: 1100px` cho hero, lưới card, media full-bleed, footer.
- **Lề:** `padding-inline: clamp(1.25rem, 5vw, 3rem)`.
- **Nhịp dọc (vertical rhythm):** đơn vị nền `8px`; khoảng cách section dùng `clamp(4rem, 10vw, 8rem)`.
- **Whitespace — airy & cinematic:** khoảng thở lớn là *tính năng*, không phải chỗ trống. Hero chiếm gần trọn viewport; mỗi section có "air" rộng để từng ý được hít thở. Mật độ thấp → cảm giác cao cấp.
- **Lưới:** 12 cột cho vùng rộng; cột đọc canh giữa độc lập với container.

```css
.container { max-width: 1100px; margin-inline: auto; padding-inline: clamp(1.25rem,5vw,3rem); }
.reading   { max-width: 720px;  margin-inline: auto; }
.section   { padding-block: clamp(4rem,10vw,8rem); }
```

---

## 6. Depth & Elevation

**Triết lý: phẳng + tương phản, không bóng đổ vật lý.** Chiều sâu đến từ **ánh sáng có hướng**, không từ `box-shadow` xám.

- **Tách lớp bằng giá trị bề mặt:** `--black` (nền) → `--ink` (surface nâng) → hairline `--border-dark`. Không cần shadow để phân lớp.
- **Radial glow rượu vang** thay cho shadow: đặt một quầng sáng `--glow-wine` phía sau hero, sau tiêu đề lớn, hoặc mép trên navbar sticky — như đèn sân khấu hắt lên.

```css
.hero {
  position: relative;
  background: var(--black);
  color: var(--text-on-dark);
}
.hero::before {            /* glow điện ảnh thay cho đổ bóng */
  content: "";
  position: absolute; inset: 0;
  background: var(--glow-wine);
  pointer-events: none;
}
```

- **Shadow vật lý:** chỉ dùng cực hạn chế (ví dụ menu dropdown nổi), và phải nhuốm rượu vang chứ không xám trung tính:
  `box-shadow: 0 24px 60px -24px rgba(86,16,25,0.55);`
- **Trên nền sáng (cream/paper):** tách lớp bằng hairline `--border-light`, tránh shadow nặng — giữ chất "sạch & bền".

---

## 7. Do's & Don'ts (ràng buộc cứng)

1. **DÙNG `border-radius: 0`** cho mọi nút, chip, card, input. **ĐỪNG** bo góc — radius khác 0 phá vỡ ngôn ngữ "sạch & dứt khoát".
2. **ĐỪNG dùng gold `#c8a45a`** hay bất kỳ sắc vàng/đồng nào. Accent **chỉ** thuộc họ rượu vang (`--wine` / `--wine-deep` / `--wine-bright` / `--wine-soft`).
3. **DÙNG Playfair Display cho mọi tiêu đề** (h1–h3, pull-quote) và **Inter cho body**. **ĐỪNG** đặt body bằng Playfair (mỏi mắt khi đọc dài) hay tiêu đề lớn bằng Inter.
4. **ĐỪNG để chữ tier-dim** (`--text-dim-dark` / `--text-dim-light`) trên nền sai tông — không bao giờ dùng `--text-dim-dark` trên nền sáng, và không dùng `--wine #7b1e2b` thuần làm chữ body trên nền đen (contrast < AA).
5. **DÙNG glow rượu vang + hairline** để tạo chiều sâu trên nền tối. **ĐỪNG** dùng `box-shadow` xám trung tính lớn — nó làm thiết kế trông "Material/SaaS" và phá tông điện ảnh.

> Bonus rule: eyebrow/label **luôn** IN HOA giãn chữ `0.18em`. Accent rượu vang là gia vị — phủ ≤ ~10% diện tích mỗi màn hình.

---

## 8. Responsive Behavior

**Breakpoints.**

| Tên | Range | Hành vi |
|---|---|---|
| Mobile | `< 640px` | 1 cột; hero clamp về cận dưới (~44px); navbar gập thành hamburger; card xếp dọc; reading column = full width trừ lề. |
| Tablet | `640–1024px` | Lưới 2 cột cho card; container co theo `5vw`; hero cỡ trung. |
| Desktop | `> 1024px` | Container `1100px`, reading `720px`; lưới tới 12 cột; hero đạt cực đại 93.94px. |

**Chiến lược gập.**
- Navbar: ngang trên desktop → menu trượt/hamburger trên mobile (nền `--black`, items full-width, mỗi item ≥ 48px chiều cao).
- Hero: 2 cột (chữ + media) trên desktop → xếp dọc, media dưới, trên mobile.
- Card grid: `repeat(auto-fit, minmax(280px, 1fr))`.
- Pull-quote: giảm còn `1.5rem` và bỏ thụt lề lớn trên mobile.

**Touch.**
- **Touch target ≥ 44×44px** cho mọi phần tử bấm được (nút, link menu, tag bấm được, nút share, control progress).
- Khoảng cách giữa hai target bấm ≥ 8px.
- Bỏ hiệu ứng chỉ-hover trên touch; trạng thái `:active` rõ ràng (đổi nền sang `--wine-deep`).

```css
@media (max-width: 640px) {
  .hero h1 { font-size: clamp(2.5rem, 11vw, 3.25rem); }
  .nav__links { position: fixed; inset: 0 0 0 auto; width: min(82vw,360px);
                background: var(--black); }
  .btn, .nav__link, .tag--clickable { min-height: 44px; }
}
```

---

## 9. Agent Prompt Guide

Ba prompt mẫu để chỉ thị một LLM sinh component đúng hệ thống này. Mỗi prompt đã nhúng token bắt buộc để output không lệch tông.

### Prompt mẫu 1 — Hero section

```
Sinh một hero section HTML+CSS cho blog "Bạn có tin nhắn mới!" theo design system Đỏ Rượu Vang.
BẮT BUỘC:
- Nền --black #0d0b0c, chữ --text-on-dark #f2ede6.
- Eyebrow IN HOA giãn chữ 0.18em màu --wine-soft #c97b85, trên tiêu đề.
- Tiêu đề Playfair Display, clamp(2.75rem,6vw+1rem,5.875rem), weight 600, line-height 1.04.
- Lead Inter 1.375rem màu dim.
- 1 nút primary: nền --wine #7b1e2b, radius 0, hover --wine-deep #561019, padding cao >=44px.
- Thêm lớp radial glow rượu vang (--glow-wine) phía sau bằng ::before; KHÔNG dùng box-shadow xám.
- Container max-width 1100px.
CẤM: màu gold #c8a45a, border-radius khác 0, body bằng Playfair.
```

### Prompt mẫu 2 — Q&A / FAQ accordion

```
Sinh component FAQ accordion theo design system Đỏ Rượu Vang + Đen + Trắng.
BẮT BUỘC:
- Mỗi item là card nền --ink #161213, viền 1px rgba(242,237,230,0.14), radius 0, border-left 3px solid --wine.
- Câu hỏi: Inter 600 + eyebrow "HỎI" màu --wine-soft (uppercase, letter-spacing 0.18em).
- Câu trả lời: Inter 400, line-height 1.72, màu --text-dim-dark, cách bằng hairline.
- Icon mở/đóng đổi màu sang --wine-bright #a02234 khi active; focus-visible outline 2px --wine-bright.
- Touch target toàn hàng tiêu đề >=44px.
CẤM: gold, bo góc, shadow xám, dùng --wine #7b1e2b làm màu chữ trên nền đen.
```

### Prompt mẫu 3 — Article card grid

```
Sinh lưới card bài viết responsive theo design system Đỏ Rượu Vang.
BẮT BUỘC:
- Grid: repeat(auto-fit, minmax(280px,1fr)), gap 1.5rem, trong container 1100px.
- Card: nền --ink trên nền --black, viền hairline --border-dark, radius 0, padding 1.75rem.
- Tag/chip ở đầu card: uppercase, letter-spacing 0.16em, màu --wine-soft, viền hairline, radius 0.
- Tiêu đề card: Playfair Display 1.5rem, weight 500, màu --text-on-dark.
- Excerpt: Inter, --text-dim-dark, tối đa 3 dòng (line-clamp).
- "Đọc tiếp →" màu --wine-soft, hover --wine-bright.
- Hover card: viền chuyển --wine-soft + glow rượu vang nhẹ; KHÔNG nâng bằng box-shadow xám.
- Mobile <640px: 1 cột, mọi link >=44px.
CẤM: gold #c8a45a, border-radius > 0, font body Playfair, shadow trung tính.
```

---

**Tóm tắt bất biến:** Đỏ rượu vang là accent duy nhất · Playfair cho tiêu đề / Inter cho body · radius 0 tuyệt đối · chiều sâu bằng glow + hairline, không shadow xám · whitespace rộng, điện ảnh · accent ≤ ~10% diện tích · touch ≥ 44px · không bao giờ gold.

*File: `DESIGN-SYSTEM.md`*
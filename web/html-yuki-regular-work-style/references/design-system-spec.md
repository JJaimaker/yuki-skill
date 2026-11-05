# html-yuki-regular-work-style — Full Specification

## 1. Base Visual Tone

- **Style name**: html-yuki-regular-work-style (Modern Minimalism base)
- **Core identity**: Single hue + warm base + weight contrast + extreme breathing room, research report print quality
- **Never use**: Gradients, shadows, glassmorphism, neon glow, heavy decorations
- **Separation method**: Borders + whitespace only, not visual effects
- **Vibe**: Printed research report, not a dashboard, not a landing page

## 2. Color & Functional Constraints

### Theme: 研报红 (default, for TCO reports)

| Role | Value | Usage |
|---|---|---|
| Page base | `#FAF7F2` warm white | Global background, warm yellow/cream tone |
| Card base | `#FFF` pure white | Content containers, float above warm base |
| Primary accent | `#B91C1C` deep red | Title numbers, table headers, borders, tags, signature |
| Dark accent | `#7F1D1D` | Bold text (strong), keywords |
| Shade ramp | `#DC2626` -> `#EF4444` -> `#F87171` | P0 -> P3 priority tags, dark to light |
| Border/divider | `#E8D9D2` warm beige | Card outlines, table outer border |
| Row divider | `#F1E5E0` ultra-light warm | Table row lines, card inner separators |
| Highlight base | `#FEF2F2` ultra-light pink | Blockquotes, hover highlight |
| Zebra row | `#FCF8F5` | Table even rows |
| Body text | `#1B1B1B` near-black | Main text, warmer than pure black |
| Secondary text | `#2B1B1B` warm dark | Paragraph text |
| Auxiliary text | `#6B4F4F` warm brown-gray | Tag descriptions, dates, footer |

### Theme: Gemini 紫 (for dark mode diagrams)

| Role | Value |
|---|---|
| Page base | `#131314` pure black |
| Primary accent | `#A142F4` / `#BB86FC` bright purple |
| Title color | `#CECBF6` |
| Body text | `#AFA9EC` |
| Card fills (ramp 800) | Purple `#3C3489` / Blue `#0C447C` / Pink `#4B1528` / Teal `#04342C` / Orange `#412402` |
| Card strokes (ramp 200) | `#AFA9EC` / `#85B7EB` / `#ED93B1` / `#5DCAA5` / `#FAC775` |
| Table header | `#A142F4` solid + `#131314` black text |

### Principles
- **Single hue**: Only one color hue per theme; use shade depth for hierarchy, not different hues
- **Warm base**: Base is never cold gray or pure white; it carries a warm tone matching the accent
- **90/10 rule**: 90% neutral colors (base + white cards + near-black text), 10% accent (titles, headers, tags, signature)

## 3. Font Weight Contrast

- **Only two weights**: 400 (body) + 500 (titles/emphasis)
- **h1/h2 may use 600** for stronger hierarchy, but never 700
- Contrast comes from font-size + color + spacing, not from bold
- `strong` tag: `font-weight: 500` + dark accent color (`#7F1D1D` for red theme), never default bold + black

## 4. Type Scale

| Element | Size | Weight |
|---|---|---|
| h1 | 36px | 500 |
| h2 | 24px | 500 |
| h3 | 17px | 500 |
| h4 | 15px | 500 |
| Body p | 15px | 400 |
| Table td | 13.5px | 400 |
| Table th | 13px | 500 |
| Tag | 12px | 500 |
| Auxiliary | 12px | 400 |
| Eyebrow (label) | 13px | 500 + uppercase + letter-spacing 0.18em |

## 5. Layout & Spacing

- Max width: 960px, centered
- Padding: 64px top / 48px sides / 96px bottom, generous whitespace
- Line-height: body 1.7, titles 1.3
- Paragraph spacing: 14px
- List item spacing: 8px
- Section spacing: 64px (h2 margin-top)
- Responsive: below 720px, collapse to single column, reduce font sizes

### Text wrapping & orphans

- **No single-character orphan lines**: Short labels, headings, list items, menu items, and table cells must not break so that only one character sits alone on the last line.
  - Bad: `AI 新手教 / 练`, `AI 工况推 / 荐`, `AI 拆装方 / 案`
  - Good: keep the whole phrase on one line, or break at a sensible point with at least 2 characters on each line.
- **Implementation**: For phrases ≤ 8 Chinese characters where orphan risk exists, wrap in `<span class="no-break">` or apply `white-space: nowrap`.
- **CSS utility**:
  ```css
  .no-break { white-space: nowrap; }
  ```
- **Default paragraph text** may wrap normally; this rule targets short labels/headings/items where an orphan is visually awkward.

### Adaptive CJK text wrapping (anti-orphan, all viewport widths)

CJK text can break at any character, making single-character orphans common. This is a resolution/viewport-dependent problem — the same text can look fine at one width and broken at another. Applied globally to all paragraphs, list items, table cells, and blockquotes.

- **Level 1 — Modern CSS (primary)**:
  ```css
  p, li, td, th, blockquote { text-wrap: pretty; }
  h1, h2, h3, h4 { text-wrap: balance; }
  ```
  `text-wrap: pretty` prevents orphans on the last line. `text-wrap: balance` evenly distributes text across heading lines. Supported in Chrome/Edge 117+, Safari 17+. Graceful fallback for unsupported browsers.

- **Level 2 — CJK character boundaries**:
  ```css
  html[lang="zh-CN"] p, html[lang="zh-CN"] li, html[lang="zh-CN"] td {
    word-break: normal;
    overflow-wrap: break-word;
    hyphens: none;
  }
  ```

- **Level 3 — JS fallback** (for browsers without `text-wrap: pretty`, e.g. Firefox): A script detects `CSS.supports('text-wrap', 'pretty')` and conditionally activates a CJK-aware orphan fixer that glues the last few characters together. The script is self-contained and included in the template.

- **Template placement**: All three levels are included in the Skill template by default. When generating HTML from this Skill, always include all three.

### Responsive breakpoints

Apply three breakpoints for consistent rendering across devices:

| Breakpoint | Target | Behavior |
|---|---|---|
| ≤ 960px | Narrow desktop / tablet landscape | TOC narrows to 200px |
| ≤ 720px | Tablet portrait | TOC stacks above content; fonts scale down |
| ≤ 480px | Mobile | Tight padding; single-column; smallest font sizes |

## 6. Component Patterns

### Cards
- White base + `#E8D9D2` border (red theme) / `#3C3489` border (purple theme)
- Accent cards: `border-left: 3px solid <accent>` + `#FEF2F2` base
- Radius: 4–8px, no shadow

### Tables
- Header: solid accent color + white text
- Even rows: `#FCF8F5` (red theme)
- Hover: `#FEF2F2`
- Outer border: `#E8D9D2`
- **Header cells: `white-space: nowrap`, never wrap**
- **Column widths: proportional to content**
- **Cell text: max 10 characters; if longer, shorten or abbreviate**

### Tags (pill shape)
- P0: `#B91C1C` (darkest)
- P1: `#DC2626`
- P2: `#EF4444`
- P3: `#F87171` (lightest)
- White text, `border-radius: 4px`, `padding: 2px 8px`

### Blockquotes
- `#FEF2F2` base + `border-left: 3px solid #B91C1C`
- Text color: `#2B1B1B`

### Formula blocks
- White base + border + centered + monospace font

### SVG charts
- White card container + caption text below (12px `#6B4F4F`)

### Roadmap cards
- White base + `border-top: 3px solid #B91C1C`

### Dividers
- Section: `1px solid #E8D9D2`
- Inline: `1px solid #F1E5E0`

## 7. Table Rules

- Header cells: `white-space: nowrap` (never wrap)
- Column widths: proportional to content
- Cell text: default max 10 characters; if longer, split or abbreviate
- Wide columns may wrap; narrow columns forced single-line

## 8. TOC & Structure

- **Core conclusions first**: Place key findings immediately after the header, before any section
- **Section numbering**: Use Arabic numerals (1, 2, 3...), never Chinese numerals
- **Left sidebar TOC**: Fixed position, contains all h2 + h3 entries
- **Scroll-spy**: Current section highlighted in TOC as user scrolls
- **Clickable anchors**: Each TOC item links to the corresponding section
- **All sub-headings included**: If a section has sub-headings, they appear as nested items in the TOC

### TOC implementation
```html
<nav class="toc">
  <a href="#sec-1" class="toc-item toc-h2">1. Section Title</a>
  <a href="#sec-1-1" class="toc-item toc-h3">1.1 Sub Title</a>
  <a href="#sec-2" class="toc-item toc-h2">2. Section Title</a>
</nav>
```

### Scroll-spy JavaScript
```javascript
const sections = document.querySelectorAll('section[id]');
const tocItems = document.querySelectorAll('.toc-item');
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      tocItems.forEach(item => item.classList.remove('active'));
      const activeItem = document.querySelector(`.toc-item[href="#${entry.target.id}"]`);
      if (activeItem) activeItem.classList.add('active');
    }
  });
}, { rootMargin: '-20% 0px -70% 0px' });
sections.forEach(s => observer.observe(s));
```

## 9. Footer Signature

Every HTML page MUST end with the Yuki 观测站 signature block.

### Template
```html
<div class="footer">
  <p>用途：内部战略研究与评审</p>
  <div class="signature">
    <span class="sig-icon"></span>Yuki 观测站
  </div>
</div>
```

### CSS
```css
.footer {
  margin-top: 80px;
  padding-top: 24px;
  border-top: 1px solid #E8D9D2;
  font-size: 12px;
  color: #6B4F4F;
  text-align: center;
}
.footer .signature {
  margin-top: 16px;
  padding-top: 16px;
  border-top: 1px solid #E8D9D2;
  font-size: 13px;
  font-weight: 500;
  color: #B91C1C; /* accent color, adapt per theme */
  letter-spacing: 2px;
}
.footer .signature .sig-icon {
  display: inline-block;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #B91C1C; /* accent color */
  margin: 0 8px 1px 0;
  vertical-align: middle;
}
```

### Theme adaptation
- 研报红: `#B91C1C`
- Gemini 紫: `#BB86FC`
- Custom: use the theme's accent color

## 10. Golden Prompt Self-Check

Before delivering any HTML, mentally run through these 4 categories. Do not write them into the prompt; just verify each item.

### A. Base Aesthetics
- [ ] Modern Minimalism: warm white / pure black base (by theme), single hue
- [ ] No gradients, no shadows, no glassmorphism
- [ ] Research report print quality, not dashboard or landing page

### B. Color & Tone
- [ ] 90/10 rule: 90% neutral, 10% accent
- [ ] Single hue: depth for hierarchy, not multiple hues
- [ ] No pure black `#000` for body text; use `#1B1B1B` (light) or `#AFA9EC` (dark)
- [ ] Secondary text uses warm neutral, not cold gray `#888`
- [ ] Color serves content: accent appears only where attention is needed

### C. Typography & Spacing
- [ ] Weight contrast not bold: titles 500–600, body 400, never 700
- [ ] Contrast from size + color + spacing, not from font-weight
- [ ] Line-height 1.7 (body) / 1.3 (titles), slightly larger than intuition
- [ ] Section gap 64px, paragraph gap 14px, 1.5x wider than normal
- [ ] Max width 960px, centered
- [ ] Font stack: `-apple-system, 'Inter', 'Noto Sans SC', sans-serif`

### D. Component
- [ ] Radius unified 4–8px, no large radius (12px+), no rounded-full
- [ ] No box-shadow; layers from border + background color difference
- [ ] Cards = white base + warm border; accent cards = left bar + light tint
- [ ] Table headers: solid accent + white text, no striped backgrounds
- [ ] Pill tags: accent shade ramp from dark (P0) to light (P3)
- [ ] Dividers: warm light color, not cold gray `#ccc`

### Anti-Patterns (must NOT appear)
- Large radius cards + shadows + gradient backgrounds (airline template)
- Multiple hues mixed (red + blue + green + orange)
- All-bold emphasis (PPT style, not report)
- Pure black text on pure white (cold, no warmth)
- Information filling every pixel (dashboard, not report)

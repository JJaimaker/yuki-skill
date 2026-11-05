---
name: html-yuki-regular-work-style
description: "html-yuki-regular-work-style设计系统 — Modern Minimalism 基底，单色相 + 暖底色 + 字重对比 + 极致留白，研报印刷品质感。This skill should be used when generating static HTML pages, research reports, interactive web pages, or any HTML deliverable that needs a refined, professional visual style. Triggers on requests like '生成网页', '生成 HTML', '做个页面', '用 Sany WorkStyle 风格', '用研报红风格', '部署到 Netlify'. Also triggers when the user asks to create any HTML page without specifying a different design system."
---

# html-yuki-regular-work-style

## Overview

html-yuki-regular-work-style is a self-contained design system for generating refined, report-grade static web pages. Core philosophy: Modern Minimalism — single hue, warm base, weight contrast (not bold), extreme breathing room, no shadows or gradients.

## When to Use

- Generating any static HTML page, research report, interactive widget, or web deliverable
- User says "生成网页", "生成 HTML", "做个页面", "用 Sany Work Style 风格", "用研报红风格"
- User asks to deploy HTML to Netlify or any static host
- User asks for a "report", "研究报告", "分析页面" in HTML format
- No other design system is explicitly requested

## Design Principles (4 Core Laws)

1. **90/10 Color Rule**: 90% neutral (base + white cards + near-black text), 10% accent (titles, headers, tags, signature)
2. **Weight Contrast, Not Bold**: Titles 500–600, body 400. Contrast comes from size + color + spacing, never from font-weight 700
3. **Extreme Breathing Room**: Line-height 1.7, section gap 64px, paragraph gap 14px — 1.5x wider than intuition
4. **No Shadows, No Gradients**: Layers come from border + background color difference, not box-shadow. Radius unified at 4–8px

## Color Themes

Sany WorkStyle HTML supports theme switching by changing only the accent hue:

| Theme name | Accent | Base | Trigger phrase |
|---|---|---|---|
| 研报红 (default) | `#B91C1C` red | `#FAF7F2` warm white | "研报红" / default |
| Gemini 紫 | `#BB86FC` purple | `#131314` pure black | "Gemini dark mode" / "紫" |
| 自定义 | any hex | any hex | user specifies hex values |

For each theme, derive a 5-step shade ramp from dark to light for the accent color.

## Workflow

### Step 1: Load Full Specification

Read `references/design-system-spec.md` before generating HTML. This file contains the complete 10-section specification: color tokens, typography scale, spacing rules, component patterns, table rules, TOC structure, and footer signature.

### Step 2: Choose Theme

Determine the accent color and base color based on:
- User's explicit request (e.g., "用研报红风格")
- Project context (e.g., TCO report = red, Gemini dark = purple)
- Default: 研报红 (warm white base + red accent)

### Step 3: Use Template

Copy `assets/Sany-WorkStyle-Template.html` as the starting point. This template includes:
- Pre-built CSS with CSS custom properties for theme switching
- Left sidebar TOC with scroll-spy
- Footer signature block
- Responsive breakpoints

Customize the content area; keep the CSS framework intact unless the user requests changes.

### Step 4: Self-Check (4 Categories)

Before delivering, run through the 5-category checklist from `references/design-system-spec.md` Section 10:
- A. Base Aesthetics (minimalism, no gradients/shadows)
- B. Color & Tone (90/10 rule, single hue, no pure black)
- C. Typography & Spacing (weight contrast, 1.7 line-height, 64px gaps, **CJK anti-orphan: text-wrap:pretty + JS fallback + no-break spans on short labels**)
- D. Component (4–8px radius, no shadows, pill tags)
- E. Responsive (3 breakpoints: 960px / 720px / 480px; test at common viewport widths)

### Step 5: Footer Signature

Every HTML page MUST end with the Yuki 观测站 signature block. See `references/design-system-spec.md` Section 9 for the exact template.

### Step 6: Deploy (if requested)

If the user says "部署到 Netlify" or "部署上线":
1. Put all files in a `dist/` directory
2. Entry file must be named `index.html`
3. All filenames in English, no Chinese
4. HTML must be self-contained (inline CSS/JS)
5. Include a `_redirects` file for fallback
6. Deliver the ready-to-deploy directory

Alternatively, use the built-in CloudStudio deployment to publish directly.

## Anti-Patterns (Do NOT Do These)

- Large rounded corners (12px+) with shadows — looks like an airline landing page, not a research report
- Multiple hues mixed together (red + blue + green + orange)
- All-bold emphasis (looks like a PPT, not a report)
- Pure black text on pure white background (cold, no warmth)
- Information filling every pixel with no whitespace (looks like a dashboard, not a report)

## Resources

### references/
- `design-system-spec.md` — Complete 10-section specification with color tokens, typography, spacing, components, tables, TOC, and self-check checklist. Load this before generating HTML.

### assets/
- `Sany-WorkStyle-Template.html` — Ready-to-use HTML boilerplate with pre-built CSS framework, left sidebar TOC, and footer signature. Copy this as the starting point for every HTML page.

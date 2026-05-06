# Design System Reference

> Load this file when designing SVG slides. It covers typography, color, layout, visual elements, consistency, and brand identity.

---

## Typography Rules

Text hierarchy must clearly separate:

1. **Headlines** — Large, bold, high impact, visually dominant
2. **Subheadings** — Structured, supportive, slightly smaller
3. **Body Text** — Highly readable, clean, easy to scan
4. **Highlight Words** — Selectively emphasized for retention

**Rules:**
- Never overcrowd text
- Never make text too small
- Maintain consistency across all slides
- Optimize for mobile readability
- Use system-safe font families (e.g., `font-family="sans-serif"` or embed a Google Font via `<style>@import url(...)</style>`)

### Recommended Size Scale (1080px canvas)

| Element | Weight | Size Range |
|---------|--------|------------|
| Headline | 700–900 | 64–96px |
| Subheading | 600–700 | 40–56px |
| Body | 400–500 | 28–36px |
| Highlight / Label | 600–700 | 24–32px |
| Caption / Fine Print | 400 | 20–24px |

> For LinkedIn (1080×1080), scale sizes down by ~10–15% to preserve readability at square format.

---

## Color Rules

Use color strategically for hierarchy, contrast, emphasis, branding, readability, and emotional tone.

**If user provides brand colors:**
- Use them consistently across all slides
- Apply to headings, accents, highlights, CTAs, backgrounds

**If no brand colors — use a premium palette matching the topic:**

| Topic | Background | Primary | Accent |
|-------|-----------|---------|--------|
| Tech / AI | `#0D1B2A` | `#3A86FF` | `#FFFFFF` |
| Business / Productivity | `#1A1A2E` | `#F5A623` | `#F0F0F0` |
| Creator / Personal Brand | `#2D1B69` | `#FF6B6B` | `#FAFAFA` |
| Health / Wellness | `#1B4332` | `#52B788` | `#FFFDF7` |
| Finance / Professional | `#002147` | `#708090` | `#FFFFFF` |
| Education / Learning | `#1C2951` | `#6C63FF` | `#F8F9FA` |

**Avoid:**
- Random neon overload
- Low-contrast text (target minimum 4.5:1 ratio for body text)
- More than 3 primary colors per carousel

---

## Layout Rules

Prioritize:
- Strong visual hierarchy
- Balanced spacing and clear alignment
- Intentional negative space
- Elegant composition and mobile readability
- Visual breathing room

**Safe Margins:**
- Top margin: 80–120px
- Bottom margin: 80–120px (leave room for brand footer)
- Left/Right padding: 72–96px
- Section spacing: 32–48px between content blocks

**Usable Content Area:**
- Instagram (1080×1350): X 72–1008px × Y 80–1270px
- LinkedIn (1080×1080): X 72–1008px × Y 80–1000px

The design must feel: **modern, polished, premium, professional, social-media optimized.**

---

## Visual Element Rules

Use visual elements only when they improve communication:
- Abstract shapes, cards, highlight containers
- Icon-style symbols built from SVG primitives (no external icon dependencies)
- Dividers, arrows, decorative gradients
- Minimal charts or diagrams if content requires it

**Effective SVG Elements:**

| Element | SVG Tag | Notes |
|---------|---------|-------|
| Highlight box | `<rect rx="16">` | Semi-transparent fill + accent left border |
| Accent line | `<rect width="6">` | Brand color, tall and narrow |
| Number badge | `<circle>` + `<text>` | Centered number, brand color fill |
| Gradient bg | `<linearGradient>` in `<defs>` | Subtle, 2-stop |
| Divider | `<line>` | Low opacity (0.2), full width |
| Rounded card | `<rect rx="20">` | Low opacity fill (0.08–0.12) |

**Every element must feel intentional** — support the message, improve readability, never create clutter.

---

## Consistency Rules

All slides must feel like one cohesive branded system. Maintain consistency in:
- Colors, typography, spacing, and margins
- Visual language, icon style, and layout logic
- Brand placement and design rhythm
- Corner radius values (pick one value and use it throughout)
- Font families and weight pairings

---

## Brand Identity Integration

If the user provides branding materials (logo, handle, colors), integrate them consistently:
- **Footer strip:** Handle at the bottom of every slide
- **Top corner:** Small logo or brand mark (optional)
- **CTA slide:** Prominent handle + call to action

**Footer strip SVG example:**
```xml
<!-- Instagram footer (adjust Y for LinkedIn: y="1030") -->
<rect x="0" y="1300" width="1080" height="50" fill="#0D1B2A"/>
<text x="540" y="1332" font-family="sans-serif" font-size="22"
      font-weight="600" fill="#FFFFFF" text-anchor="middle" opacity="0.85">
  @handle
</text>
```

**Branding should feel:** subtle, premium, clean, intentional. Never overpower the content.

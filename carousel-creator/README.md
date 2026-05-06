# Carousel Creator

Create premium, polished Instagram and LinkedIn carousel posts as individual SVG slides. Generate swipe-worthy, visually striking carousels that feel designed by a top-tier social media agency.

## When to Use This Skill

Trigger this skill when users want to create:
- Instagram carousel posts (4:5 portrait — 1080 × 1350 px)
- LinkedIn carousel content (1:1 square — 1080 × 1080 px)
- Educational carousels
- Brand-aware social media content
- Carousel slides from any topic, niche, or concept

## Output

**Individual SVG slides** per platform:

| Platform | Canvas Size | Aspect Ratio |
|----------|-------------|---------------|
| Instagram | 1080 × 1350 px | 4:5 portrait |
| LinkedIn | 1080 × 1080 px | 1:1 square |

- Minimum 5 slides, ideal 5–10 slides

Each SVG is:
- Complete and self-contained
- Visually clean and renderable
- Mobile-readable with proper typography hierarchy

## What This Skill Does

1. **Runs intake** — Collects topic, platform, audience, handle, brand colors, and tone
2. **Analyzes the topic** — Understands the niche, audience, and content goals
3. **Creates strategic flow** — Hook → Context → Value → Breakdown → Summary → CTA
4. **Designs premium slides** — Clean layouts, strong typography, intentional colors
5. **Generates SVG output** — Raw SVG code for each slide (no HTML/CSS)
6. **Integrates branding** — Uses brand colors, logos, handles if provided
7. **Writes caption & hashtags** — Generates a copy-paste-ready post caption saved to `caption.md`

## Key Features

- **Intake Workflow** — Collects platform, audience, handle, and brand info before generating
- **Platform-Aware** — Correct canvas size for Instagram (4:5) or LinkedIn (1:1)
- **Hook-First Design** — First slide uses proven hook formulas to stop scroll
- **Strategic Content Flow** — Maximizes retention, saves, and shares
- **Mobile-Optimized** — Readable on small screens, fast scanning
- **Brand Integration** — Subtle, premium branding with user's handle
- **Consistent System** — All slides feel like one cohesive carousel
- **CTA-Driven** — Final slide drives Follow, Save, and Share
- **Caption & Hashtags** — Generates a ready-to-post caption saved to `caption.md`

## Trigger Phrases

- "Create a carousel about..."
- "Make an Instagram carousel for..."
- "Design a carousel for LinkedIn"
- "Create swipe-worthy content"
- "Make a carousel post"
- "Generate social media carousel"

## Example Input

User provides:
- Topic: "5 AI Tools That Will Transform Your Content Creation"
- Audience: Content creators, marketers
- Brand colors: #FF6B35 (orange), #1A1A2E (dark blue)

Skill outputs:
- 7-8 SVG slides
- Hook slide with bold headline
- Context slide on why it matters
- Main value slides with tool breakdowns
- Summary slide with key takeaways
- CTA slide (Save, Follow, Share)

## Output Structure

Every run creates a date-stamped folder:

```
YYYYMMDD-HHMM/
├── slides/
│   ├── {topic-slug}-slide-1.svg   ← Hook slide
│   ├── {topic-slug}-slide-2.svg   ← Context
│   └── ...                        ← Value, breakdown, CTA
└── caption.md                     ← Copy-paste-ready post caption + hashtags
```

Open any `.svg` file in a browser to preview. Convert to PNG/JPG for posting.

## Files

```
carousel-creator/
├── SKILL.md                        # Main skill instructions
├── README.md                       # This file
└── references/
    ├── design-system.md            # Typography, colors, layout, brand identity
    ├── content-strategy.md         # Writing rules, CTAs, caption & hashtag format
    └── svg-templates.md            # SVG structure, layout patterns, reusable snippets
```

## What Makes This Different

This skill generates **actual SVG code** that can be:
- Opened in any browser to view
- Imported into design tools
- Converted to PNG/JPG for posting
- Directly used on social platforms

It does NOT output:
- HTML or CSS layouts
- React components
- Website mockups
- Markdown descriptions

Only polished, renderable SVG slides.
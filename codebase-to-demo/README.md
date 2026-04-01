# Codebase-to-Demo

Transform any codebase or automation implementation into a compelling, interactive single-page HTML demo deck built for non-technical buyers and decision-makers.

## Overview

This skill enables AI agents to convert technical implementations into polished, client-facing presentation materials. The output is a single self-contained HTML file that sells the *value* of the implementation through animated architecture diagrams, before/after comparisons, sequence walkthroughs, and a business-first narrative.

## When to Use This Skill

Trigger this skill when users mention:
- "create a demo for this"
- "make a pitch deck from this codebase"
- "show this to a client"
- "explain this implementation to a non-technical audience"
- "demo deck"
- "showcase this automation"
- "create a client presentation from this project"

## Input Methods

Users can provide their codebase in several ways:
- **A local folder** — e.g., "create a demo from ./my-automation"
- **A GitHub link** — e.g., "make a demo deck from https://github.com/user/repo"
- **The current project** — if already in a codebase, say "create a demo for this"

## The Pitch-Mode Mindset

This is not a learning tool. It is a **selling tool**. Every design and content decision should serve one goal: helping the buyer understand the value of what was built and feel confident saying yes.

### Business Value Framing

| Technical framing (wrong) | Business framing (right) |
|---|---|
| "This uses a webhook to trigger n8n" | "The moment a lead fills out your form, this kicks off automatically — no one has to press a button" |
| "Data is stored in a Postgres database" | "Every record is saved permanently, searchable, and exportable — nothing lives in someone's inbox" |
| "The API rate limit is 100 req/min" | "The system handles up to 100 requests per minute — enough for most growing businesses without any upgrade" |
| "Error handling retries 3 times" | "If anything goes wrong, it automatically tries again before alerting you — most errors fix themselves" |
| "Built with n8n and OpenAI" | "Built on tools used by thousands of businesses worldwide, with active communities and long-term support" |

**Never lead with technology.** Always lead with the problem it solves. The tech is the *proof*, not the *point*.

## The Process (4 Phases)

### Phase 1: Implementation Analysis

Before writing any HTML, deeply analyze the codebase to extract the business story.

**What to extract:**
- **The core problem** — what was the buyer doing manually, expensively, or inconsistently before this?
- **The transformation** — what does the system do that humans no longer have to?
- **The cast of components** — the main actors (services, APIs, databases, automations) and their business-level roles
- **The data journey** — what enters the system, how it's processed, and what comes out
- **External integrations** — every third-party tool, API, or platform the system touches
- **The tech stack** — what was chosen, and the business reason why (stability, cost, flexibility, etc.)
- **Failure modes** — how the system handles errors, retries, and edge cases
- **Scale and deployment** — how it's hosted, who maintains it, what happens as volume grows

### Phase 2: Demo Structure Design

Structure the demo as **6-9 modules** following the Pitch Arc:

| Module | Buyer's question | What to show |
|---|---|---|
| 1 — The Problem | "Do you understand my world?" | The old way: manual, slow, error-prone. Use the Before/After Toggle. |
| 2 — The Solution | "What does this actually do?" | A one-screen overview with the Integration Map. |
| 3 — How It Works | "Walk me through it" | The Sequence Diagram — step-by-step animated trace. |
| 4 — The Architecture | "What are the moving parts?" | The Clickable Architecture Map. |
| 5 — What Could Break | "What happens when something goes wrong?" | The "What Would Break If…" Explorer. |
| 6 — Why These Tools | "Why not just use [X]?" | Tech Stack Justification. |
| 7 — Integrations | "What does it plug into?" | Integration Map detail. |
| 8 — Going Live | "How do we actually run this?" | Deployment & Scaling Notes. |
| 9 — Next Steps | "What happens after I say yes?" | Implementation timeline and next steps. |

### Phase 3: Build the Demo

Generate a single HTML file with embedded CSS and JavaScript. The file must be completely self-contained (only external dependency: Google Fonts CDN).

**Build order:**
1. Foundation first — HTML shell, complete CSS, navigation bar with module titles, scroll-snap behavior
2. One module at a time — Build, verify, then move on
3. Interactive elements pass — Add maps, diagrams, toggles after content scaffold
4. Polish pass — Transitions, mobile responsiveness, visual consistency

### Phase 4: Review and Deliver

After generating the HTML file, walk through each module and confirm the business narrative is coherent. Ask: "Does this answer the buyer's questions in the right order?"

## Interactive Elements

This skill uses specialized interactive elements designed for sales presentations. Each element serves a specific buyer question.

### Core Elements

1. **Before/After Toggle** — Makes the "old way" visceral so the buyer feels the pain before seeing the solution
2. **Clickable Architecture Map** — SVG-based diagram where buyers click components to learn what they do
3. **Sequence Diagram** — Step-by-step animated trace of one real workflow
4. **"What Would Break If" Explorer** — Proactively addresses fragility fears
5. **Integration Map** — Shows what the system connects to with hub-and-spoke layout
6. **Tech Stack Justification** — One card per tool with business reasons
7. **Deployment & Scaling Notes** — Three-column layout showing day 1 / 6 months / at scale

### Learning Elements

The demo can also incorporate educational elements for context:
- Code ↔ English Translation Blocks
- Drag-and-Drop Matching
- Group Chat Animation
- Message Flow Animation
- "Spot the Bug" Challenge
- Callout Boxes
- Pattern Cards
- And more...

## Design Identity

The visual design should feel like a **polished agency deliverable**:

- **Clean, premium palette**: White or very light neutral backgrounds with one strong accent color
- **Typography**: Display font for module titles (Bricolage Grotesque or Cabinet Grotesk), clean sans-serif for body
- **Generous whitespace**: Every module breathes
- **Subtle animation**: Flows, fades, and slides — nothing flashy
- **Mobile-first**: Demos are often opened on phones; every interactive element must work with touch
- **Dark navigation bar**: Fixed top bar with module names, progress indicator

## Content Rules

### Lead With Pain, Not Features
Every module opens with the buyer's problem, not the solution.

### Numbers Make It Real
Include estimates: time saved, error rate reduction, cost per transaction, volume capacity.

### No Code in the Demo
This demo is for buyers, not developers. **Never show raw code.** Use diagrams, plain-language descriptions, or visual traces.

### Plain Language, Always
Every technical term must be replaced with its business equivalent or immediately followed by a plain-language definition.

### Honest About Limitations
Surface real limitations proactively in the "What Would Break If…" section. Buyers who discover limitations after they've agreed feel deceived.

## Output

This skill produces **one file**: `[project-name]-demo.html`

The file is:
- Completely self-contained (open in any browser, share via email, works offline)
- Presenter-ready (keyboard navigation, large touch targets)
- Client-shareable (no login, no install, no dependencies)
- Print-friendly (CSS `@media print` strips navigation and renders each module as a page)

## Directory Structure

```
codebase-to-demo/
├── SKILL.md                    # Main skill definition
├── references/
│   ├── interactive-elements.md # All interactive element implementations
│   └── design-system.md        # Design tokens and styling guidelines
└── README.md                   # This file
```

## Files Reference

### SKILL.md
The main skill file containing the complete skill definition, process phases, interactive elements specifications, content rules, and design identity guidelines.

### references/interactive-elements.md
Comprehensive implementation patterns for every interactive element used in demo decks:
- Code translation blocks
- Drag-and-drop matching
- Group chat animations
- Architecture diagrams
- Before/After toggles
- Sequence diagrams
- And 15+ more element types

### references/design-system.md
Design tokens and styling guidelines for consistent implementation.

## Quality Criteria

After generating a demo, verify:
1. Every module answers a real buyer question
2. The business narrative is coherent end-to-end
3. No raw code is displayed
4. All technical terms are explained in plain language
5. Numbers are specific, not vague
6. Limitations are surfaced proactively
7. Mobile touch targets are at least 44×44px
8. The file works offline

## Author Notes

This skill was designed for AI agencies, freelancers, and in-house builders who want to present their work compellingly to clients or stakeholders without spending hours in Figma or PowerPoint.

The tone should be confident, clear, and outcome-focused — like a senior consultant presenting to a board.

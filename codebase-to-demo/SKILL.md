---
name: codebase-to-demo
description: Turn any codebase or automation implementation into a beautiful, interactive single-page HTML demo deck for non-technical buyers and decision-makers. Use this skill whenever someone wants to create a client-facing demo, implementation showcase, pitch deck, or sales presentation from a codebase or project. Also trigger when users mention 'create a demo for this,' 'make a pitch deck from this codebase,' 'show this to a client,' 'explain this implementation to a non-technical audience,' 'demo deck,' 'showcase this automation,' or 'create a client presentation from this project.' This skill produces a stunning, self-contained HTML file with scroll-based modules, animated architecture maps, before/after comparisons, sequence diagrams, integration maps, and a deployment overview — all framed around business value, not technical learning.
---

# Codebase-to-Demo

Transform any codebase or automation implementation into a compelling, interactive single-page HTML demo deck built for non-technical buyers and decision-makers. The output is a single self-contained HTML file (no dependencies except Google Fonts) that sells the *value* of the implementation through animated architecture diagrams, before/after comparisons, sequence walkthroughs, and a business-first narrative.

## First-Run Welcome

When the skill is first triggered and the user hasn't specified a codebase yet, introduce yourself:

> **I can turn any implementation into an interactive demo deck for your clients — no technical knowledge required from them.**
>
> Just point me at a project:
>
> * **A local folder** — e.g., "create a demo from ./my-automation"
> * **A GitHub link** — e.g., "make a demo deck from https://github.com/user/repo"
> * **The current project** — if you're already in a codebase, say "create a demo for this"
>
> I'll analyze the implementation, identify the business problems it solves, and generate a polished single-page HTML demo deck with animated diagrams, before/after comparisons, and a clear value story. The whole thing runs in your browser — shareable as a single file, works offline.

If the user provides a GitHub link, clone the repo first (`git clone <url> /tmp/<repo-name>`) before starting the analysis. If they say "this codebase" or similar, use the current working directory.

---

## Who This Is For

The **viewer** of this demo is a **non-technical buyer** — a business owner, department head, or executive who cares about outcomes, not code. They are evaluating whether this implementation is worth their time, money, or trust. They have zero interest in how the code is structured. They want to know:

1. **What problem does this solve for me?**
2. **How does it actually work at a high level?**
3. **What does it connect to / replace / integrate with?**
4. **Will it break? Who maintains it? Can it scale?**
5. **Why these tools? Why this approach?**

The **creator** of this demo is typically an AI agency, freelancer, or in-house builder who wants to present their work compellingly to a client or stakeholder without spending hours in Figma or PowerPoint.

**Tone:** Confident, clear, outcome-focused. Like a senior consultant presenting to a board — not a developer showing a side project. Every sentence earns its place by answering "so what?" for the buyer.

---

## The Pitch-Mode Mindset

This is not a learning tool. It is a **selling tool**. Every design and content decision should serve one goal: helping the buyer understand the value of what was built and feel confident saying yes.

**Reframe everything through business value:**

| Technical framing (wrong) | Business framing (right) |
|---|---|
| "This uses a webhook to trigger n8n" | "The moment a lead fills out your form, this kicks off automatically — no one has to press a button" |
| "Data is stored in a Postgres database" | "Every record is saved permanently, searchable, and exportable — nothing lives in someone's inbox" |
| "The API rate limit is 100 req/min" | "The system handles up to 100 requests per minute — enough for most growing businesses without any upgrade" |
| "Error handling retries 3 times" | "If anything goes wrong, it automatically tries again before alerting you — most errors fix themselves" |
| "Built with n8n and OpenAI" | "Built on tools used by thousands of businesses worldwide, with active communities and long-term support" |

**Never lead with technology.** Always lead with the problem it solves. The tech is the *proof*, not the *point*.

---

## The Process (4 Phases)

### Phase 1: Implementation Analysis

Before writing any HTML, deeply analyze the codebase to extract the business story. Read all key files, trace data flows, and identify what manual processes this automates or improves.

**What to extract:**

* **The core problem** — what was the buyer doing manually, expensively, or inconsistently before this?
* **The transformation** — what does the system do that humans no longer have to?
* **The cast of components** — the main actors (services, APIs, databases, automations) and their business-level roles
* **The data journey** — what enters the system, how it's processed, and what comes out
* **External integrations** — every third-party tool, API, or platform the system touches
* **The tech stack** — what was chosen, and the business reason why (stability, cost, flexibility, etc.)
* **API & service costs** — every external API, paid service, or SaaS tool with pricing tiers (e.g., OpenAI, Anthropic, Stripe, Twilio, Supabase, Railway, etc.). Note the expected usage volume from the codebase.
* **Failure modes** — how the system handles errors, retries, and edge cases
* **Scale and deployment** — how it's hosted, who maintains it, what happens as volume grows
* **App entry point** — identify how to start the app locally (`package.json` scripts, `Makefile`, README start command, `pyproject.toml` etc.) so real screenshots can be captured before building the HTML

**Figure out the business context yourself.** Read the README, the workflow files, the API calls, and the config. Infer the industry and use case from the code. The demo should open with a crisp statement of what problem this solves — written for a buyer, not a developer.

### Phase 2: Demo Structure Design

Structure the demo as **6-9 modules** following the Pitch Arc below. Each module corresponds to a question in the buyer's mind. Answer their questions in the order they naturally arise — don't front-load technical details.

**The Pitch Arc:**

| Module | Buyer's question | What to show |
|---|---|---|
| 0 — The Hook | *[No question — this is the hook before they start asking]* | Two lines. Full-screen. Punchy opener that names their pain and teases the reveal. The audience leans in before Module 1 starts. |
| 1 — The Problem | "Do you understand my world?" | The old way: manual, slow, error-prone. Use the Before/After Toggle to make it visceral. |
| 2 — The Solution | "What does this actually do?" | A one-screen overview with the Integration Map — every input, output, and connection at a glance. |
| 3 — How It Works | "Walk me through it" | The Sequence Diagram — a step-by-step animated trace of one real workflow, narrated in plain language. |
| 4 — The Architecture | "What are the moving parts?" | The Clickable Architecture Map — click any component to zoom into what it does and why it matters. |
| 5 — What Could Break | "What happens when something goes wrong?" | The "What Would Break If…" Explorer — show resilience, retry logic, and alerts in a visual way. |
| 6 — Why These Tools | "Why not just use [X]?" | Tech Stack Justification — one card per tool, with the business reason it was chosen over alternatives. |
| 7 — Integrations | "What does it plug into?" | Integration Map detail — each connected platform with logo, what data flows in/out, and setup complexity. |
| 8 — Going Live | "How do we actually run this?" | Deployment & Scaling Notes — hosting, maintenance, calculated API costs (INR with USD toggle), who to call when something breaks. |
| 8.5 — See It In Action | "Is this real or just a concept?" | Screenshots gallery: 3-6 actual screenshots of the running app and codebase. Lightbox layout. Plain-language captions. Proof it's built and working. |
| 9 — Next Steps | "What happens after I say yes?" | A clear, confident close: implementation timeline, what you need from them, and what they get. |

**Hook Writing Rules (Module 0):**

Module 0 is a full-screen opener — two lines, nothing else. Write them like this:

- **Line 1:** A provocative stat or question that names a *specific* cost pulled from Phase 1 analysis — time lost, money wasted, error rate, or headcount. Make the audience feel the weight of the current reality. Example: *"Your team spends 3 hours every Friday copying data between systems that should talk to each other automatically."*
- **Line 2:** A confident tease of what they're about to see — one sentence, specific outcome. Example: *"In the next 10 minutes, you'll see exactly how that's already been solved — for your business, with your data."*

Both lines together must be readable in under 5 seconds. No bullets. No diagrams. No nav bar on this slide — the hook stands alone. Background: dark (`#0F1117`). Font: Bricolage Grotesque at display scale, centered, generous vertical padding. Underline the key pain phrase in Line 1 with the accent color.

Not every implementation needs all 9. A simple two-step automation might only need 5-6 modules. Use judgment — every module must earn its place by answering a real buyer question.

**Do NOT present the structure for approval — just build it.** The user wants a demo, not a planning session.

### Phase 3: Build the Demo

Generate a single HTML file with embedded CSS and JavaScript. The file must be completely self-contained (only external dependency: Google Fonts CDN).

**Build order:**

0. **Screenshots first** — Before writing any HTML, attempt to capture real screenshots using Playwright browser tools (see Interactive Element 8). Start the app, navigate to key screens, capture and base64-encode 3-6 images. Store them as variables for embedding later. If the app can't be started, note which placeholder slots to leave.
1. **Foundation first** — HTML shell, complete CSS, navigation bar with module titles (not numbers — use the question the module answers, e.g., "How It Works"), scroll-snap behavior, keyboard navigation. Module order: Hook → Problem → Solution → How It Works → Architecture → What Could Break → Why These Tools → Integrations → Going Live → Screenshots → Next Steps.
2. **One module at a time** — Build Module 0 (Hook) first, verify it looks right, then Module 1. Never try to write all modules in one pass.
3. **Interactive elements pass** — Add the Clickable Architecture Map, Sequence Diagram, Before/After Toggle, and "What Would Break" Explorer after the content scaffold is in place.
4. **Polish pass** — Transitions, mobile responsiveness, visual consistency, animation timing.

**Critical implementation rules:**

* Use CSS `scroll-snap-type: y proximity` (never `mandatory`)
* Use `min-height: 100dvh` with `100vh` fallback
* Only animate `transform` and `opacity` for GPU performance
* Wrap all JS in an IIFE, use `passive: true` on scroll listeners
* All interactive element click targets must be at least 44×44px (touch-friendly)
* Presenter-friendly: keyboard arrows advance modules, ESC returns to overview

### Phase 4: Review and Deliver

After generating the HTML file, open it in the browser. Walk through each module and confirm the business narrative is coherent end-to-end. Ask: "Does this answer the buyer's questions in the right order?"

Also verify:
- **The Hook (Module 0):** Read the two lines aloud. Do they land in under 5 seconds? Does Line 1 name a specific cost? Does Line 2 create genuine anticipation? If not, rewrite.
- **Screenshots (Module 8.5):** Are all images loading? Are captions in plain buyer language? Does the lightbox open and close correctly with both click and ESC?

---

## Interactive Elements (Required)

These are not optional decorations. Each one is a specific answer to a buyer question. Build at least 4 of the following per demo.

### 1. Before/After Toggle

**Purpose:** Make the "old way" visceral so the buyer feels the pain before seeing the solution.

**Implementation:**
- Two-panel layout with a sliding toggle or tab switch
- LEFT panel: "Before" — the old manual process shown as a timeline of human steps (with time estimates, error risks, and handoff delays called out as red badges)
- RIGHT panel: "After" — the automated process, same timeline but most steps replaced with green "automated" badges, human steps reduced to review/approve only
- Animate the transition between states: cards collapse/expand, colors shift from warm-red to cool-green
- Below the toggle: a single stat callout — "From 4 hours to 8 minutes" or "From 60% error rate to <1%"

```html
<!-- Structure pattern -->
<div class="before-after-toggle">
  <div class="toggle-controls">
    <button class="toggle-btn active" data-panel="before">Before</button>
    <button class="toggle-btn" data-panel="after">After</button>
  </div>
  <div class="panel before-panel active">
    <!-- Timeline of manual steps with pain-point badges -->
  </div>
  <div class="panel after-panel">
    <!-- Same timeline with automated step badges -->
  </div>
</div>
```

**Animation:** Use `transform: translateX` and `opacity` to transition between panels. Duration: 400ms ease-in-out. Stagger each timeline step by 80ms.

### 2. Clickable Architecture Map

**Purpose:** Give buyers a mental model of the system without overwhelming them. They click what they're curious about.

**Implementation:**
- SVG-based diagram with labeled component nodes (use business names, not technical ones: "Lead Capture" not "Webhook endpoint")
- Connecting lines animate on load with a flowing dot effect (SVG `stroke-dashoffset` animation) to show data direction
- Each node is clickable — clicking opens a slide-up panel with: what this component does in one sentence, what goes in, what comes out, and which module in the demo covers it in detail
- Active node gets a highlight ring; inactive nodes dim slightly
- Include a "Reset" button to return all nodes to default state

```javascript
// Node click handler pattern
node.addEventListener('click', () => {
  document.querySelectorAll('.arch-node').forEach(n => n.classList.remove('active'));
  node.classList.add('active');

  detailPanel.innerHTML = `
    <h3>${nodeData.businessName}</h3>
    <p>${nodeData.oneLineSummary}</p>
    <div class="io-row">
      <span class="input-badge">IN: ${nodeData.input}</span>
      <span class="output-badge">OUT: ${nodeData.output}</span>
    </div>
  `;
  detailPanel.classList.add('visible');
});
```

**Node naming convention:** Always use buyer-language. "Form Submission" not "Webhook trigger." "AI Processor" not "LLM call." "Client Notification" not "SMTP send."

### 3. Sequence Diagram (Step-by-Step Animated Trace)

**Purpose:** Walk the buyer through exactly what happens when a real event occurs — like a behind-the-scenes tour of one transaction.

**Implementation:**
- Pick the most important single workflow (e.g., "A new lead submits your contact form")
- Show it as a vertical timeline with 5-10 steps, each with: a step number, a plain-language description, the component involved (as a colored badge), and the time elapsed
- Steps animate in one at a time, driven by a "Next Step" button or auto-advance on a timer
- A progress bar at the top shows how far through the workflow you are
- Each step can optionally expand to show a "behind the scenes" callout — one sentence of slightly more technical detail for buyers who want it
- At the end: a summary card showing total time (automated) vs. estimated manual time

```html
<!-- Step structure pattern -->
<div class="seq-step" data-step="3">
  <div class="step-marker">3</div>
  <div class="step-body">
    <div class="step-component-badge" style="background: var(--accent-ai)">AI Processor</div>
    <p class="step-description">The lead's message is analyzed to detect intent, urgency, and industry — taking about 1.2 seconds.</p>
    <span class="step-time">+1.2s</span>
    <details class="step-detail">
      <summary>Behind the scenes</summary>
      <p>OpenAI's GPT-4o reads the message and returns a structured JSON object with intent score, urgency level, and suggested response category.</p>
    </details>
  </div>
</div>
```

**Key rule:** The scenario must use a *real* example from the actual system. Don't make up generic steps — trace an actual data flow from the codebase.

### 4. "What Would Break If…" Explorer

**Purpose:** Proactively address the buyer's fear of fragility. Show that the system handles failure gracefully.

**Implementation:**
- A visual of the Architecture Map (simplified) with each component shown as a node
- Below it: a list of "What if…" scenario buttons (3-5 scenarios)
  - e.g., "What if the AI API goes down?", "What if a webhook fires twice?", "What if the database is full?"
- Clicking a scenario highlights the affected nodes in amber/red and shows a panel explaining: what happens (the failure mode), how the system responds (retry, fallback, alert), and what the buyer/user would see
- Healthy nodes stay green; affected nodes pulse amber; critical failures show red
- A "Recovery" button resets to green and shows estimated recovery time

```javascript
// Scenario definition pattern
const scenarios = [
  {
    label: "What if the AI API goes down?",
    affectedNodes: ['ai-processor'],
    severity: 'amber',
    failureMode: "New submissions can't be classified automatically.",
    systemResponse: "The system queues the submission and retries every 5 minutes for up to 2 hours.",
    buyerExperience: "You'd receive a Slack alert. The lead is saved — nothing is lost.",
    recoveryTime: "Auto-recovers when API is restored, typically <30 min."
  },
  // ...
];
```

### 5. Integration Map

**Purpose:** Show the buyer what the system connects to — making it feel substantial and well-integrated with their existing tools.

**Implementation:**
- Hub-and-spoke layout: the core system in the center, external integrations as spokes
- Each integration node shows: the platform logo (use inline SVG or emoji as fallback), the platform name, and a one-line description of what data flows in/out
- Hovering a spoke highlights the connection and shows a tooltip: direction of data flow, frequency, and what happens if this connection breaks
- Color-code by integration type: CRM (blue), communication (green), storage (yellow), AI/processing (purple), payments (teal)
- A legend explains the colors

**Integration node content (per spoke):**
```
[Platform Logo]
Platform Name
"Receives confirmed leads every time a form is submitted"
Data direction: → OUT
Frequency: Real-time
If disconnected: Queued until reconnected
```

**Critical:** Use the real integrations from the codebase. Don't make up integrations that don't exist.

### 6. Tech Stack Justification

**Purpose:** Answer "why not just use [simpler/cheaper/alternative]?" before the buyer asks it.

**Implementation:**
- One card per major technology choice (3-6 cards)
- Each card contains: tool name + logo, one-sentence business role ("n8n: the automation backbone that connects all moving parts"), the key reason it was chosen over alternatives (frame as a business benefit, not a technical preference), and a "vs. alternative" row showing what was considered and why this won
- Cards laid out in a 2-3 column grid
- A summary line at the bottom: total cost estimate for the stack at the buyer's scale

```html
<!-- Card structure pattern -->
<div class="stack-card">
  <div class="stack-header">
    <span class="stack-logo">⚙️</span>
    <h3>n8n</h3>
    <span class="stack-role">Automation Backbone</span>
  </div>
  <p class="stack-reason">Self-hosted, so your data never leaves your infrastructure. Unlimited workflows at a flat monthly cost — no per-task pricing that grows with volume.</p>
  <div class="stack-vs">
    <span class="vs-label">vs. Zapier:</span>
    <span class="vs-reason">Zapier charges per task — at your volume, n8n is 10× cheaper and you own the data.</span>
  </div>
</div>
```

### 7. Deployment & Scaling Notes

**Purpose:** Address the "what happens after we go live?" fear. Buyers who don't understand ops often imagine a fragile DIY contraption.

**Implementation:**
- Three-column layout: "Day 1" / "After 6 Months" / "At Scale"
- Each column shows: infrastructure, expected volume, monthly cost estimate, maintenance burden (hours/month), and who handles what
- A simple uptime/reliability callout: "Hosted on [platform], which guarantees 99.9% uptime"
- A "Who to call" section: clear ownership of each component (you/client/vendor)
- If relevant: a data retention and backup summary

**Tone:** Calm and reassuring. The buyer should feel like they're buying a managed service, not inheriting a DIY project.

### 8. Screenshots Gallery

**Purpose:** Prove the implementation is real and working — not just a concept deck. Show the buyer what they'd actually see if they opened the app today.

**Implementation:**

**Step 1 — Capture screenshots before writing HTML.**

Try to capture real screenshots using Playwright browser tools:

1. Read the project's `package.json`, `Makefile`, or README to find the start command
2. Launch the app locally (e.g., `npm run dev`, `python app.py`, `uvicorn main:app`)
3. Use `mcp__plugin_playwright_playwright__browser_navigate` to open the running app
4. Use `mcp__plugin_playwright_playwright__browser_take_screenshot` to capture 2-4 app UI screens (landing page, main dashboard, a key workflow result, a data output view)
5. For code screenshots: navigate to a key source file and capture it rendered with syntax highlighting (open in a browser-based viewer or the IDE)
6. Encode each screenshot as a base64 data URI for embedding directly in the HTML `<img src="data:image/png;base64,...">`

**Fallback:** If Playwright is unavailable or the app cannot be started, build placeholder cards — a styled `<div>` per screenshot slot labelled *"Screenshot [N]: [describe what to capture here]"* — and add a comment in the HTML instructing the user to replace them.

**Target: 3-6 screenshots.** Suggested breakdown:
- 2-3 app UI screens (what the buyer would actually see and interact with)
- 1-2 code/architecture screenshots as proof-of-craft (the main workflow file, syntax highlighted)

**Exception to the "No Code" rule:** This module is the one place where a screenshot of code is appropriate — it signals craftsmanship without asking the buyer to read code. Caption code screenshots as: *"Under the hood: the automation logic, built for reliability."*

**Step 2 — Build the gallery module.**

```html
<!-- Gallery structure pattern -->
<section class="module screenshots-gallery">
  <h2 class="module-headline">See It In Action</h2>
  <p class="module-subhead">Real screens from the live implementation — not mockups.</p>
  <div class="gallery-grid">
    <div class="gallery-card" data-lightbox="1">
      <img src="data:image/png;base64,..." alt="The main dashboard after a lead is processed" loading="lazy">
      <p class="gallery-caption">The dashboard updates the moment a new lead comes in — no refresh needed.</p>
    </div>
    <!-- repeat for each screenshot -->
  </div>

  <!-- Lightbox overlay -->
  <div class="lightbox" id="lightbox" hidden>
    <button class="lightbox-close" aria-label="Close">✕</button>
    <img class="lightbox-img" src="" alt="">
    <p class="lightbox-caption"></p>
  </div>
</section>
```

**Gallery CSS rules:**
- Grid: `display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem`
- Cards: `border-radius: 12px; overflow: hidden; box-shadow: var(--shadow-md); cursor: zoom-in`
- Images: `width: 100%; aspect-ratio: 16/9; object-fit: cover`
- Captions: DM Sans, 14px, muted color, padding 12px

**Lightbox JavaScript:**
```javascript
// Lightbox handler
document.querySelectorAll('.gallery-card').forEach(card => {
  card.addEventListener('click', () => {
    const img = card.querySelector('img');
    const caption = card.querySelector('.gallery-caption').textContent;
    document.getElementById('lightbox').removeAttribute('hidden');
    document.querySelector('.lightbox-img').src = img.src;
    document.querySelector('.lightbox-caption').textContent = caption;
  });
});
document.querySelector('.lightbox-close').addEventListener('click', () => {
  document.getElementById('lightbox').setAttribute('hidden', '');
});
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') document.getElementById('lightbox').setAttribute('hidden', '');
});
```

---

## Content Rules

### Lead With Pain, Not Features

Every module opens with the buyer's problem, not the solution. "Right now, your team spends 3 hours every Friday manually copying data between systems. Here's how this changes that." Pain first. Solution second.

### Numbers Make It Real

Wherever possible, include estimates: time saved, error rate reduction, cost per transaction, volume capacity. If you can't find exact numbers in the codebase, use conservative estimates based on the architecture and flag them as estimates. Vague benefits ("saves time") are weak. Specific benefits ("reduces processing time from 45 minutes to 90 seconds") are compelling.

### Estimate Real API Costs

When building Module 8, calculate actual execution costs instead of using static examples:

1. **Identify all paid services:** List every external API, hosting platform, and SaaS tool used in the codebase
2. **Research current pricing:** Use web search to find the latest pricing for each service (e.g., OpenAI GPT-4 pricing, Supabase storage costs, Railway compute pricing)
3. **Calculate monthly estimates:** Based on the expected usage inferred from the codebase (API call frequency, data volume, user count)
4. **Convert to INR:** Fetch live USD→INR rate, add 2-5% conversion levy for international transactions
5. **Show per-API breakdown:** Display each service's estimated monthly cost separately in INR
6. **Include currency toggle:** Add a toggle to switch between INR and USD views (default to INR)
7. **Show rate source:** Display "Rate from [source] on [date] with X% levy applied"
8. **Add total row:** Show the sum of all API costs as "Estimated Monthly Cost"

Example output format:
```
┌─────────────────────────────────────────┐
│  Estimated API Costs (INR)    [INR|USD] │
├─────────────────────────────────────────┤
│  OpenAI GPT-4 API        ₹4,500/month   │
│  Supabase Database       ₹1,200/month   │
│  Railway Hosting         ₹2,000/month   │
│  ─────────────────────────────────────   │
│  Total                   ₹7,700/month   │
│                                         │
│  Rate: 1 USD = ₹83.50 + 2.5% levy       │
│  Source: exchangerate.host, Apr 2026    │
└─────────────────────────────────────────┘
```

### No Code in the Demo

This demo is for buyers, not developers. **Never show raw code.** If you need to illustrate something technical, use a diagram, a plain-language description, or a visual trace — never a code block. The one exception: a very short, heavily commented snippet in the "Behind the Scenes" expandable sections — and even then, only if it genuinely adds value for a technically curious buyer.

### Plain Language, Always

Every technical term must be replaced with its business equivalent or immediately followed by a plain-language definition. "Webhook" → "an automatic notification your system sends the moment something happens." "API" → "a connection between two software systems." "Database" → "a permanent, searchable record of everything that's passed through the system."

### One Business Outcome Per Module

Each module exists to make the buyer believe one specific thing about the value of the implementation. State it as a headline at the top of the module ("Your team never has to touch this manually again") and let everything in the module prove that claim.

### Honest About Limitations

If the system has real limitations, constraints, or known failure modes, surface them proactively in the "What Would Break If…" section. Buyers who discover limitations after they've agreed feel deceived. Buyers who are told limitations upfront feel respected — and it builds trust in everything else you've said.

---

## Design Identity

The visual design should feel like a **polished agency deliverable** — professional, modern, and confident. Not a generic template. Not a toy.

* **Clean, premium palette**: White or very light neutral backgrounds. One strong accent color (deep teal, electric blue, or rich amber — pick based on the client's brand if known). No purple gradients.
* **Typography**: Display font for module titles (Bricolage Grotesque or Cabinet Grotesk). Clean sans-serif for body (DM Sans or Inter at a pinch). Never Comic Sans, never Times New Roman.
* **No code fonts**: Since there's no code in the demo, JetBrains Mono is only used for data values, IDs, or endpoint paths in technical callouts.
* **Generous whitespace**: Every module breathes. Decision-makers skim — make every screen scannable in 5 seconds.
* **Subtle animation**: Flows, fades, and slides. Nothing that flashes, spins, or distracts. The animation should feel inevitable, not showy.
* **Mobile-first thinking**: Demos are often opened on phones. Every interactive element must work with touch. No hover-only interactions.
* **Dark navigation bar**: Fixed top bar with module names (not numbers), progress indicator, and the implementation name. Dark background (#0F1117 or similar) with light text.

---

## Gotchas — Common Failure Points

### Accidentally Teaching Instead of Selling
The most common failure: the demo starts explaining how things work instead of why they matter. Every sentence should pass the "so what?" test from a buyer's perspective. If the answer is "it's technically interesting," cut it.

### Too Much Architecture Detail
Non-technical buyers don't need to know about every microservice, every table, every edge case. Show the 5-7 components that tell the business story. Everything else is noise.

### No Before State
Without the Before/After Toggle, the buyer has no frame of reference for how good the After is. Always show the pain before showing the solution.

### Generic Integration Map
Listing "connects to Slack" without saying *what* flows to Slack, *when*, and *why the buyer cares* is useless. Every integration spoke must answer: "what does this mean for me?"

### Fragility Theater
Showing only success paths makes the system look brittle ("what happens when it breaks?"). The "What Would Break If…" Explorer preempts this fear — don't skip it.

### Tooltip Clipping (Technical)
Any tooltips must use `position: fixed` and be appended to `document.body`. Calculate position from `getBoundingClientRect()`. Never rely on `position: absolute` inside overflow-hidden containers.

### Scroll-Snap Mandatory
Always use `scroll-snap-type: y proximity`, never `mandatory`.

### Module Quality Degradation
Build one module at a time and verify each before moving on. Later modules built in one pass are always thinner and weaker.

---

## Output

This skill produces **one file**: `[project-name]-demo.html`

The file is:
- Completely self-contained (open in any browser, share via email, works offline)
- Presenter-ready (keyboard navigation, large touch targets)
- Client-shareable (no login, no install, no dependencies)
- Print-friendly (CSS `@media print` strips navigation and renders each module as a page)

After generating, open the file in the browser, walk through it end-to-end, and ask: **"If I were the buyer, would I say yes after seeing this?"**

---

## Reference Files

The `references/` directory contains detailed implementation specs. Read them when you reach the relevant phase:

- **`references/design-system.md`** — Complete CSS custom properties, color palette, typography scale, spacing system, shadows, animations, scrollbar styling. Read this before writing any CSS.
- **`references/interactive-elements.md`** — Implementation patterns for every interactive element: code↔English translations, group chat animations, message flow visualizations, architecture diagrams, pattern cards, callout boxes. Read this before building any interactive elements.

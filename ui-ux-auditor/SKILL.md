---
name: ui-ux-auditor
description: Perform a thorough, structured UI/UX audit of an application. Use when given a video recording, YouTube URL, live web URL, or a zip/set of screenshots of an application and asked to audit, review, or evaluate its design, usability, or launch-readiness.
---

# UI/UX Auditor Skill

A senior-level UI/UX audit framework that evaluates applications for launch readiness, usability, visual polish, accessibility, and product risk. Covers 11 structured audit dimensions and produces an actionable, brutally honest report.

---

## When to Use This Skill

Activate this skill when the user:
- Provides a **video recording** of their app and asks for a UI/UX review
- Provides a **YouTube URL** to a demo or walkthrough
- Provides a **web URL** of a live or staging application
- Provides a **zip file or set of screenshots** of their application
- Asks for a "pre-launch audit", "UX review", "design critique", "usability report", or similar

---

## Step 1 — Identify Input Type

Before doing anything else, determine what the user has provided:

| Input Type | How to Handle |
|---|---|
| **Video file** (mp4, webm, mov) | Use the `view_file` tool to load the video as context, then analyze frame-by-frame |
| **YouTube URL** | Use `browser_subagent` to navigate to the URL, take screenshots of key moments using the browser tool |
| **Live web URL** | Use `browser_subagent` to fully navigate the app — visit all pages, interact with forms, menus, and CTAs; capture screenshots at every major screen |
| **Zip file of screenshots** | Use `run_command` to unzip (`unzip <file> -d <dir>`), then use `view_file` on each image |
| **Individual screenshot images** | Use `view_file` on each image directly |

> **If the input type is unclear**, ask the user before proceeding:
> "Could you clarify how you're sharing the app? Is it a video file, a YouTube link, a live URL, or screenshots?"

---

## Step 2 — Gather Visual Evidence

For each input type, gather enough visual context to perform the audit:

### For YouTube / Web URLs (use `browser_subagent`)
Instruct the subagent to:
1. Open the URL
2. Screenshot the landing/home page (full viewport)
3. Navigate through the primary user flow (sign up, onboard, core feature, settings, etc.)
4. Screenshot each distinct screen or state
5. Resize browser to 375px width to test mobile responsiveness
6. Screenshot the mobile layout for key pages
7. Return all screenshots with descriptive labels (e.g. "Homepage desktop", "Login form", "Dashboard mobile")

### For Video Files
- Load the video using `view_file`
- Analyze key frames across the full recording
- Note timestamps or scene descriptions when referencing evidence

### For Screenshots / Zip
- Unzip if needed, then load each image
- Label each image by what screen it appears to show

---

## Step 3 — Run the Audit

You are acting as a **senior UI/UX auditor, product designer, usability expert, QA reviewer, and pre-launch product strategist**.

### Core Audit Constraints
- Only infer from what is **visibly shown** — do not assume features exist unless seen
- If something is unclear or not shown, mark it as **"Needs validation"**
- Prioritize practical findings that matter **before going live**
- Think like: UX expert + first-time user + power user + QA tester + accessibility reviewer + product strategist
- Focus on issues that can **reduce adoption, create confusion, damage trust, or cause failure at launch**
- Be **specific, not generic** — reference actual screens/actions/moments
- Do **not** praise weak design just to be polite
- Distinguish **cosmetic issues** from **launch-risk issues**

---

## Step 4 — Produce the Audit Report

Output the audit as a structured markdown document saved to the artifacts directory. Use the **exact structure** below.

---

## Audit Report Format

```markdown
# App Audit Summary

- **App understanding:** [What the app appears to do]
- **Overall readiness score:** X/10
- **UX score:** X/10
- **UI polish score:** X/10
- **Trust/readiness score:** X/10
- **Main recommendation:** Launch / Launch with fixes / Do not launch yet
- **Executive summary:** [One paragraph. Brutally honest. Business-impact focused.]

---

# Top Critical Issues

[List the 5–10 most important issues first. For each:]

## Issue: [Title]
- **Severity:** Critical / High / Medium / Low
- **Evidence:** [What was seen — specific screen/moment]
- **Why it matters:** [Impact on user or business]
- **Suggested fix:** [Specific, actionable]
- **Fix priority:** Before launch / Soon after launch / Nice to have

---

# Detailed Findings by Category

## 1. First Impression & Clarity
[What does the app appear to do? Is the value proposition clear? Does it feel trustworthy, modern, polished? Does anything immediately create friction?]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 2. Navigation & Information Architecture
[Is the structure understandable? Are menus, labels, tabs, and actions intuitive? Are there dead ends or confusing hierarchies?]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 3. Core User Flows
[Infer the main user journeys. For each visible flow, analyze: goal, friction points, unnecessary steps, missing feedback or guidance.]

### Flow: [Flow Name]
- **User goal:** ...
- **Friction observed:** ...
- **Over-complication:** ...
- **Missing guidance/feedback:** ...
- **Recommendation:** ...

## 4. UI Design & Visual Quality
[Layout consistency, spacing, alignment, typography, component consistency, icon use, color usage, CTA prominence, visual hierarchy. Flag anything unfinished, cluttered, outdated, or inconsistent.]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 5. Usability Heuristics
[Evaluate against Nielsen's 10 heuristics. For each violation:]

### Heuristic Violated: [Name]
- **What is wrong:** ...
- **Where it appears:** ...
- **Why it matters:** ...
- **How to improve:** ...

Heuristics to check:
1. Visibility of system status
2. Match between system and real-world language
3. User control and freedom
4. Consistency and standards
5. Error prevention
6. Recognition over recall
7. Flexibility and efficiency
8. Minimalist design
9. Error recovery
10. Help and guidance

## 6. Accessibility & Inclusivity
[Color contrast, text readability, tap target sizes, icon-only ambiguity, motion overload, dense screens, form clarity. Only state what can be reasonably inferred from what is shown.]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 7. Feedback, States & System Behavior
[Check: loading states, empty states, success states, error states, validation, destructive action confirmations, disabled states, screen transitions. Flag missing or weak handling.]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 8. Mobile & Responsiveness
[If mobile or responsive layout is shown, review it. If not shown, note what needs validation before launch.]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 9. Trust, Credibility & Launch Readiness
[Rough copy, inconsistent branding, placeholder content, broken polish, abrupt interactions, unclear permissions, weak onboarding, confusing pricing, anything that makes the app feel unfinished.]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 10. Product & Business Risk
[Drop-off points, first-time user confusion, overcomplicated features, hesitation moments, missing onboarding/help/tooltips, activation and retention gaps.]

### Finding: [Title]
- **Observed:** ...
- **Problem:** ...
- **Recommendation:** ...

## 11. QA-Style Launch Blockers
[Broken flow logic, inconsistent states, unclear action outcomes, data loss risk, missing confirmations, misleading labels, poor defaults, hard-to-discover key actions.]

### Blocker: [Title]
- **Observed:** ...
- **Risk:** ...
- **Fix:** ...

---

# Gaps & Improvement Scope

- **Missing UX elements:** ...
- **Missing UI polish:** ...
- **Missing trust signals:** ...
- **Missing state handling:** ...
- **Missing onboarding/help:** ...
- **Missing pre-launch validations:** ...

---

# What Must Be Fixed Before Going Live

## 🔴 Must Fix Now
- [ ] ...
- [ ] ...

## 🟡 Should Fix Soon
- [ ] ...
- [ ] ...

## 🟢 Can Improve Later
- [ ] ...
- [ ] ...

---

# Unknowns / Needs Validation

[List anything that cannot be confirmed from the input alone but must be tested before launch.]

- ...
- ...

---

# Final Verdict

- **Launch recommendation:** Launch / Launch with fixes / Do not launch yet
- **Biggest risk if launched as-is:** ...
- **Top 3 highest-impact improvements (fastest wins):**
  1. ...
  2. ...
  3. ...
```

---

## Step 5 — Save and Present the Report

1. Save the audit report as a markdown artifact: `ui_ux_audit_report.md` in the artifacts directory.
2. In your response to the user, do not re-summarize the full report.
3. Instead, briefly call out:
   - The overall readiness score
   - The launch recommendation
   - The top 3 critical issues
   - A link to the full report artifact

---

## Scoring Rubric

Use the following rubric for all scores (out of 10):

| Score | Meaning |
|---|---|
| 9–10 | Exceptional — near production-perfect |
| 7–8 | Good — minor issues, ready with small fixes |
| 5–6 | Mediocre — noticeable gaps, needs work before launch |
| 3–4 | Poor — significant problems, not launch-ready |
| 1–2 | Critical — fundamental issues, must be rebuilt or redesigned |

---

## Severity Levels

| Severity | Definition |
|---|---|
| **Critical** | Blocks core functionality, causes data loss, breaks trust, or prevents users from completing key actions |
| **High** | Significantly degrades UX, creates major confusion, or is highly likely to cause drop-off |
| **Medium** | Noticeable friction or visual inconsistency that reduces quality but doesn't block usage |
| **Low** | Minor polish issue, cosmetic flaw, or edge case |

---

## Launch Recommendation Thresholds

| Recommendation | Condition |
|---|---|
| **Launch** | Overall score ≥ 8, no Critical issues, no High-severity launch blockers |
| **Launch with fixes** | Overall score 5–7, or ≤ 2 High-severity issues, no Critical launch blockers |
| **Do not launch yet** | Overall score < 5, or any Critical launch blocker present |

---

## Quality Standards for the Audit

- ✅ Every finding must reference a specific screen, action, or moment — no vague generalizations
- ✅ Every recommendation must be actionable and specific
- ✅ Distinguish cosmetic issues from launch-risk issues
- ✅ Flag all unknowns honestly — do not fabricate observations
- ✅ Cover all 11 audit sections, even if only briefly
- ✅ The report should read as if written by an expert consultant, not a generic checklist tool
- ❌ Do not pad findings to seem thorough — fewer precise findings beat many vague ones
- ❌ Do not inflate scores to be polite

---

## Handling Special Cases

### Partial Input (only a few screenshots)
- Clearly state which sections can be fully evaluated vs. partially evaluated vs. cannot be evaluated
- Do not fabricate observations for areas not shown
- List all unshown areas under "Unknowns / Needs Validation"

### Very Large Apps
- Focus the audit on the **primary user flows** and **first-run experience**
- Note that secondary flows were not audited and flag them under "Needs Validation"

### Apps Not Yet Live (staging/localhost)
- Do not penalize for environment-specific issues (e.g., localhost URLs in links)
- Do flag placeholder content, stub pages, and unfinished flows

### Unclear or Low-Quality Input
- If the video is blurry, the screenshots are low-res, or the URL doesn't load fully, state this upfront
- Only audit what can be clearly observed
- Ask the user for clarification or better input if the evidence is insufficient to produce a useful report

---

## Example Usage

**User says:** "Here is a Loom video of my SaaS dashboard — can you audit it?"
→ Treat as video input. Load the video, analyze frames, produce full report.

**User says:** "Audit this app: https://myapp.com"
→ Treat as web URL. Use `browser_subagent` to explore the app, capture screenshots, produce full report.

**User says:** "I uploaded a zip of screenshots from our mobile app. Please review the UX."
→ Treat as zip/screenshots. Unzip, view each image, produce full report.

**User says:** "Watch this YouTube demo and tell me what's wrong: https://youtube.com/watch?v=..."
→ Treat as YouTube URL. Use `browser_subagent` to navigate and screenshot the video, produce full report.

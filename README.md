# All Agent Skills

A collection of Claude Code skills for various use cases. Install individual skills or add the entire repository.

## Available Skills

| Skill | Description |
|-------|-------------|
| [codebase-to-course](#codebase-to-course) | Transform any codebase into a beautiful, interactive single-page HTML course that teaches how the code works to non-technical people |
| [codebase-to-demo](#codebase-to-demo) | Transform any codebase or automation into a polished, interactive HTML demo deck for non-technical buyers and decision-makers |
| [excalidraw-diagram](#excalidraw-diagram) | Generate Excalidraw diagrams with JSON from natural language descriptions |
| [skill-builder](#skill-builder) | Create new skills, optimize existing skills, or audit skill quality following Claude Code best practices |

---

## Installation

### Add All Skills (Recommended)

```bash
npx skills add devenkhatri/all-agent-skills-repo
```

### Add Individual Skills

#### Codebase-to-Course

```bash
npx skills add devenkhatri/all-agent-skills-repo/codebase-to-course
```

#### Codebase-to-Demo

```bash
npx skills add devenkhatri/all-agent-skills-repo/codebase-to-demo
```

#### Excalidraw Diagram

```bash
npx skills add devenkhatri/all-agent-skills-repo/excalidraw-diagram
```

#### Skill Builder

```bash
npx skills add devenkhatri/all-agent-skills-repo/skill-builder
```

---

## Skill Details

### codebase-to-course

Transform any codebase into a stunning, interactive single-page HTML course that teaches how the code works through scroll-based modules, animated visualizations, and plain-English translations of code.

**Target Audience:** "Vibe coders" — people who build software using AI coding tools without a traditional CS education.

**Output:** A single self-contained HTML file (no dependencies except Google Fonts) that teaches code through:
- Scroll-based modules with progress tracking
- Code ↔ Plain English translations (real code on the left, explanation on the right)
- Animated visualizations (data flow, group chat between components)
- Glossary tooltips on technical terms

**Trigger Phrases:**
- "Turn this into a course"
- "Explain this codebase interactively"
- "Make a course from this project"
- "Teach me how this code works"
- "Interactive tutorial from this code"

**Files:**
```
codebase-to-course/
├── SKILL.md                    # Main skill instructions
├── README.md                   # Documentation
└── references/
    ├── design-system.md        # CSS tokens, typography, colors
    └── interactive-elements.md # Animation & visualization patterns
```

---

### codebase-to-demo

Transform any codebase or automation implementation into a compelling, interactive single-page HTML demo deck for non-technical buyers and decision-makers. The output sells the *value* through animated architecture diagrams, before/after comparisons, sequence walkthroughs, and a business-first narrative.

**Target Audience:** Non-technical buyers, business owners, executives evaluating implementations.

**Output:** A single self-contained HTML file that includes:
- Before/After Toggle (visceral comparison of manual vs automated processes)
- Clickable Architecture Map (SVG diagram with component details)
- Sequence Diagram (step-by-step animated workflow trace)
- "What Would Break If" Explorer (resilience and failure handling)
- Integration Map (hub-and-spoke layout showing connections)
- Tech Stack Justification cards with business reasons
- Deployment & Scaling Notes

**Trigger Phrases:**
- "Create a demo for this"
- "Make a pitch deck from this codebase"
- "Show this to a client"
- "Explain this implementation to a non-technical audience"
- "Demo deck"
- "Showcase this automation"
- "Create a client presentation from this project"

**Files:**
```
codebase-to-demo/
├── SKILL.md                    # Main skill instructions
├── README.md                   # Documentation
└── references/
    ├── design-system.md        # CSS tokens, typography, colors
    └── interactive-elements.md # Animation & visualization patterns
```

---

### excalidraw-diagram

Generate Excalidraw diagrams using JSON from natural language descriptions. Default for all diagram requests.

**Use Cases:**
- Architecture diagrams
- Flowcharts
- System diagrams
- Concept visualizations

**Workflow:**
1. Understand the request (ask clarifying questions if needed)
2. Research if needed for technical accuracy
3. Plan the layout mentally
4. Generate JSON elements
5. Save to `.excalidraw` file and provide JSON for copy-paste

**Files:**
```
excalidraw-diagram/
└── SKILL.md  # Main skill instructions
```

---

### skill-builder

Guide for creating new Claude Code skills, optimizing existing skills, or auditing skill quality. Follows official Claude Code best practices.

**Use Cases:**
- Building a new skill from scratch
- Optimizing or auditing an existing skill
- Deciding on advanced features (subagent execution, hooks, dynamic context)
- Troubleshooting skill issues

**Features:**
- Discovery Interview process (6 rounds of questions)
- Frontmatter configuration guide
- Build phase instructions
- Audit checklist for existing skills
- Reference documentation for advanced patterns

**Files:**
```
skill-builder/
├── SKILL.md      # Main skill instructions
├── reference.md  # Technical reference for advanced patterns
└── README.md     # Documentation
```

---

## Quick Start

1. Add skills to your project:
   ```bash
   npx skills add devenkhatri/all-agent-skills-repo
   ```

2. Use a skill by typing its name or trigger phrase:
   - `/codebase-to-course` → "Turn this codebase into a course"
   - `/codebase-to-demo` → "Create a demo for this"
   - `/excalidraw-diagram` → "Draw a diagram of..."
   - `/skill-builder` → "Help me build a skill"

---

## License

MIT
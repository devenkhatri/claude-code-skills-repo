# Interactive Elements Reference

Implementation patterns for every interactive element type used in courses. Pick the elements that best serve each module's teaching goal.

## Table of Contents
1. [Code ↔ English Translation Blocks](#code--english-translation-blocks)
3. [Drag-and-Drop Matching](#drag-and-drop-matching)
4. [Group Chat Animation](#group-chat-animation)
5. [Message Flow / Data Flow Animation](#message-flow--data-flow-animation)
6. [Interactive Architecture Diagram](#interactive-architecture-diagram)
7. [Layer Toggle Demo](#layer-toggle-demo)
8. ["Spot the Bug" Challenge](#spot-the-bug-challenge)
10. [Callout Boxes](#callout-boxes)
11. [Pattern/Feature Cards](#patternfeature-cards)
12. [Flow Diagrams](#flow-diagrams)
13. [Permission/Config Badges](#permissionconfig-badges)
14. [Glossary Tooltips](#glossary-tooltips)
15. [Visual File Tree](#visual-file-tree)
16. [Icon-Label Rows](#icon-label-rows)
17. [Numbered Step Cards](#numbered-step-cards)
18. [Before/After Toggle](#beforeafter-toggle)
19. [Clickable Architecture Map](#clickable-architecture-map)
20. [Sequence Diagram](#sequence-diagram)
21. ["What Would Break If" Explorer](#what-would-break-if-explorer)
22. [Integration Map](#integration-map)
23. [Tech Stack Justification](#tech-stack-justification)
24. [Deployment & Scaling Notes](#deployment--scaling-notes)

---

## Numbered Step Cards

For sequences that would otherwise be a numbered paragraph list. Visual, scannable, and each step stands alone.

```html
<div class="step-cards">
  <div class="step-card">
    <div class="step-num">1</div>
    <div class="step-body">
      <strong>User pastes a YouTube URL</strong>
      <p>The frontend captures the URL and extracts the video ID</p>
    </div>
  </div>
  <div class="step-card">
    <div class="step-num">2</div>
    <div class="step-body">
      <strong>API fetches the transcript</strong>
      <p>A server-side route calls an external service to get the video's text</p>
    </div>
  </div>
  <div class="step-card">
    <div class="step-num">3</div>
    <div class="step-body">
      <strong>AI analyzes the content</strong>
      <p>The transcript is sent to an AI model that extracts key moments</p>
    </div>
  </div>
</div>
```

```css
.step-cards { display: flex; flex-direction: column; gap: var(--space-3); }
.step-card {
  display: flex; align-items: flex-start; gap: var(--space-4);
  padding: var(--space-4) var(--space-5);
  background: var(--color-surface);
  border-radius: var(--radius-md);
  border-left: 3px solid var(--color-accent);
  box-shadow: var(--shadow-sm);
}
.step-num {
  width: 32px; height: 32px; border-radius: 50%;
  background: var(--color-accent);
  color: white; font-weight: 700;
  display: flex; align-items: center; justify-content: center;
  font-family: var(--font-display);
  flex-shrink: 0;
}
.step-body p { margin: var(--space-1) 0 0; color: var(--color-text-secondary); font-size: var(--text-sm); }

---

## Before/After Toggle

Make the "old way" visceral so the buyer feels the pain before seeing the solution.

**HTML:**
```html
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

**CSS:**
```css
.before-after-toggle { position: relative; margin: var(--space-8) 0; }
.toggle-controls {
  display: flex; justify-content: center; gap: var(--space-2);
  margin-bottom: var(--space-6);
}
.toggle-btn {
  padding: var(--space-3) var(--space-6);
  border: 2px solid var(--color-border);
  background: transparent;
  border-radius: var(--radius-md);
  cursor: pointer; font-weight: 600;
  transition: all var(--duration-normal) var(--ease-out);
}
.toggle-btn.active {
  background: var(--color-accent);
  border-color: var(--color-accent);
  color: white;
}
.panel {
  display: none;
  animation: fadeIn 0.4s var(--ease-out);
}
.panel.active { display: block; }
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(8px); }
  to { opacity: 1; transform: translateY(0); }
}
```

**JS:**
```javascript
document.querySelectorAll('.toggle-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.toggle-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    const panel = btn.dataset.panel;
    document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
    document.querySelector(`.${panel}-panel`).classList.add('active');
  });
});
```

**Rules:**
- LEFT panel: "Before" — the old manual process shown as a timeline of human steps (with time estimates, error risks, and handoff delays called out as red badges)
- RIGHT panel: "After" — the automated process, same timeline but most steps replaced with green "automated" badges, human steps reduced to review/approve only
- Below the toggle: a single stat callout — "From 4 hours to 8 minutes" or "From 60% error rate to <1%"

---

## Clickable Architecture Map

Give buyers a mental model of the system without overwhelming them. They click what they're curious about.

**HTML:**
```html
<div class="arch-map">
  <svg class="arch-svg" viewBox="0 0 800 500">
    <!-- Connecting lines -->
    <path class="arch-line" d="M200,250 L400,150" />
    <path class="arch-line" d="M400,150 L600,250" />
    <!-- Component nodes -->
    <g class="arch-node" data-name="lead-capture" data-desc="Captures leads from web forms">
      <rect x="100" y="200" width="120" height="80" rx="8" />
      <text x="160" y="245" text-anchor="middle">Lead Capture</text>
    </g>
    <g class="arch-node" data-name="ai-processor" data-desc="Analyzes and classifies incoming data">
      <rect x="340" y="100" width="120" height="80" rx="8" />
      <text x="400" y="145" text-anchor="middle">AI Processor</text>
    </g>
    <g class="arch-node" data-name="crm" data-desc="Stores and manages customer records">
      <rect x="540" y="200" width="120" height="80" rx="8" />
      <text x="600" y="245" text-anchor="middle">CRM</text>
    </g>
  </svg>
  <div class="arch-detail" id="arch-detail">
    <h4>Click any component to learn what it does</h4>
  </div>
</div>
```

**JS:**
```javascript
const nodeData = {
  'lead-capture': {
    businessName: 'Lead Capture',
    oneLineSummary: 'Captures leads from web forms',
    input: 'Form submission (name, email, message)',
    output: 'Structured lead data to AI Processor'
  },
  'ai-processor': {
    businessName: 'AI Processor',
    oneLineSummary: 'Analyzes and classifies incoming data',
    input: 'Raw lead data',
    output: 'Classified lead with intent score'
  },
  'crm': {
    businessName: 'CRM',
    oneLineSummary: 'Stores and manages customer records',
    input: 'Classified lead data',
    output: 'Confirmed record in database'
  }
};

document.querySelectorAll('.arch-node').forEach(node => {
  node.addEventListener('click', () => {
    document.querySelectorAll('.arch-node').forEach(n => n.classList.remove('active'));
    node.classList.add('active');
    
    const data = nodeData[node.dataset.name];
    const detailPanel = document.getElementById('arch-detail');
    detailPanel.innerHTML = `
      <h3>${data.businessName}</h3>
      <p>${data.oneLineSummary}</p>
      <div class="io-row">
        <span class="input-badge">IN: ${data.input}</span>
        <span class="output-badge">OUT: ${data.output}</span>
      </div>
    `;
    detailPanel.classList.add('visible');
  });
});
```

**CSS:**
```css
.arch-map { position: relative; margin: var(--space-8) 0; }
.arch-node { cursor: pointer; transition: all var(--duration-normal) var(--ease-out); }
.arch-node rect { fill: var(--color-surface); stroke: var(--color-border); stroke-width: 2; }
.arch-node:hover rect { stroke: var(--color-accent); }
.arch-node.active rect { stroke: var(--color-accent); stroke-width: 3; filter: drop-shadow(0 0 10px rgba(217, 79, 48, 0.3)); }
.arch-line { stroke: var(--color-border-light); stroke-width: 2; stroke-dasharray: 8 4; animation: flowDash 1s linear infinite; }
@keyframes flowDash { to { stroke-dashoffset: -12; } }
.arch-detail {
  position: absolute; bottom: 0; left: 0; right: 0;
  background: var(--color-bg-code); color: #CDD6F4;
  padding: var(--space-4); border-radius: var(--radius-md);
  opacity: 0; transform: translateY(10px);
  transition: all var(--duration-normal) var(--ease-out);
}
.arch-detail.visible { opacity: 1; transform: translateY(0); }
```

**Rules:**
- Use buyer-language, not technical names: "Lead Capture" not "Webhook endpoint", "AI Processor" not "LLM call"
- Connecting lines animate with flowing dot effect (SVG `stroke-dashoffset` animation)
- Active node gets a highlight ring; inactive nodes dim slightly

---

## Sequence Diagram

Walk the buyer through exactly what happens when a real event occurs — like a behind-the-scenes tour of one transaction.

**HTML:**
```html
<div class="sequence-diagram">
  <div class="seq-progress-bar">
    <div class="seq-progress-fill" id="seq-progress"></div>
  </div>
  <div class="seq-steps" id="seq-steps">
    <div class="seq-step" data-step="1">
      <div class="step-marker">1</div>
      <div class="step-body">
        <div class="step-component-badge" style="background: var(--color-actor-1)">Lead Capture</div>
        <p class="step-description">A visitor fills out your contact form — name, email, and message.</p>
        <span class="step-time">+0s</span>
      </div>
    </div>
    <div class="seq-step" data-step="2">
      <div class="step-marker">2</div>
      <div class="step-body">
        <div class="step-component-badge" style="background: var(--color-actor-2)">API Route</div>
        <p class="step-description">The form data is sent to your server — taking about 200ms.</p>
        <span class="step-time">+0.2s</span>
      </div>
    </div>
    <div class="seq-step" data-step="3">
      <div class="step-marker">3</div>
      <div class="step-body">
        <div class="step-component-badge" style="background: var(--color-actor-3)">AI Processor</div>
        <p class="step-description">The lead's message is analyzed to detect intent, urgency, and industry.</p>
        <span class="step-time">+1.5s</span>
        <details class="step-detail">
          <summary>Behind the scenes</summary>
          <p>OpenAI's GPT-4o reads the message and returns a structured JSON object with intent score, urgency level, and suggested response category.</p>
        </details>
      </div>
    </div>
  </div>
  <div class="seq-controls">
    <button onclick="seqNext()">Next Step</button>
    <button onclick="seqPlayAll()">Play All</button>
    <button onclick="seqReset()">Replay</button>
    <span class="seq-progress-text" id="seq-progress-text">Step 0 / 3</span>
  </div>
</div>
```

**JS:**
```javascript
const seqSteps = document.querySelectorAll('.seq-step');
let seqIndex = 0;

window.seqNext = function() {
  if (seqIndex >= seqSteps.length) return;
  const step = seqSteps[seqIndex];
  step.style.display = 'flex';
  step.style.animation = 'fadeSlideUp 0.3s var(--ease-out)';
  seqIndex++;
  updateSeqProgress();
};

window.seqPlayAll = function() {
  const interval = setInterval(() => {
    if (seqIndex >= seqSteps.length) { clearInterval(interval); return; }
    seqNext();
  }, 1500);
};

window.seqReset = function() {
  seqIndex = 0;
  seqSteps.forEach(s => s.style.display = 'none');
  updateSeqProgress();
};

function updateSeqProgress() {
  const progress = (seqIndex / seqSteps.length) * 100;
  document.getElementById('seq-progress').style.width = progress + '%';
  document.getElementById('seq-progress-text').textContent = `Step ${seqIndex} / ${seqSteps.length}`;
}
```

**CSS:**
```css
.sequence-diagram { margin: var(--space-8) 0; }
.seq-progress-bar { height: 4px; background: var(--color-border-light); border-radius: 2px; margin-bottom: var(--space-4); }
.seq-progress-fill { height: 100%; background: var(--color-accent); border-radius: 2px; width: 0%; transition: width 0.4s var(--ease-out); }
.seq-step {
  display: none; align-items: flex-start; gap: var(--space-4);
  padding: var(--space-4); margin-bottom: var(--space-3);
  background: var(--color-surface); border-radius: var(--radius-md);
  border-left: 3px solid var(--color-accent);
}
.seq-step[data-step="1"] { border-left-color: var(--color-actor-1); }
.seq-step[data-step="2"] { border-left-color: var(--color-actor-2); }
.seq-step[data-step="3"] { border-left-color: var(--color-actor-3); }
.step-marker {
  width: 28px; height: 28px; border-radius: 50%;
  background: var(--color-accent); color: white;
  display: flex; align-items: center; justify-content: center;
  font-weight: 700; flex-shrink: 0;
}
.step-component-badge {
  display: inline-block; padding: var(--space-1) var(--space-3);
  border-radius: var(--radius-sm); color: white;
  font-size: var(--text-xs); font-weight: 600; margin-bottom: var(--space-2);
}
.step-time { font-family: var(--font-mono); font-size: var(--text-xs); color: var(--color-text-muted); margin-left: var(--space-2); }
.step-detail { margin-top: var(--space-2); font-size: var(--text-sm); }
.step-detail summary { cursor: pointer; color: var(--color-accent); }
.step-detail p { margin-top: var(--space-2); color: var(--color-text-secondary); }

@keyframes fadeSlideUp {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
```

**Rules:**
- Pick the most important single workflow from the codebase
- Show 5-10 steps, each with: step number, plain-language description, component involved, and time elapsed
- Steps animate in one at a time, driven by "Next Step" button or auto-advance
- Each step can optionally expand to show "behind the scenes" detail

---

## "What Would Break If" Explorer

Proactively address the buyer's fear of fragility. Show that the system handles failure gracefully.

**HTML:**
```html
<div class="resilience-explorer">
  <div class="resilience-map" id="resilience-map">
    <!-- Simplified architecture nodes -->
  </div>
  <div class="scenario-buttons">
    <button class="scenario-btn" data-scenario="ai-down">What if the AI API goes down?</button>
    <button class="scenario-btn" data-scenario="webhook-dup">What if a webhook fires twice?</button>
    <button class="scenario-btn" data-scenario="db-full">What if the database is full?</button>
  </div>
  <div class="scenario-detail" id="scenario-detail"></div>
  <button class="recovery-btn" onclick="resetResilience()">Recovery</button>
</div>
```

**JS:**
```javascript
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
  {
    label: "What if a webhook fires twice?",
    affectedNodes: ['lead-capture'],
    severity: 'green',
    failureMode: "Duplicate entries could be created.",
    systemResponse: "The system checks for existing records by unique identifier before creating new ones.",
    buyerExperience: "No action needed — duplicates are prevented automatically.",
    recoveryTime: "N/A — handled automatically"
  },
  {
    label: "What if the database is full?",
    affectedNodes: ['crm'],
    severity: 'red',
    failureMode: "New leads can't be saved.",
    systemResponse: "System stops accepting new submissions and alerts you immediately.",
    buyerExperience: "You'd receive an urgent Slack alert. Old records can be archived to free space.",
    recoveryTime: "Immediate after space is freed"
  }
];

document.querySelectorAll('.scenario-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    const scenario = scenarios.find(s => s.label === btn.textContent);
    showScenario(scenario);
  });
});

function showScenario(scenario) {
  const detail = document.getElementById('scenario-detail');
  detail.innerHTML = `
    <div class="scenario-failure">
      <strong>Failure Mode:</strong> ${scenario.failureMode}
    </div>
    <div class="scenario-response">
      <strong>System Response:</strong> ${scenario.systemResponse}
    </div>
    <div class="scenario-buyer">
      <strong>What You'd See:</strong> ${scenario.buyerExperience}
    </div>
    <div class="scenario-recovery">
      <strong>Recovery Time:</strong> ${scenario.recoveryTime}
    </div>
  `;
  detail.className = `scenario-detail visible severity-${scenario.severity}`;
}
```

**CSS:**
```css
.resilience-explorer { margin: var(--space-8) 0; }
.scenario-buttons { display: flex; flex-wrap: wrap; gap: var(--space-3); margin: var(--space-4) 0; }
.scenario-btn {
  padding: var(--space-3) var(--space-4); border: 2px solid var(--color-border);
  background: var(--color-surface); border-radius: var(--radius-md);
  cursor: pointer; transition: all var(--duration-normal) var(--ease-out);
}
.scenario-btn:hover { border-color: var(--color-accent); }
.scenario-detail {
  padding: var(--space-4); border-radius: var(--radius-md);
  background: var(--color-bg-code); color: #CDD6F4;
  opacity: 0; transform: translateY(10px);
  transition: all var(--duration-normal) var(--ease-out);
}
.scenario-detail.visible { opacity: 1; transform: translateY(0); }
.scenario-detail.severity-amber { border-left: 4px solid #f59e0b; }
.scenario-detail.severity-green { border-left: 4px solid #10b981; }
.scenario-detail.severity-red { border-left: 4px solid #ef4444; }
.scenario-failure, .scenario-response, .scenario-buyer, .scenario-recovery { margin-bottom: var(--space-2); }
.recovery-btn {
  margin-top: var(--space-4); padding: var(--space-2) var(--space-4);
  background: var(--color-accent); color: white;
  border: none; border-radius: var(--radius-sm); cursor: pointer;
}
```

---

## Integration Map

Show the buyer what the system connects to — making it feel substantial and well-integrated.

**HTML:**
```html
<div class="integration-map">
  <div class="int-hub">
    <div class="int-hub-icon">⚙️</div>
    <span>Core System</span>
  </div>
  <div class="int-spokes">
    <div class="int-spoke" data-platform="crm">
      <div class="int-spoke-icon">💼</div>
      <span>CRM</span>
    </div>
    <div class="int-spoke" data-platform="slack">
      <div class="int-spoke-icon">💬</div>
      <span>Slack</span>
    </div>
    <div class="int-spoke" data-platform="email">
      <div class="int-spoke-icon">📧</div>
      <span>Email</span>
    </div>
    <div class="int-spoke" data-platform="openai">
      <div class="int-spoke-icon">🤖</div>
      <span>OpenAI</span>
    </div>
  </div>
  <div class="int-legend">
    <span class="legend-item"><span class="legend-dot crm"></span> CRM</span>
    <span class="legend-item"><span class="legend-dot comm"></span> Communication</span>
    <span class="legend-item"><span class="legend-dot ai"></span> AI/Processing</span>
  </div>
</div>
```

**CSS:**
```css
.integration-map { position: relative; margin: var(--space-8) 0; text-align: center; }
.int-hub {
  display: inline-block; padding: var(--space-4) var(--space-6);
  background: var(--color-accent); color: white;
  border-radius: var(--radius-md); margin-bottom: var(--space-6);
}
.int-spokes { display: flex; justify-content: center; gap: var(--space-6); flex-wrap: wrap; }
.int-spoke {
  display: flex; flex-direction: column; align-items: center;
  padding: var(--space-4); background: var(--color-surface);
  border-radius: var(--radius-md); border: 2px solid var(--color-border);
  cursor: pointer; transition: all var(--duration-normal) var(--ease-out);
  min-width: 100px;
}
.int-spoke:hover { border-color: var(--color-accent); transform: translateY(-4px); }
.int-spoke-icon { font-size: 2rem; margin-bottom: var(--space-2); }
.int-legend { margin-top: var(--space-6); display: flex; justify-content: center; gap: var(--space-4); }
.legend-dot { width: 12px; height: 12px; border-radius: 50%; display: inline-block; margin-right: var(--space-1); }
.legend-dot.crm { background: #3b82f6; }
.legend-dot.comm { background: #10b981; }
.legend-dot.ai { background: #8b5cf6; }
```

---

## Tech Stack Justification

Answer "why not just use [simpler/cheaper/alternative]?" before the buyer asks it.

**HTML:**
```html
<div class="tech-stack">
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
  <div class="stack-card">
    <div class="stack-header">
      <span class="stack-logo">🤖</span>
      <h3>OpenAI</h3>
      <span class="stack-role">AI Processing</span>
    </div>
    <p class="stack-reason">Industry-leading language model with proven reliability. Handles complex classification and extraction with 95%+ accuracy.</p>
    <div class="stack-vs">
      <span class="vs-label">vs. Rule-based:</span>
      <span class="vs-reason">No need to manually write rules — the model learns from your data and improves over time.</span>
    </div>
  </div>
</div>
```

**CSS:**
```css
.tech-stack { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: var(--space-6); margin: var(--space-8) 0; }
.stack-card {
  background: var(--color-surface); border-radius: var(--radius-md);
  padding: var(--space-6); border-top: 3px solid var(--color-accent);
}
.stack-header { display: flex; align-items: center; gap: var(--space-3); margin-bottom: var(--space-4); }
.stack-logo { font-size: 1.5rem; }
.stack-role { font-size: var(--text-xs); color: var(--color-text-muted); text-transform: uppercase; letter-spacing: 0.05em; }
.stack-reason { color: var(--color-text-secondary); line-height: 1.6; margin-bottom: var(--space-4); }
.stack-vs { font-size: var(--text-sm); padding: var(--space-3); background: var(--color-bg-code); border-radius: var(--radius-sm); }
.vs-label { font-weight: 600; color: var(--color-accent); }
.vs-reason { color: #CDD6F4; }
```

---

## Deployment & Scaling Notes

Address the "what happens after we go live?" fear.

**HTML:**
```html
<div class="deployment-notes">
  <div class="deploy-columns">
    <div class="deploy-column">
      <h4>Day 1</h4>
      <div class="deploy-item">
        <strong>Infrastructure</strong>
        <span>Self-hosted on Railway</span>
      </div>
      <div class="deploy-item">
        <strong>Expected Volume</strong>
        <span>~50 leads/day</span>
      </div>
      <div class="deploy-item">
        <strong>Monthly Cost</strong>
        <span>$25/month</span>
      </div>
      <div class="deploy-item">
        <strong>Maintenance</strong>
        <span>1 hour/month</span>
      </div>
    </div>
    <div class="deploy-column">
      <h4>After 6 Months</h4>
      <div class="deploy-item">
        <strong>Infrastructure</strong>
        <span>Same + monitoring</span>
      </div>
      <div class="deploy-item">
        <strong>Expected Volume</strong>
        <span>~500 leads/day</span>
      </div>
      <div class="deploy-item">
        <strong>Monthly Cost</strong>
        <span>$50/month</span>
      </div>
      <div class="deploy-item">
        <strong>Maintenance</strong>
        <span>2 hours/month</span>
      </div>
    </div>
    <div class="deploy-column">
      <h4>At Scale</h4>
      <div class="deploy-item">
        <strong>Infrastructure</strong>
        <span>Dedicated server</span>
      </div>
      <div class="deploy-item">
        <strong>Expected Volume</strong>
        <span>5,000+ leads/day</span>
      </div>
      <div class="deploy-item">
        <strong>Monthly Cost</strong>
        <span>$200/month</span>
      </div>
      <div class="deploy-item">
        <strong>Maintenance</strong>
        <span>4 hours/month</span>
      </div>
    </div>
  </div>
  <div class="deploy-contact">
    <h4>Who to Call</h4>
    <div class="contact-item">
      <span class="contact-label">Automation issues:</span>
      <span>Your development team</span>
    </div>
    <div class="contact-item">
      <span class="contact-label">Infrastructure:</span>
      <span>Railway support</span>
    </div>
  </div>
</div>
```

**CSS:**
```css
.deployment-notes { margin: var(--space-8) 0; }
.deploy-columns { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--space-6); }
.deploy-column { background: var(--color-surface); padding: var(--space-6); border-radius: var(--radius-md); }
.deploy-column h4 { color: var(--color-accent); margin-bottom: var(--space-4); }
.deploy-item { margin-bottom: var(--space-3); display: flex; flex-direction: column; }
.deploy-item strong { font-size: var(--text-xs); color: var(--color-text-muted); text-transform: uppercase; letter-spacing: 0.05em; }
.deploy-item span { font-size: var(--text-sm); }
.deploy-contact { margin-top: var(--space-6); padding: var(--space-4); background: var(--color-bg-code); border-radius: var(--radius-md); }
.contact-item { display: flex; gap: var(--space-3); margin-top: var(--space-2); }
.contact-label { font-weight: 600; color: var(--color-accent); }

@media (max-width: 768px) {
  .deploy-columns { grid-template-columns: 1fr; }
}```

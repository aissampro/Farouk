# Farouk

**The AI CEO that builds and runs your startup.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude%20Sonnet-purple)](https://anthropic.com)
[![Languages](https://img.shields.io/badge/Languages-EN%20%7C%20FR-blue)](./README.fr.md)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Stars](https://img.shields.io/github/stars/YOUR_USERNAME/farouk?style=social)](https://github.com/YOUR_USERNAME/farouk)

---

You have an idea.

Farouk turns it into a strategy, assembles an AI team, assigns tasks, and delivers real outputs — in minutes.

No consultants. No co-founders. No waiting.

---

## Demo

> **[▶ Watch the full demo](./demo/demo.md)**

![Farouk in action](./demo/assets/demo.gif)
*(GIF coming soon — see [demo/demo.md](./demo/demo.md) for the full walkthrough)*

---

## Try it in 30 seconds

```bash
git clone https://github.com/YOUR_USERNAME/farouk.git
cd farouk
open src/index.html
```

No install. No npm. No Docker. Just open the file.

> You'll need a free [Anthropic API key](https://console.anthropic.com) to power Farouk's brain.

---

## What is Farouk?

Farouk is an **AI CEO operating system**.

You give it a business idea. It does the rest:

| Phase | What Farouk does |
|---|---|
| **1. Strategy** | Analyzes the market, defines positioning, models the business |
| **2. CEO Planning** | Builds a 90-day roadmap, assigns roles, sets KPIs |
| **3. Team Assembly** | Recruits AI agents: Marketing, Engineering, Sales, Ops |
| **4. Execution** | Agents run in parallel, each completing their assigned tasks |
| **5. Deliverables** | Business plan, GTM strategy, product roadmap, action items |

Everything streams live. Every output is real.

---

## Example Output

**Input:** `"Launch a coaching business for young professionals"`

**Output (generated in ~90 seconds):**

```
MARKET OPPORTUNITY
The coaching market is valued at $20B globally, growing at 6.7% annually.
Young professionals aged 25-35 are underserved — they need structured guidance
but can't afford traditional coaching rates ($300-500/hr).

POSITIONING
Farouk recommends: "AI-assisted human coaching at a fraction of the cost."
Target price point: $79/month. Primary channel: LinkedIn organic + community.

TEAM
→ Léa   (Marketing Agent)    — brand strategy, content calendar, launch campaign
→ Hakim (Engineering Agent)  — landing page, booking system, client portal MVP
→ Sarah (Sales Agent)        — ICP definition, outreach scripts, first 10 clients
→ Omar  (Ops Agent)          — onboarding flow, session templates, KPI dashboard

TASKS ASSIGNED (8 tasks, auto-prioritized)
✅ [LÉA]   Define brand voice and visual identity
✅ [HAKIM] Build landing page with waitlist form
✅ [SARAH] Write 3 cold outreach sequences for LinkedIn
✅ [OMAR]  Create client onboarding checklist

WEEK 1 ACTION ITEMS
1. Register domain and set up brand kit
2. Launch LinkedIn presence — 3 posts/week starting now
3. Reach out to 50 potential clients using Sarah's templates
4. Publish landing page — target: 200 waitlist signups in 14 days
5. Book 5 discovery calls this week using Omar's session framework
```

→ See full examples in [/examples](./examples/)

---

## How it works

```
Your idea
    │
    ▼
┌─────────────────────────────┐
│   FAROUK (CEO + Consultant) │
│   Strategy · Roadmap · Team │
└──────────────┬──────────────┘
               │
    ┌──────────┴──────────┐
    │                     │
    ▼                     ▼
┌────────┐          ┌──────────────┐
│ AGENTS │          │ TASK ENGINE  │
│ Léa    │          │ Auto-assign  │
│ Hakim  │          │ Prioritize   │
│ Sarah  │          │ Track        │
│ Omar   │          └──────────────┘
└────────┘
    │
    ▼
┌─────────────────────────────┐
│         DELIVERABLES        │
│ Plan · GTM · Roadmap · Deck │
└─────────────────────────────┘
```

Farouk calls Claude under the hood. Each agent has its own system prompt, personality, and area of responsibility. They run in parallel. Their outputs are merged into a consolidated report.

Full architecture: [docs/architecture.md](./docs/architecture.md)

---

## Why this matters

Most startups fail before they start.

Not because the idea is bad.
Because the founder is alone — no strategy, no team, no execution system.

Farouk changes that.

It's not a chatbot. It's not a template generator.
It's the founding team you never had — available instantly, working in parallel, producing real outputs.

**We believe everyone with a good idea deserves a world-class team.**
Farouk is how we make that true.

---

## Bilingual — EN / FR

Farouk speaks English and French natively.

Switch languages with one click. The UI, the agents, the prompts, and all outputs adapt automatically.

---

## Stack

- **AI:** Claude Sonnet (Anthropic) — strategy, agents, streaming
- **Frontend:** Vanilla HTML/CSS/JS — zero dependencies, single file
- **Architecture:** Multi-agent orchestration with parallel execution
- **License:** MIT — fork it, build on it, ship it

---

## Roadmap

| Version | Feature |
|---|---|
| v1.0 ✅ | Core OS — strategy, CEO, 4 agents, bilingual EN/FR |
| v1.1 | Export to PDF / Word |
| v1.2 | Session save & restore |
| v1.3 | Web search for real market data |
| v1.4 | Custom agent personas |
| v2.0 | Multi-user collaboration |
| v3.0 | Autonomous execution (real actions) |

Full roadmap: [docs/roadmap.md](./docs/roadmap.md)

---

## Contributing

Farouk is open-source and community-driven.

The best contributions:
- Add a new language (ES, DE, PT, AR...)
- Improve agent prompts in [/prompts](./prompts/)
- Add new example outputs in [/examples](./examples/)
- Build the UI improvements from the roadmap

See [CONTRIBUTING.md](./CONTRIBUTING.md) to get started.

---

## Examples

| Input | Output |
|---|---|
| [Coaching business](./examples/coaching-business.md) | Full strategy, team, tasks, landing page |
| [SaaS startup](./examples/saas-startup.md) | Full strategy, team, tasks, product roadmap |

---

## License

MIT — free forever. Build on it. Ship it. Make it yours.

---

<br/>

> *"I gave Farouk my idea on a Tuesday. By Wednesday I had a go-to-market strategy, a landing page copy, and a list of 50 leads to contact."*

<br/>

**Give Farouk a ⭐ if it gave you a team.**

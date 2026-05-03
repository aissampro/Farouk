# Farouk — Architecture

## Overview

Farouk is a **multi-agent AI orchestration system** that simulates a complete startup founding team.

It is built as a single HTML file with no dependencies, calling the Anthropic Claude API directly from the browser.

---

## The 5-Phase Pipeline

```
INPUT (business idea)
       │
       ▼
┌──────────────────────────────────────────────────────┐
│  PHASE 1: STRATEGIC ANALYSIS                         │
│                                                      │
│  Model: claude-sonnet-4-20250514                     │
│  Prompt: prompts/ceo.txt (consulting mode)           │
│  Output: Market, users, positioning, model, risks    │
│  Streaming: yes                                      │
└──────────────────────────┬───────────────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────────────┐
│  PHASE 2: CEO EXECUTION PLAN                         │
│                                                      │
│  Input: Phase 1 output + original idea               │
│  Prompt: prompts/ceo.txt (CEO mode)                  │
│  Output: 90-day roadmap, agent assignments, KPIs     │
│  Streaming: yes                                      │
└──────────────────────────┬───────────────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────────────┐
│  PHASE 3: TASK GENERATION                            │
│                                                      │
│  Input: CEO plan                                     │
│  Output: JSON array of 8 tasks with agent/priority   │
│  Streaming: no (JSON parse required)                 │
└──────────────────────────┬───────────────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────────────┐
│  PHASE 4: PARALLEL AGENT EXECUTION                   │
│                                                      │
│  4 calls fired simultaneously via Promise.all()      │
│                                                      │
│  Léa   → prompts/marketing.txt  → marketing output   │
│  Hakim → prompts/engineering.txt → tech output       │
│  Sarah → prompts/sales.txt      → sales output       │
│  Omar  → prompts/ops.txt        → ops output         │
│                                                      │
│  Each agent: receives idea + CEO plan + their tasks  │
│  Streaming: no (parallel JSON responses)             │
└──────────────────────────┬───────────────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────────────┐
│  PHASE 5: CONSOLIDATED REPORT                        │
│                                                      │
│  Input: strategy + CEO plan (summaries)              │
│  Output: Exec summary, GTM, roadmap, revenue, actions│
│  Streaming: yes                                      │
└──────────────────────────────────────────────────────┘
```

---

## Concurrency Model

Phases 1, 2, and 5 stream sequentially (each depends on the previous).

Phase 4 (agent execution) runs all 4 agents in parallel using `Promise.all()`:

```javascript
await Promise.all([
  runAgent('mkt', 'marketing'),
  runAgent('eng', 'engineering'),
  runAgent('sls', 'sales'),
  runAgent('ops', 'ops')
]);
```

This reduces total execution time by ~3× compared to sequential execution.

---

## Language System

All prompts are stored in the `T` translation object with `en` and `fr` keys.

When a language is selected:
1. The UI re-renders all `data-en` / `data-fr` attributes
2. All Claude prompts switch to the selected language
3. The system prompt instructs agents to respond in that language
4. Outputs are guaranteed to be monolingual

Adding a new language requires:
- Adding a new key to the `T` object
- Translating all prompt templates (including Claude system prompts)
- Adding the language button to the HTML switcher

---

## API Usage

Each Farouk run makes approximately **6-7 API calls**:

| Phase | Calls | Streaming |
|---|---|---|
| Strategy analysis | 1 | Yes |
| CEO plan | 1 | Yes |
| Task generation | 1 | No |
| Agent execution (×4) | 4 | No |
| Consolidated report | 1 | Yes |
| **Total** | **8** | — |

Estimated cost per run: ~$0.03-0.08 USD (varies with idea complexity and output length).

---

## File Structure

```
farouk/
├── src/
│   └── index.html        ← The entire application
├── prompts/
│   ├── ceo.txt           ← CEO + consultant system prompt
│   ├── marketing.txt     ← Léa's system prompt
│   ├── engineering.txt   ← Hakim's system prompt
│   ├── sales.txt         ← Sarah's system prompt
│   └── ops.txt           ← Omar's system prompt
├── examples/
│   ├── coaching-business.md
│   └── saas-startup.md
├── demo/
│   └── demo.md
├── docs/
│   ├── architecture.md   ← this file
│   ├── roadmap.md
│   └── LAUNCH_GUIDE.md
├── .github/
│   ├── workflows/ci.yml
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── README.md
├── README.fr.md
├── CONTRIBUTING.md
├── CHANGELOG.md
└── LICENSE
```

---

## Design Principles

**1. Zero dependencies**
The entire app runs by opening a single HTML file in a browser. No npm, no bundler, no Docker.

**2. Single source of truth**
All logic, UI, and prompts live in `src/index.html`. Easy to fork, easy to modify.

**3. Language as a first-class concern**
Every string in the UI and every Claude prompt has an `en` and `fr` version. Adding a language is a structured task, not a find-and-replace.

**4. Streaming as the default**
All user-facing AI outputs stream token by token. The system should feel alive.

**5. Parallel execution**
Agents run simultaneously. The system should feel like a team, not a queue.

**6. Modularity through prompts**
Each agent's behavior is controlled entirely by its system prompt in `/prompts/`. Improving an agent's output means improving its prompt file — no code changes required.

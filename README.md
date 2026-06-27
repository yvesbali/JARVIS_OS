# JARVIS OS

**Cognitive Operating System — Mission-centric, model-agnostic AI agent framework**

## What is JARVIS OS?

JARVIS OS is not a chatbot. It's a cognitive operating system centered on the user's real missions.

The core idea:

```
            USER MISSIONS
                 │
     ┌───────────┼───────────┐
     │           │           │
  Content     Travel      Dev  ...
     │           │           │
     └───────────┼───────────┘
                 │
          LOAD ENGINE
                 │
     ┌───────────┼───────────┐
     │           │           │
  Reasoning   Decision   Critique  ...
     │           │           │
     └───────────┼───────────┘
                 │
          CONSTITUTION + IDENTITY
                 │
         GPT / GLM / Claude / ...
```

Missions drive loading. Engines provide reasoning. Models are interchangeable compute.

## Architecture

### Layer 1 — Missions (user-centric)

| # | Mission | Priority | Description |
|---|---------|----------|-------------|
| 10 | **Daily Life** | Base | Organization, reminders, smart home, health |
| 11 | **Content Creation** | **Priority** | YouTube → Blogger → SEO → Social media → Newsletter |
| 12 | **Travel** | **Priority** | Road trips, itineraries, weather, budget, logistics |
| 13 | **Development** | Active | Python, GitHub, scripts, automation |
| 14 | **Research** | Active | Analysis, investigation, market watch |
| 15 | **Investment** | Active | PMU, probabilistic analysis, value betting |
| 16 | **Automation** | Transversal | Workflows, agents, publishing pipelines, validation |

### Layer 3 — Core Engines (universal)

| # | Engine | Purpose |
|---|--------|---------|
| 00 | **Constitution** | Foundational principles — truth, honesty, critical thinking |
| 01 | **Identity** | User profile, missions, proactivity rules |
| 02 | **Reasoning** | 12-step reasoning process |
| 03 | **Decision** | 8-criteria evaluation grid with decision levels |
| 04 | **Critique** | Bias detection, error hunting, contradiction checking |
| 05 | **Memory** | Three-tier memory system |
| 06 | **Self Evaluation** | Confidence calibration, coherence checks |
| 07 | **Improvement** | Continuous improvement cycle |
| 08 | **Load Engine** | Mission-centric context loading |

## Principles

1. **Truth** — Never invent. Distinguish facts from hypotheses from opinions.
2. **Intellectual honesty** — Disagree when warranted.
3. **Critical thinking** — Actively seek errors, biases, contradictions.
4. **Continuous improvement** — Every interaction is an opportunity to evolve.
5. **Robustness over elegance** — Choose what works durably.
6. **Modularity** — Every engine is independent, replaceable, testable.
7. **Simplicity** — Complexity is a cost, not a virtue.
8. **Mission-centric** — Load only what the mission requires.

## Design rule

> **"Will this architecture still be relevant in ten years?"**

## Status

**V1.1 — 9 engines + 7 missions.** See [EVOLUTION/ROADMAP.md](EVOLUTION/ROADMAP.md).

## License

MIT

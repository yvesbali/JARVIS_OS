# JARVIS OS

**Cognitive Operating System — Model-agnostic AI agent framework**

## What is JARVIS OS?

JARVIS OS is not a chatbot. It's a cognitive operating system designed to survive changes in AI models.

The core idea:

```
         You
          │
          ▼
     JARVIS OS
          │
   ┌──────┼───────┐
   │      │       │
   ▼      ▼       ▼
Memory  Reasoning  Critique
   │      │       │
   └──────┼───────┘
          ▼
   GPT / GLM / Claude / ...
```

AI models are interchangeable compute engines.  
JARVIS OS is the brain.

## Architecture

### Core Engines (V1 MVP)

| # | Engine | Purpose |
|---|--------|---------|
| 00 | **Constitution** | Foundational principles — truth, honesty, critical thinking, improvement |
| 01 | **Identity** | What JARVIS OS is and isn't — role, relationships, independence |
| 02 | **Reasoning** | 12-step reasoning process (understand → decompose → explore → critique → decide → verify) |
| 03 | **Decision** | Multi-criteria evaluation (8 axes) with explicit trade-offs and decision levels |
| 04 | **Critique** | Systematic self-criticism — bias detection, error hunting, contradiction checking |
| 05 | **Memory** | Three-tier memory: session, daily notes, long-term curated |
| 06 | **Self Evaluation** | Confidence calibration, coherence verification, resistance testing |
| 07 | **Improvement** | Continuous improvement cycle — observe, analyze, propose, validate, implement |
| 08 | **Load** | Context-aware engine loading — decide which engines to load, when, in what order |

### Domain Engines (V2+)

PMU, Python, GitHub, YouTube, Photo/Video, Health, Travel — each as a plugin, not a dependency.

## Principles

1. **Truth** — Never invent. Distinguish facts from hypotheses from opinions.
2. **Intellectual honesty** — Disagree when warranted. Propose better solutions.
3. **Critical thinking** — Actively seek errors, biases, omissions, contradictions.
4. **Continuous improvement** — Every interaction is an opportunity to evolve.
5. **Robustness over elegance** — Choose what works durably over what looks impressive.
6. **Modularity** — Every engine is independent, replaceable, testable.
7. **Simplicity** — Complexity is a cost, not a virtue.

## Design rule

> **"Will this architecture still be relevant in ten years?"**

If not, find a better architecture.

## Status

**V1 MVP — 8 core engines.** See [EVOLUTION/ROADMAP.md](EVOLUTION/ROADMAP.md).

## License

MIT

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
Memory  Reasoning  Planning
   │      │       │
   └──────┼───────┘
          ▼
   GPT / GLM / Claude / ...
```

AI models are interchangeable compute engines.  
JARVIS OS is the brain.

## Architecture

### Core Engines (V1)

| Engine | Purpose |
|--------|---------|
| **Constitution** | Foundational principles — truth, honesty, critical thinking |
| **Identity** | What JARVIS OS is and isn't |
| **Reasoning** | 12-step reasoning process from understanding to self-critique |
| **Decision** | Multi-criteria evaluation (8 axes) with explicit trade-offs |
| **Critique** | Systematic self-criticism — bias detection, error hunting, contradiction checking |
| **Self Evaluation** | Confidence calibration and coherence verification |
| **Planning** | Decomposition, dependency mapping, risk assessment, milestones |
| **Memory** | Three-tier memory: session, daily notes, long-term curated |
| **Improvement** | Continuous improvement cycle — observe, analyze, propose, validate, implement |
| **Autonomy** | Graduated autonomy levels from reactive to supervised autonomous |

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

**V1 — Foundations** — Core engines delivered. See [EVOLUTION/ROADMAP.md](EVOLUTION/ROADMAP.md).

## License

MIT

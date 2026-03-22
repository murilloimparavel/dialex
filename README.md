<p align="center">
  <strong>D I A L E X</strong>
  <br />
  <em>Cognitive Search Amplifier</em>
</p>

<p align="center">
  Multi-mind debate that produces emergent knowledge
</p>

<p align="center">
  <a href="https://github.com/murilloimparavel/dialex/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License: MIT" /></a>
  <img src="https://img.shields.io/badge/status-early%20development-orange" alt="Status: Early Development" />
  <img src="https://img.shields.io/badge/python-3.11%2B-3776AB?logo=python&logoColor=white" alt="Python 3.11+" />
  <img src="https://img.shields.io/badge/PRD-complete-green" alt="PRD Complete" />
</p>

<p align="center">
  <b>English</b> | <a href="README.pt-br.md">Portugues</a> | <a href="README.es.md">Espanol</a> | <a href="README.zh-cn.md">中文</a>
</p>

---

## What is Dialex?

**The metaphor:** A round table where the authors of books argue with each other — and the argument produces a new book that none of them could have written alone.

Dialex is a system where multiple AI expert minds — each with a distinct reasoning method — debate problems and produce knowledge that no single mind could generate alone. The debate feeds a self-organizing knowledge graph that grows smarter with each interaction.

The name comes from **dia** (through/between, Greek) + **lex** (word/law, Latin) — *knowledge through dialogue*.

### Honest Framing

We believe in intellectual honesty about what this system does and does not do:

- **"Cognitive search amplifier"** — Dialex explores problem spaces more broadly than a single perspective can. It does not create consciousness or understanding.
- **"Combinatorial and structural novelty"** — The synthesis produces genuinely new combinations and framings, not ontological emergence. The novelty is real but bounded.
- **"Expert minds"** — The minds are persona-fidelity clones built with structured prompting methodology, not cognitive replicas of real people.
- **"Debate"** — The process is structured divergence under constraint, not genuine disagreement. The value comes from forcing heterogeneous reasoning paths through the same problem.

---

## Key Features

**Multi-Mind Debate Engine**
Three-phase pipeline: decomposition, positions + tensions, debate + synthesis. Multiple AI minds with distinct reasoning methods argue through problems until convergent insight emerges.

**Self-Organizing Knowledge Graph**
SQLite + JSON storage with FTS5 full-text search. Local-first, zero infrastructure. Knowledge nodes connect, strengthen, and reorganize based on usage patterns.

**Temporal Decay**
Knowledge ages naturally. Configurable half-life lets irrelevant nodes go dormant while frequently-accessed knowledge stays sharp.

**Contradiction Detection**
Automated identification of tension pairs across mind positions. Contradictions are not bugs — they are the raw material of synthesis.

**Round-Aware Retrieval**
Each debate round fetches new evidence from the knowledge graph based on what was actually said, not just the original query. The debate steers its own research.

**Multi-Scale Prompt Compression**
Three-tier compression (verbatim / condensed / abstract) keeps long debates within context limits without losing critical nuance.

**Multi-Perspective Decomposition**
Two minds propose different breakdowns of the same question before debate begins. The decomposition itself is a source of insight.

**Interview Mode**
`*interview {mind} {topic}` — Deep-dive a single expert mind on any topic within its domain. Structured Socratic extraction.

**Multi-Provider LLM Support**
Built on LiteLLM for provider-agnostic operation. Claude, Gemini, local models — mix and match across minds for maximum cognitive diversity.

**Anti-Sycophancy by Architecture**
Heterogeneous models across minds prevent the convergence bias that plagues single-model systems. Disagreement is a feature, not a failure mode.

---

## Quick Start

> **Note:** Dialex is in early development. The CLI and package are not yet published. The instructions below show the intended interface.

```bash
# Install (coming soon)
pip install dialex

# Initialize a knowledge base
dialex init my-research

# Ingest expert minds from MMOS
dialex ingest minds ./path/to/mmos-export/

# Run a debate
dialex debate "What are the second-order effects of widespread AI agent adoption?"

# Interview a specific mind
dialex interview "systems-thinker" "feedback loops in AI governance"

# Search the knowledge graph
dialex search "emergence" --decay-aware
```

### Development Setup

```bash
# Clone the repository
git clone https://github.com/murilloimparavel/dialex.git
cd dialex

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # Linux/macOS

# Install in development mode
pip install -e ".[dev]"

# Run tests
pytest
```

---

## Architecture Overview

```
                        USER QUERY
                            |
                            v
                 +---------------------+
                 |    DECOMPOSITION    |
                 |  (2 minds propose   |
                 |   different splits) |
                 +---------------------+
                            |
              +-------------+-------------+
              |             |             |
              v             v             v
        +---------+   +---------+   +---------+
        | Mind A  |   | Mind B  |   | Mind C  |
        | (Claude)|   | (Gemini)|   | (Local) |
        +---------+   +---------+   +---------+
              |             |             |
              v             v             v
         Position      Position      Position
         + Tensions    + Tensions    + Tensions
              |             |             |
              +------+------+
                     |
                     v
            +------------------+
            |  DEBATE ENGINE   |
            |  Round 1..N      |<----+
            |  (structured     |     |
            |   divergence)    |     |
            +------------------+     |
                     |               |
                     v               |
            +------------------+     |
            | ROUND-AWARE      |     |
            | RETRIEVAL        |-----+
            | (KG evidence     |
            |  for next round) |
            +------------------+
                     |
                     v
            +------------------+
            |    SYNTHESIS     |
            | Contradiction    |
            | pairs resolved   |
            +------------------+
                     |
                     v
         +------------------------+
         |   KNOWLEDGE GRAPH      |
         |   SQLite + JSON        |
         |   FTS5 full-text       |
         |   Temporal decay       |
         |   Self-organizing      |
         +------------------------+
```

---

## The Science Behind Dialex

Dialex is not built on intuition. The PRD was informed by 100+ scientific papers, 20+ repository analyses, and 35 framework evaluations conducted by 28 parallel AI research subagents across 4 waves. Here are the foundational principles:

### 1. Diversity Beats Ability (Hong & Page, 2004)

Groups of diverse problem solvers consistently outperform groups of high-ability identical solvers. This is the mathematical foundation for multi-mind debate: cognitive diversity produces better search coverage than raw capability.

### 2. Conceptual Blending (Fauconnier & Turner, 2002)

Novel ideas emerge when mental spaces from different domains are systematically blended. Dialex's synthesis phase implements structured blending across mind positions to produce combinations that no single mind would reach.

### 3. Paraconsistent Logic (da Costa, 1974)

Classical logic collapses in the presence of contradiction. Paraconsistent logic treats contradictions as information-bearing rather than system-breaking. Dialex's contradiction pair detection builds on this: tensions between minds are the raw material of insight, not errors to eliminate.

### 4. Self-Organizing Knowledge Graphs (Buehler Lab, MIT, 2024)

Knowledge structures can self-organize through usage patterns, strengthening high-value connections and letting unused paths decay. Dialex's temporal decay and connection reinforcement implement this principle at the storage layer.

### 5. Diverse Methods Achieve More (DMAD, ICLR 2025)

Reasoning diversity across methods (not just across models) is the key driver of multi-agent performance. Dialex assigns distinct reasoning methods to each mind, not just different model providers.

### 6. Multi-Agent Debate for Factuality (Du et al., 2023)

Multi-agent debate improves factual accuracy and reasoning quality over single-agent baselines. The debate structure provides natural error correction through cross-examination.

### 7. Structured Knowledge Accumulation (KARMA, NeurIPS 2025)

Knowledge graphs that accumulate structured relations across interactions outperform flat retrieval systems. Dialex's knowledge graph grows with each debate, making future debates more informed.

---

## Built On

Dialex is built on top of **MMOS (Mind Mapping & Orchestration System)**, created by **Alan Nicolas**. MMOS provides the upstream pipeline that creates expert mind clones using the **8-layer DNA Mental methodology** — a structured approach to encoding domain expertise, reasoning patterns, communication style, and cognitive biases into coherent AI personas.

Dialex takes the minds that MMOS creates and puts them into productive conflict. MMOS builds the experts; Dialex builds the debate table.

> **Credit:** The DNA Mental methodology and MMOS system are the work of Alan Nicolas. Dialex extends and orchestrates the minds that MMOS produces.

---

## Research & Acknowledgments

### Foundational Papers

| Paper | Authors | Relevance |
|-------|---------|-----------|
| *Groups of diverse problem solvers can outperform groups of high-ability problem solvers* | Hong & Page, 2004 | Mathematical proof that diversity > ability |
| *The Way We Think: Conceptual Blending* | Fauconnier & Turner, 2002 | Blending theory for synthesis engine |
| *On the theory of inconsistent formal systems* | da Costa, 1974 | Paraconsistent logic for contradiction handling |
| *Generative retrieval-augmented ontologic graph* | Buehler Lab / MIT, 2024 | Self-organizing knowledge graphs |
| *Improving Factuality and Reasoning via Multiagent Debate* | Du et al., 2023 | Multi-agent debate validation |
| *Debate Helps Supervise Unreliable Experts* | Irving et al. (OpenAI), 2018 | Debate as alignment mechanism |
| *Diverse Methods Achieve More* (DMAD) | ICLR 2025 | Method diversity > model diversity |

### Frameworks Studied

The PRD evaluated 35 framework candidates. Key systems that informed Dialex's design:

- **KARMA** (NeurIPS 2025) — Knowledge graph accumulation patterns
- **TruthfulRAG** (AAAI 2026) — Hallucination detection via knowledge graphs
- **MAGMA** — Multi-agent architecture patterns
- **Graphiti / Zep** — Temporal knowledge graph design
- **HippoRAG** — Neurobiologically-inspired retrieval
- **LightRAG** — Lightweight graph-based RAG
- **MiroFish** — Memory-inspired retrieval with forgetting
- **CrewAI / AutoGen / LangGraph** — Multi-agent orchestration patterns

### Research Process

- 28 parallel AI research subagents across 4 investigation waves
- 100+ scientific papers reviewed
- 20+ open-source repositories analyzed
- 35 framework candidates evaluated against 12 selection criteria

---

## MVP Roadmap

Dialex follows a 12-week MVP plan focused on proving the core hypothesis: multi-mind debate over a self-organizing knowledge graph produces measurably better knowledge synthesis than single-perspective approaches.

| Weeks | Phase | Deliverables |
|-------|-------|-------------|
| 1-2 | **Knowledge Graph Foundation** | SQLite schema + FTS5, CRUD operations, CLI skeleton, MMOS mind ingestion |
| 3-4 | **Retrieval & Decomposition** | Multi-perspective question decomposition, per-mind retrieval, round-aware retrieval |
| 5-7 | **Debate Engine** | 3-phase debate with LiteLLM, contradiction pair detection, multi-scale prompt compression |
| 8-9 | **Interview & Evaluation** | Interview mode, single-judge evaluation, baseline comparison metrics |
| 10-11 | **Hardening** | Polish, comprehensive tests, null hypothesis testing |
| 12 | **Validation** | Dog-food on real domain, document results |

### Null Hypothesis Test

The MVP includes a formal test against the null hypothesis: *"A single well-prompted LLM produces equivalent or better results than multi-mind debate."* If we cannot reject this hypothesis with measurable evidence, we will document that honestly.

---

## Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Areas where help is especially needed:

- Core debate engine implementation
- Knowledge graph storage layer (SQLite + JSON)
- CLI interface
- Multi-language documentation (ES, ZH)
- Testing and benchmarking
- LLM provider integrations

---

## License

MIT License. See [LICENSE](LICENSE) for details.

Copyright (c) 2026 Murillo Alves ([@murilloimparavel](https://github.com/murilloimparavel))

---

<p align="center">
  <em>"Knowledge through dialogue"</em>
  <br />
  <strong>dia</strong> (through, Greek) + <strong>lex</strong> (word, Latin)
</p>

# Green LLM Token Research

**Reducing Token Waste in Student LLM Use for University Learning Tasks: Implications for Sustainable AI Computing**

---

## Overview

As students increasingly rely on large language models for academic work, the computational cost of these interactions — and their environmental footprint — is rarely questioned. This project asks a simple question: **can we cut unnecessary token usage in everyday university-related LLM prompts without losing response quality or educational value?**

To answer this, we run a controlled comparison: for each academic task, a *baseline* prompt (written the way students typically phrase things) is measured against an *optimized* prompt (rewritten to be more token-efficient), while keeping the underlying task and expected learning outcome identical.

## What We're Measuring

| Item | Value |
|---|---|
| University-learning tasks | 500 |
| Task categories | 5 |
| Tasks per category | 100 |
| Prompt variants per task | 2 (baseline, optimized) |
| Executions per variant | 1 (primary run) |
| **Total primary LLM executions** | **1,000** (500 × 2) |

### The Five Task Categories

1. **Assignment Writing**
2. **Exam Preparation**
3. **Programming Help**
4. **Concept Learning**
5. **Research Paper Summarization**

## Defining "Academic" Scope

A task only qualifies for the dataset if its context is *explicitly* tied to a university setting — a course, an assessment, an exam, coursework, a lab activity, or formal research. This classification is based on the **stated purpose/context** of the interaction, not just the subject matter of the prompt itself. Generic, ambiguous, general-purpose queries are deliberately left out.

## Repository Layout

```
green-llm-token-research/
│
├── data/
│   ├── prompts/
│   │   └── prompts.csv              # master dataset of 500 tasks
│   ├── raw/
│   │   └── runs.jsonl                # raw LLM execution logs
│   ├── evaluation/
│   │   └── quality_scores.csv        # human evaluation scores
│   └── processed/
│       └── results.csv               # auto-generated paired results
│
├── contexts/
│   ├── papers/
│   ├── code/
│   └── assignment_materials/
│
├── scripts/
│   └── validate_prompts.py
│
├── notebooks/
├── figures/
├── logs/
│
├── config/
│   ├── controlled_vocabulary.json
│   ├── data_dictionary.csv
│   ├── run_data_dictionary.csv
│   ├── quality_data_dictionary.csv
│   ├── results_data_dictionary.csv
│   ├── experiment_config.json
│   └── quality_rubric.md
│
└── README.md
```

## Data Files, In Detail

**`data/prompts/prompts.csv`** — the master dataset. Each row holds: academic context, the underlying task, the baseline prompt, the optimized prompt, the optimization strategy applied, the expected content, and supporting metadata.

**`data/raw/runs.jsonl`** — one line per model execution. This is raw experimental data and must **never** be manually edited or overwritten after the fact.

**`data/evaluation/quality_scores.csv`** — human ratings for generated responses across three dimensions, each scored **1–5**:
- Accuracy
- Completeness
- Educational usefulness

**`data/processed/results.csv`** — the final paired baseline-vs-optimized comparison table, generated automatically by the analysis scripts (not written by hand).

## Ground Rules for the Experiment

1. A baseline and its optimized counterpart must always represent the **same** underlying task.
2. Optimization is about efficiency, not scope — it must **never** alter the intended educational outcome.
3. Raw outputs (`runs.jsonl`) are immutable once logged.
4. Failed executions and retries are kept in the record, not discarded.
5. Token count and latency are treated as **directly measured** variables.
6. Response quality is judged separately, using the predefined human evaluation rubric.
7. Environmental/computational impact is **estimated**, not measured directly — kept distinct from the directly measured variables.
8. Dataset validation is a hard gate: experiments cannot begin until it passes.

## Running Validation

Before executing anything, validate the dataset:

```bash
python scripts/validate_prompts.py
```

If validation reports any blocking errors, **do not proceed** with the main experiment until they're resolved.

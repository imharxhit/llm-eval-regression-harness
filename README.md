# LLM Evaluation & Prompt Regression Harness

A lightweight **Python** (`pytest`) evaluation suite for testing LLM prompts and RAG APIs across **Faithfulness**, **Answer Relevance**, **Context Recall**, **JSON Schema compliance**, and **p95 response latency** inside **GitHub Actions CI**.

## Why I Built This
Coming from a software QA and test automation background, I wanted a way to catch regressions when changing system prompts, switching models (e.g., `gpt-4o-mini` vs `llama-3.3-70b`), or tweaking chunk sizes. Instead of manually spot-checking outputs, this harness runs a golden dataset through deterministic schema/latency checks and semantic grading gates on every push.

## How AI Is Evaluated & Used
- **Faithfulness & Context Recall Scorers**: Measures whether claims in the LLM output are supported by the retrieved context passages and whether all ground-truth facts were recalled.
- **JSON Contract & Prompt Injection Checks**: Validates structured LLM responses against `JSONSchema` definitions and verifies that system prompt guardrails refuse jailbreak/override attempts.
- **Latency & Cost Telemetry**: Tracks per-request latency (`p50`, `p95`) and token usage budgets so slow prompt changes fail CI early.

## Quick Start
```bash
pip install -r requirements.txt
pytest -v
```

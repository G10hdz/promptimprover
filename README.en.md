# promptimprover

[Español](README.md) | English

Multi-agent prompt optimizer in a single Colab notebook. It takes a prompt, detects common problems, rewrites it, and generates three variants tuned to the OpenAI, Gemini, and Claude guidelines.

Kavak x OpenAI hackathon prototype: a one-cell experiment, not a service.

## What it does

- Reviews the prompt with three analysis agents: logical contradictions, expected output format, and few-shot example consistency.
- Rewrites the prompt and the inconsistent examples while preserving the original intent.
- Generates one optimized variant for OpenAI, one for Gemini, and one for Claude.
- Scores each variant with an evaluator agent and prints a per-attempt score table.

## How it works

Everything lives in `prompt_improver_multiAI.ipynb` (one cell, ~560 lines):

1. `optimize_prompt_parallel_with_platforms` runs the three checkers in parallel via `Runner.run` from the OpenAI Agents SDK.
2. `dev_rewriter` fixes the prompt and `fewshot_rewriter` aligns the examples.
3. `create_multi_optimized_outputs` runs `openai_optimizer`, `gemini_optimizer`, and `claude_optimizer`.
4. `prompt_evaluator_agent` and `_evaluate_platforms` score each variant.
5. `run_all_tests` loops over 6 test prompts (3 attempts each), picks the best attempt per test, and saves the summary to a JSON file.

All agents run on OpenAI (`gpt-5` and `gpt-5-mini`): the Gemini and Claude variants are written by the same model following each provider's practices, not by the Google or Anthropic APIs.

## How to run

1. Open `prompt_improver_multiAI.ipynb` in Colab (badge in the first cell) or VS Code.
2. `pip install openai-agents pydantic nest_asyncio` and export `OPENAI_API_KEY`.
3. Run the cell; the entrypoint runs the 6 tests and writes a `promptsmith_unified_results_*.json`.

If the SDK is not installed, the script falls back to shims that return example outputs: good for dry-running the orchestration, not for real optimization. It also tries to import `main_shared_runtime` as an alternate runtime; it is optional and not part of this repo.

## Structure

- `prompt_improver_multiAI.ipynb`: the whole project (agents, evaluator, and test suite).
- `docs/diagrams/architecture.html`: agent pipeline diagram.

## License

MIT (see `LICENSE`).

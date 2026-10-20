# promptimprover

Español | [English](README.en.md)

Optimizador de prompts multiagente en un solo notebook de Colab. Recibe un prompt, detecta problemas comunes, lo reescribe y genera tres variantes ajustadas a las guías de OpenAI, Gemini y Claude.

Prototipo del hackathon Kavak x OpenAI: un experimento de una celda, no un servicio.

## Qué hace

- Revisa el prompt con tres agentes de análisis: contradicciones lógicas, formato de salida esperado y consistencia de los ejemplos few-shot.
- Reescribe el prompt y los ejemplos inconsistentes conservando la intención original.
- Genera una variante optimizada para OpenAI, otra para Gemini y otra para Claude.
- Evalúa cada variante con un agente evaluador e imprime una tabla de scores por intento.

## Cómo funciona

Todo vive en `prompt_improver_multiAI.ipynb` (una celda, ~560 líneas):

1. `optimize_prompt_parallel_with_platforms` corre los tres checkers en paralelo con `Runner.run` del OpenAI Agents SDK.
2. `dev_rewriter` corrige el prompt y `fewshot_rewriter` alinea los ejemplos.
3. `create_multi_optimized_outputs` lanza `openai_optimizer`, `gemini_optimizer` y `claude_optimizer`.
4. `prompt_evaluator_agent` y `_evaluate_platforms` puntúan cada variante.
5. `run_all_tests` repite el ciclo sobre 6 prompts de prueba (3 intentos cada uno), elige el mejor intento por test y guarda el resumen en un JSON.

Todos los agentes corren sobre OpenAI (`gpt-5` y `gpt-5-mini`): las variantes de Gemini y Claude las escribe el mismo modelo siguiendo las prácticas de cada proveedor, no las APIs de Google ni Anthropic.

## Cómo correrlo

1. Abre `prompt_improver_multiAI.ipynb` en Colab (el badge está en la primera celda) o en VS Code.
2. `pip install openai-agents pydantic nest_asyncio` y exporta `OPENAI_API_KEY`.
3. Ejecuta la celda; el entrypoint corre los 6 tests y deja un `promptsmith_unified_results_*.json`.

Si el SDK no está instalado, el script cae en shims que devuelven salidas de ejemplo: sirven para probar la orquestación en seco, no para optimizar de verdad. También intenta importar `main_shared_runtime` como runtime alterno; es opcional y no viene en el repo.

## Estructura

- `prompt_improver_multiAI.ipynb`: el proyecto completo (agentes, evaluador y suite de tests).
- `docs/diagrams/architecture.html`: diagrama del pipeline de agentes.

## Licencia

MIT (ver `LICENSE`).

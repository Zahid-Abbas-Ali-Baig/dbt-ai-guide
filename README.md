# dbt-ai-guide

## Purpose

A **prompt library + config template** for building a production dbt project with an AI coding agent. You provide a **requirements document** ([`requirements.md`](requirements.md)) — the agent uses it (plus live schema discovery) to generate a full dbt project through phased prompts.

## Usage

1. Copy and fill [`requirements.md`](requirements.md) — domain context, business questions, and source-system hints.
2. Fill in [`config.md`](config.md) — `PROJECT_ROOT` (`.`), warehouse connection, `ENABLE_SEMANTIC_LAYER`, and paths to `requirements.md` / `design_brief.md`.
3. Run **Phase 0** with `config.md` only — bootstrap the dbt project in the current directory.
4. Run **Phase 1** with `config.md` + `requirements.md` — discovery writes [`design_brief.md`](design_brief.md).
5. **Approve the Design Brief** — edit `design_brief.md`, set `Status: approved`.
6. In your AI agent for Phases 2–7, attach:
   - config.md
   - requirements.md
   - design_brief.md
   - phase prompts from [`dbt_ai_agent_prompts_generalized.md`](dbt_ai_agent_prompts_generalized.md)
7. Run phases in order:
   - **Phase 0** — Bootstrap (skip if dbt project already works)
   - **Phase 1** — Discovery → `design_brief.md`
   - **Approve** — edit `design_brief.md`, set `Status: approved`
   - **Phases 2–6** — Build: sources → staging → intermediate → marts → docs (+ semantic layer if enabled)
   - **Phase 7** — Final validation: `dbt build`, grain checks, execution log

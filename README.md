# dbt-ai-guide

## Purpose

A **prompt library + config template** for building a production dbt project with an AI coding agent. You provide a single **requirements document** ([`requirements.md`](requirements.md)) — the agent uses it (plus live schema discovery) to generate a full dbt project through phased prompts.

## Usage

1. Copy and fill [`requirements.md`](requirements.md) — domain context, business questions, and source-system hints.
2. Fill in [`config.md`](config.md) — warehouse type, connection details, database/schema names, project name, and `REQUIREMENTS_DOC` path.
3. In your AI agent, attach:
   - config.md
   - requirements.md
   - phase prompts from [`dbt_ai_agent_prompts_generalized.md`](dbt_ai_agent_prompts_generalized.md)
4. Run phases in order:
   - **Phase 0** — Bootstrap: set up the dbt project (skip if already working)
   - **Phase 1** — Discovery: generate a Design Brief
   - **Approve the Design Brief** — required before continuing
   - **Phases 2–6** — Build: sources → staging → intermediate → marts → semantic layer + docs

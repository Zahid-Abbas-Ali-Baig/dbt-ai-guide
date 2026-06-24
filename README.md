# dbt-ai-guide

## Purpose

A **prompt library + config template** for building a production dbt project with an AI coding agent. You provide [`requirements.md`](requirements.md); the agent discovers schema and builds through phased prompts (0–8).

## Initial build

1. Fill [`requirements.md`](requirements.md) and [`config.md`](config.md).
2. Run **Phase 0** → **Phase 1** → approve [`design_brief.md`](design_brief.md).
3. Run **Phases 2–8** (dbt build + PBIP delivery). **Before Phase 8 (human):** create `BI_PBIP_DIR` and save an empty `.pbip` into that folder in Power BI Desktop — do not run Phase 8 until done.
4. Deliver to client.

## Client feedback (after review)

1. **Client** sends what is wrong or how a metric should be defined.
2. **Data engineer + analyst** fill [`client_feedback.md`](client_feedback.md) — what they said, agreed fix, which phases to re-run.
3. Run the **Feedback Re-run** prompt (in [`dbt_ai_agent_prompts_generalized.md`](dbt_ai_agent_prompts_generalized.md)) with `config.md`, `requirements.md`, `design_brief.md`, and `client_feedback.md` attached — **pass 1** updates both docs; sets `Status: pending approval` on **design_brief.md only**; **stops**.
4. **Review** both docs; set `Status: approved` on **design_brief.md** only, then run **Feedback Re-run** again — **pass 2** implements from the **approved design brief** (dbt + BI).
5. Deliver again. Repeat until sign-off.

The team owns `client_feedback.md`. `requirements.md` carries business context (no status field). **Implementation follows `design_brief.md` only** after you approve it.

## Files

| File | Role |
| ---- | ---- |
| [`config.md`](config.md) | Connection, paths, `BI_PBIP_DIR` |
| [`requirements.md`](requirements.md) | Business questions |
| [`design_brief.md`](design_brief.md) | Phase 1 output (technical KPI map) |
| [`client_feedback.md`](client_feedback.md) | Client review intake + phases to re-run |
| [`dbt_ai_agent_prompts_generalized.md`](dbt_ai_agent_prompts_generalized.md) | All prompts (0–8 + Feedback Re-run) |

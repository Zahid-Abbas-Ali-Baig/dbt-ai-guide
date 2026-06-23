# Project Config

> Fill once per engagement. Attach alongside [`dbt_ai_agent_prompts_generalized.md`](dbt_ai_agent_prompts_generalized.md) when running any phase prompt.

## How to Use

1. Replace every `{{placeholder}}` below with your project values.
2. Set `REQUIREMENTS_DOC`, `DESIGN_BRIEF_DOC`, and feedback-loop paths (defaults below).
3. Attach this file when running phase prompts. Attach `requirements.md` starting at **Phase 1**.
4. The agent reads `config.md` at the start of every phase and substitutes values into commands and file paths.
5. After client review: fill [`client_feedback.md`](client_feedback.md), then run the **Feedback Re-run** prompt from the prompt library.

> **Security:** Do not commit real passwords. Use a local-only copy of this file or environment variables for production credentials.

---

## Variables

```
PROJECT_ROOT:        .                        # dbt project files created in current directory
REQUIREMENTS_DOC:    requirements.md
DESIGN_BRIEF_DOC:    design_brief.md
CLIENT_FEEDBACK_DOC: client_feedback.md       # filled by DE/analyst after client review
AI_EXECUTION_LOG:    AI_EXECUTION_LOG.md      # optional per-engagement log

PROJECT_NAME:        {{my_project}}           # dbt project name, no spaces
WAREHOUSE_TYPE:      {{postgres}}             # postgres | snowflake | redshift | bigquery | duckdb
DATABASE_NAME:       {{my_database}}
SCHEMA_NAME:         {{my_schema}}            # v1: one source schema per engagement
DB_HOST:             {{localhost}}
DB_PORT:             {{5432}}
DB_USER:             {{postgres}}
DB_PASSWORD:         {{password}}
DB_THREADS:          {{4}}

SOURCE_NAME:         {{my_source}}            # v1: one source name in _sources.yml
STAGING_SCHEMA:      {{staging}}
INTERMEDIATE_SCHEMA: {{intermediate}}
MARTS_SCHEMA:        {{marts}}

ENABLE_SEMANTIC_LAYER: {{true}}             # true | false — skip semantic_models.yml when false
ENABLE_BI_DELIVERY:    {{false}}            # true | false — run Phase 8 when BI tool measures/report are in scope
BI_TOOL:               {{powerbi}}          # powerbi | looker | tableau | other — for Phase 8 guidance only
BI_BUILD_GUIDE_DOC:    {{bi/report_build_guide.txt}}  # optional page/measure build instructions for Phase 8
```

> **Not in this file:** table lists, fact/dimension classifications, column renames, join keys, metrics, or business questions. Those are inferred from the requirements doc + schema discovery in Phase 1.

> **Alignment:** `DATABASE_NAME`, `SCHEMA_NAME`, and `WAREHOUSE_TYPE` here should match the source-system hints in [`requirements.md`](requirements.md).

> **v1 scope:** One `SOURCE_NAME` and one `SCHEMA_NAME` per engagement. Additional source schemas require a future config extension.

---

## Example (do not use as active config)

<!--
PROJECT_NAME:        shopsphere
WAREHOUSE_TYPE:      postgres
DATABASE_NAME:       shopsphere
SCHEMA_NAME:         ecommerce
DB_HOST:             localhost
DB_PORT:             5432
DB_USER:             postgres
DB_PASSWORD:         <your-password>
DB_THREADS:          4

SOURCE_NAME:         ecommerce
STAGING_SCHEMA:      staging
INTERMEDIATE_SCHEMA: intermediate
MARTS_SCHEMA:        marts

ENABLE_SEMANTIC_LAYER: true
ENABLE_BI_DELIVERY: true
BI_TOOL: powerbi
BI_BUILD_GUIDE_DOC: bi/report_build_guide.txt

-->

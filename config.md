# Project Config

> Fill once per engagement. Attach alongside [`dbt_ai_agent_prompts_generalized.md`](dbt_ai_agent_prompts_generalized.md) when running any phase prompt.

## How to Use

1. Replace every `{{placeholder}}` below with your project values.
2. Set `REQUIREMENTS_DOC` and `DESIGN_BRIEF_DOC` paths (defaults: `requirements.md`, `design_brief.md`).
3. Attach this file when running phase prompts. Attach `requirements.md` starting at **Phase 1**.
4. The agent reads `config.md` at the start of every phase and substitutes values into commands and file paths.

> **Security:** Do not commit real passwords. Use a local-only copy of this file or environment variables for production credentials.

---

## Variables

```
PROJECT_ROOT:                              # dbt project files created in current directory
REQUIREMENTS_DOC:    requirements.md
DESIGN_BRIEF_DOC:    design_brief.md

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
-->

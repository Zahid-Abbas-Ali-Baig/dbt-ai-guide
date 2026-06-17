# Project Config

> Fill once per engagement. Attach alongside [`dbt_ai_agent_prompts_generalized.md`](dbt_ai_agent_prompts_generalized.md) when running any phase prompt.

## How to Use

1. Replace every `{{placeholder}}` below with your project values.
2. Set `REQUIREMENTS_DOC` to the path or filename of your requirements markdown (default: `requirements.md`).
3. Attach this file + the requirements doc when running phase prompts.
4. The agent reads `config.md` at the start of every phase and substitutes values into commands and file paths.

> **Security:** Do not commit real passwords. Use a local-only copy of this file or environment variables for production credentials.

---

## Variables

```
REQUIREMENTS_DOC:    requirements.md

PROJECT_NAME:        {{my_project}}           # dbt project name, no spaces
WAREHOUSE_TYPE:      {{postgres}}             # postgres | snowflake | redshift | bigquery | duckdb
DATABASE_NAME:       {{my_database}}
SCHEMA_NAME:         {{my_schema}}            # source schema containing raw tables
DB_HOST:             {{localhost}}
DB_PORT:             {{5432}}
DB_USER:             {{postgres}}
DB_PASSWORD:         {{password}}
DB_THREADS:          {{4}}

SOURCE_NAME:         {{my_source}}            # name used in _sources.yml and source()
STAGING_SCHEMA:      {{staging}}
INTERMEDIATE_SCHEMA: {{intermediate}}
MARTS_SCHEMA:        {{marts}}
```

> **Not in this file:** table lists, fact/dimension classifications, column renames, join keys, metrics, or business questions. Those are inferred from the requirements doc + schema discovery in Phase 1.

> **Alignment:** `DATABASE_NAME`, `SCHEMA_NAME`, and `WAREHOUSE_TYPE` here should match the source-system hints in [`requirements.md`](requirements.md).

---

## Example (do not use as active config)

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


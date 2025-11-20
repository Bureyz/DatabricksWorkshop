01_databricks_lakehouse_intro.ipynb ✅
   - Lakehouse concept
   - Workspace navigation
   - Clusters, notebooks, workflows

02_data_import_exploration.ipynb ✅
   - Import z różnych źródeł
   - Basic read/write
   - Data exploration (display, visualizations)

03_basic_transformations_sql_pyspark.ipynb ✅
   - Podstawowe transformacje
   - SQL vs PySpark basics
   - Filters, aggregations, joins

04_data_cleaning_quality.ipynb ✅
   - NULL handling
   - Duplicates
   - Data types
   - Basic validation

05_views_workflows.ipynb ✅
   - Temporary/Global views
   - Basic workflows
   - Parameterization




01_delta_lake_operations.ipynb [75 min] ⭐ ROZSZERZONY
   • Delta Lake fundamentals (ACID, Time Travel)
   • CREATE TABLE, INSERT, UPDATE, DELETE
   • MERGE operations (upserts)
   • Schema evolution (mergeSchema, overwriteSchema)
   • CLONE operations:
     - SHALLOW CLONE (metadata only, zero-copy)
     - DEEP CLONE (full data copy)
     - Use cases: testing, backup, env promotion
   • VACUUM & RESTORE:
     - VACUUM: remove old files, retention policy
     - Dry run mode
     - RESTORE: rollback to version
   • Change Data Feed (CDF):
     - Enable: ALTER TABLE SET TBLPROPERTIES
     - Read changes: table_changes() function
     - Change types: insert, update_preimage/postimage, delete
     - Use cases: audit, replication, incremental ETL

02_batch_data_ingestion.ipynb 🆕
   - COPY INTO (idempotent)
   - CTAS (CREATE TABLE AS SELECT)
   - File formats
   - Schema management
   - Error handling

03_streaming_data_ingestion.ipynb 🆕
   - Structured Streaming basics
   - Auto Loader (cloudFiles)
   - Checkpointing
   - Trigger modes
   - Schema evolution

04_medallion_architecture_pipeline.ipynb [105 min] 🆕
   • Medallion concept (Bronze → Silver → Gold)
   • Bronze: Raw data ingestion (batch + streaming)
   • Silver: Cleaned & validated data
   • Gold: Business-level aggregates
   • Star Schema implementation (Fact + Dimensions)
   • Slowly Changing Dimensions (SCD) - szczegółowa implementacja:
     - SCD Type 0: No changes (immutable dimensions)
     - SCD Type 1: Overwrite (no history) - dim_product example
     - SCD Type 2: Add row (full history) - dim_customer example
       * Surrogate keys, valid_from/to, is_current
       * MERGE implementation (2-step process)
     - SCD Type 3: Add column (limited history)
     - CDF integration: Using Change Data Feed for SCD
   • Data quality gates per layer
   • Incremental ETL/ELT patterns

05_optimization_best_practices.ipynb [60 min] ✅
   • Query plan analysis (explain())
   • Predicate pushdown, column pruning, file pruning
   • OPTIMIZE (compaction)
   • ZORDER BY (multi-dimensional clustering)
   • Partitioning strategies
   • Liquid Clustering (DBR 13.3+) 🆕
     - CLUSTER BY alternative to partitioning
     - Automatic clustering
     - When to use vs traditional partitioning
   • Small Files Problem (diagnosis + fix)
   • Auto Compaction (delta.autoOptimize)
   • Monitoring: DESCRIBE DETAIL
   • Performance troubleshooting




   01_advanced_transformations.ipynb 🆕 (ROZSZERZONY)
   ├── Sekcja A: Advanced PySpark
   │   - Window functions
   │   - Complex aggregations
   │   - UDFs & Pandas UDFs
   │   - Joins optimization
   │
   └── Sekcja B: Advanced SQL
       - CTEs, subqueries
       - Window functions w SQL
       - Pivot/Unpivot
       - Advanced date functions

02_lakeflow_declarative_pipelines.ipynb 🆕
   - Lakeflow SDP concepts
   - STREAMING TABLE vs MATERIALIZED VIEW
   - Expectations (data quality)
   - SQL vs Python API
   - APPLY CHANGES INTO (CDC pattern)
   - SCD Type 1/2 z Lakeflow
   - Event Log & Lineage
   - End-to-end pipeline example

03_databricks_workflows_orchestration.ipynb 🆕 (RENAMED)
   - Databricks Workflows (Jobs)
   - Task dependencies & DAGs
   - Parameters & dynamic values
   - Job clusters vs all-purpose
   - Retry strategies
   - Notifications & alerting
   - CI/CD integration

04_unity_catalog_governance.ipynb ✅
   - Unity Catalog hierarchy
   - Access control (GRANT/REVOKE)
   - Data lineage
   - Audit logs
   - Delta Sharing

05_production_best_practices.ipynb 🆕
   - Monitoring & logging
   - Error handling patterns
   - Testing strategies
   - Cost optimization
   - Security best practices
   - BI/ML integrations overview
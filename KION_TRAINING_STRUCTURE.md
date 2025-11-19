# KION Databricks Training - Skonsolidowana Struktura Szkoleniowa

**Data**: 19 listopada 2025  
**Program**: 3-dniowe szkolenie Databricks dla KION  
**Źródło**: KION_DETAIL agenda
Notebooki w formacie jupiter (JSON)

---

## Zoptymalizowana struktura katalogów

```
databricks-dea-training-kion/
├── DZIEN_1_Fundamentals_Exploration/
│   ├── 01_databricks_lakehouse_intro.ipynb
│   ├── 02_data_import_exploration.ipynb
│   ├── 03_basic_transformations_sql_pyspark.ipynb
│   ├── 04_data_cleaning_quality.ipynb
│   ├── 05_views_workflows.ipynb
│   └── workshops/
│       ├── 01_workspace_data_exploration_workshop.ipynb
│       ├── 02_transformations_cleaning_workshop.ipynb
│       └── 03_views_basic_jobs_workshop.ipynb
├── DZIEN_2_Lakehouse_Delta_Lake/
│   ├── 01_delta_lake_operations.ipynb
│   ├── 02_medallion_architecture.ipynb
│   ├── 03_batch_streaming_load.ipynb
│   ├── 04_bronze_silver_gold_pipeline.ipynb
│   ├── 05_optimization_best_practices.ipynb
│   └── workshops/
│       ├── 01_delta_medallion_workshop.ipynb
│       ├── 02_ingestion_pipeline_workshop.ipynb
│       └── 03_end_to_end_bronze_silver_gold_workshop.ipynb
├── DZIEN_3_Transformation_Governance_Integrations/
│   ├── 01_advanced_pyspark_transformations.ipynb
│   ├── 02_lakeflow_pipelines.ipynb
│   ├── 03_databricks_jobs_orchestration.ipynb
│   ├── 04_unity_catalog_governance.ipynb
│   ├── 05_bi_ml_integrations.ipynb
│   └── workshops/
│       ├── 01_advanced_transformations_workshop.ipynb
│       ├── 02_lakeflow_orchestration_workshop.ipynb
│       └── 03_governance_integrations_workshop.ipynb
├── 
│   00_setup.ipynb
├── datasets/
│   └── sample_data/
└── README.md
```

---

## Konwencje nazewnictwa

### Notebooki demo/teoria (główny folder dnia):
- **Format**: `01_nazwa_tematu.ipynb`
- **Zawartość**: Teoria + Live coding + Przykłady demonstracyjne
- **Cel**: Prowadzone przez instruktora

### Notebooki warsztatowe (folder workshops/):
- **Format**: `01_nazwa_workshop.ipynb`
- **Zawartość**: Zadania TODO + Luki w kodzie + Weryfikacja
- **Cel**: Praktyczne ćwiczenia dla uczestników

---

## Mapowanie do agendy KION_DETAIL

### 📅 DZIEŃ 1 — Fundamentals & Exploration

#### Notebooki demo:

**01_databricks_lakehouse_intro.ipynb**
- Koncepcja Lakehouse (Data Lake + Data Warehouse)
- Elementy platformy: Workspace, Catalog Explorer, Repos, Volumes, DBFS
- Compute: clusters, autoscaling, spot instances, Photon Engine
- Notebooks: magic commands (%sql, %python, %fs, %md)
- Unity Catalog overview: katalogi, schematy, tabele
- Różnice między Hive Metastore a Unity Catalog

**02_data_import_exploration.ipynb**
- Formaty danych: CSV, JSON, Parquet, Delta
- Ingest danych do dataframe z CSV,JSON,Parquet
- DataFrame Reader API: spark.read.format().option().load()
- Opcje readera: header, delimiter, schema, inferSchema, mode
- Konstruowanie schematów: StructType / StructField
- Podstawowe operacje eksploracyjne: columns, dtypes, count(), summary()

**03_basic_transformations_sql_pyspark.ipynb**
- Transformacje na przemian w pyspark i sql
- Transformacje kolumnowe: select(), withColumn(), drop(), alias()
- Logika warunkowa: when() / otherwise()
- Operacje tekstowe: regexp_replace(), trim(), lower(), upper()
- Filtry i sortowanie: filter(), where(), orderBy()
- Agregacje: groupBy(), agg(), rollup, cube
- SQL equivalents: CREATE VIEW, SELECT, GROUP BY, CASE WHEN

**04_data_cleaning_quality.ipynb**
- Obsługa wartości pustych: fillna(), dropna(), coalesce()
- Walidacja typów: cast(), to_date(), to_timestamp()
- Deduplikacja: dropDuplicates() - all columns vs key columns
- Standardyzacja: formaty dat, tekstów, kategorii
- Typowe problemy jakości: whitespace, niepoprawne kody, inconsistent formatting

**05_views_workflows.ipynb** 
- Różnice: VIEW vs TABLE vs DELTA TABLE
- Temp views, global temp views, persistent views
- Rejestracja tabel w Unity Catalog
- Przeglądanie tabel w Catalog Explorer
- Proste pipeline'y notebookowe - w workflow
- Databricks Jobs overview: taski, retry, harmonogramy

#### Warsztaty:

**01_workspace_data_exploration_workshop.ipynb** (90 min)
*Konsoliduje: Workspace setup + Data import + Exploration*
- Konfiguracja workspace i klastrów
- Wczytywanie różnych formatów (CSV, JSON, Parquet, Delta)
- Podstawowa eksploracja danych
- Konstruowanie schematów
- Analiza braków danych i wartości unikalnych

**02_transformations_cleaning_workshop.ipynb** (90 min)
*Konsoliduje: Transformacje + Data cleaning*
- Transformacje kolumnowe i warunkowe
- Filtry, sortowania, agregacje
- SQL vs PySpark comparison
- Czyszczenie: nulls, duplikaty, walidacja typów
- Quality checks i flagowanie problemów

**03_views_basic_jobs_workshop.ipynb** (60 min)
*Konsoliduje: Views + Basic workflows*
- Tworzenie różnych typów widoków
- Rejestracja tabel w Unity Catalog
- Prosty pipeline notebookowy
- Podstawowa konfiguracja Databricks Jobs

---

### 📅 DZIEŃ 2 — Lakehouse & Delta Lake

#### Notebooki demo:

**01_delta_lake_operations.ipynb**
- Delta Lake core features: ACID, Delta Log, Schema enforcement
- Schema evolution (additive, automatic)
- Time Travel i Copy-on-write
- CRUD operations: CREATE TABLE, INSERT, UPDATE, DELETE
- MERGE INTO - logika zmian na kluczach
- DESCRIBE DETAIL, DESCRIBE HISTORY
- Optymalizacja: OPTIMIZE, ZORDER BY, VACUUM

**02_medallion_architecture.ipynb**
- Bronze / Silver / Gold - logika warstw
- ETL vs ELT approach
- Zasady projektowania pipeline'ów
- Partitioning strategy
- Audyt i lineage - metadane w każdym kroku
- Data quality w kontekście warstw

**03_batch_streaming_load.ipynb**
- COPY INTO: kiedy używać, parametry (FILEFORMAT, VALIDATION_MODE, PATTERN)
- Auto Loader (CloudFiles): file notification, checkpointing, schema inference
- Schema evolution w praktyce
- Structured Streaming: micro-batch architecture
- readStream() / writeStream()
- Triggering: once vs processingTime
- Zarządzanie checkpointami
- MERGE na streamingu

**04_bronze_silver_gold_pipeline.ipynb**
- Bronze: raw load + audit columns (ingest_ts, source_file, ingested_by)
- Silver: cleaning, deduplikacja, sanity checks, JSON flattening (from_json, explode)
- Gold: KPI modeling, agregacje (daily/weekly/monthly), star schema vs denormalizacja

**05_optimization_best_practices.ipynb**
- Optymalizacja zapytań: predicate pushdown, file pruning, column pruning
- Analiza planu: explain()
- Optymalizacja tabel: partitioning keys, ZORDER use cases
- Small files problem
- Auto optimize / auto compaction

#### Warsztaty:

**01_delta_medallion_workshop.ipynb** (90 min)
*Konsoliduje: Delta operations + Medallion architecture*
- Delta CRUD operations (CREATE, INSERT, UPDATE, DELETE, MERGE)
- Time Travel hands-on
- Projektowanie Bronze/Silver/Gold architecture
- OPTIMIZE, ZORDER, VACUUM w praktyce

**02_ingestion_pipeline_workshop.ipynb** (90 min)
*Konsoliduje: COPY INTO + Auto Loader + Streaming*
- COPY INTO batch loads
- Auto Loader setup i konfiguracja
- Schema inference i evolution
- Structured Streaming basics
- Checkpointing setup

**03_end_to_end_bronze_silver_gold_workshop.ipynb** (120 min)
*Konsoliduje: Kompletny pipeline + optymalizacja*
- Raw → Bronze (ingest + audit)
- Bronze → Silver (cleaning + standardization + JSON processing)
- Silver → Gold (business models + aggregations)
- Performance optimization
- Query tuning

---

### 📅 DZIEŃ 3 — Transformation, Governance & Integrations

#### Notebooki demo:

**01_advanced_pyspark_transformations.ipynb**
- Window Functions: rowsBetween, rangeBetween, partitionBy, orderBy
- Funkcje okienkowe: lag, lead, row_number, dense_rank, rank
- Rolling windows i agregacje ruchome
- Struktury złożone: explode(), posexplode(), sequence()
- JSON processing: from_json(), to_json(), schema_of_json()
- Funkcje datowe: date_trunc, date_add, add_months, last_day

**02_lakeflow_pipelines.ipynb**
- Koncepcje Lakeflow: deklaratywny sposób definicji pipeline'ów
- SQL vs Python API
- Materialized views / streaming tables
- Expectations: warn / drop / fail
- Event log i lineage per tabela
- Automatic orchestration

**03_databricks_jobs_orchestration.ipynb**
- Multi-task Jobs
- Task types: notebook, DLT, dbt, SQL task
- Dependencies: depends_on
- Parametryzacja: job parameters, widget parameters (dbutils.widgets)
- Alerting i monitoring wykonania

**04_unity_catalog_governance.ipynb**
- Elementy UC: Metastore, Catalog, Schemas, Tables/Views/Functions, Volumes
- Zarządzanie dostępami: GRANT, REVOKE
- Privileges: SELECT, MODIFY, CREATE TABLE, EXECUTE
- Masking i row-level security
- Securable objects - inheritance
- Lineage & Audit: end-to-end lineage, metadane tabel
- Audit logging i aktywność użytkowników
- Delta Sharing: secure data sharing protocol

**05_bi_ml_integrations.ipynb**
- Power BI: Direct Lake vs Direct Query, połączenie do Gold Layer
- Modele semantyczne
- SAP Datasphere: łączenie przez JDBC, ELT flow
- Federated query engines (Dremio, Athena)
- MLflow basics: experiments, metrics, parameters, artifacts
- Feature Store - podstawy
- Spark MLlib - proste modele
- Gold Layer jako ML dataset

#### Warsztaty:

**01_advanced_transformations_workshop.ipynb** (90 min)
*Konsoliduje: Window functions + Complex structures + Temporal*
- Window Functions praktyka (lag/lead, rank, rolling aggregations)
- JSON processing hands-on
- Date/time transformations
- Sequence operations

**02_lakeflow_orchestration_workshop.ipynb** (90 min)
*Konsoliduje: DLT + Databricks Jobs*
- Delta Live Tables pipeline creation
- Expectations setup (warn/drop/fail)
- Multi-task Databricks Jobs
- Dependencies i parametryzacja
- Monitoring i alerting

**03_governance_integrations_workshop.ipynb** (90 min)
*Konsoliduje: Unity Catalog + BI/ML integrations*
- Unity Catalog setup (catalogs, schemas, permissions)
- GRANT/REVOKE privileges hands-on
- Data lineage exploration
- Power BI Direct Lake connection
- MLflow experiment tracking
- Feature Store basics
- Gold layer → ML dataset pipeline

---

## Konsolidacja warsztatów - uzasadnienie

### DZIEŃ 1: Z 5 → 3 warsztaty

✅ **Warsztat 1** (Workspace + Data + Exploration) - naturalna progresja: setup → load → explore  
✅ **Warsztat 2** (Transformations + Cleaning) - spójny workflow: transform → clean → validate  
✅ **Warsztat 3** (Views + Jobs) - logiczne połączenie: persist results → automate

### DZIEŃ 2: Z 5 → 3 warsztaty

✅ **Warsztat 1** (Delta + Medallion) - fundamenty: storage layer + architecture pattern  
✅ **Warsztat 2** (Ingestion methods) - wszystkie metody ładowania danych w jednym miejscu  
✅ **Warsztat 3** (End-to-end pipeline) - kompletny, realistyczny use case

### DZIEŃ 3: Z 5 → 3 warsztaty

✅ **Warsztat 1** (Advanced transformations) - zaawansowane techniki w jednym warsztacie  
✅ **Warsztat 2** (Lakeflow + Orchestration) - deklaratywne pipeline'y + automatyzacja  
✅ **Warsztat 3** (Governance + Integrations) - bezpieczeństwo + downstream consumers

Korzystaj zdanych z folderu dataset w workshop i demo. 

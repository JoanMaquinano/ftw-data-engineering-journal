# Journal - 2026-09-12 - Building Trustable Data Pipelines & Ingestion Patterns

## Today in one sentence
- Today I learned that failure is an expected state in data engineering, and building a trustable pipeline requires designing for idempotency, handling late/changed data, and mastering different ingestion patterns across files, databases, APIs, and web scrapers.

## What I learned
- **Building Trustable Pipelines:** Failure is inevitable (missing files, network errors, late records, schema changes). A trustable pipeline designs for failure and ensures idempotency so rerunning it safely yields the exact same state without producing duplicate data.
- **Ingestion Patterns & Strategies:**
  - *Files:* Ingest into the Bronze layer without altering raw structure. Prefer downloads over scraping.
  - *Databases:* Perform incremental loads via timestamps (`WHERE updated_at > last_processed`) or sequential IDs—never query the entire database with `SELECT *`.
  - *APIs:* Require handling pagination, rate limits, authentication, timeouts, and network failure.
  - *Web Scraping:* Extremely fragile due to UI changes; requires metadata capture for governance and provenance.
- **Data Mutation & History:** 
  - `MERGE` statements cleanly synchronize changes (inserts for new records, updates for modified records).
  - SCD Type 1 overwrites history; SCD Type 2 preserves historical changes.
  - Deduplication can be concisely handled using window functions like `QUALIFY ROW_NUMBER() OVER (PARTITION BY id ORDER BY updated_at DESC) = 1`.

## Terms I am still learning
- **Idempotency** - The property of a pipeline where executing it multiple times produces the exact same result as running it once, preventing duplicate records or corrupted states.
- **CDC (Change Data Capture)** - A set of software design patterns used to determine and track the data that has changed in a source database so actions can be taken based on those changes.
- **SCD (Slowly Changing Dimension)** - Data modeling strategy for managing how dimension data changes over time (Type 1 overwrites; Type 2 maintains history).
- **Bronze Layer** - The raw, unaltered landing zone in a medallion architecture that preserves data exactly as received from external systems.
- **Pagination** - An API pattern used to split large data payloads across multiple sequential responses/pages to manage payload sizes and memory usage.

## What confused me
- Managing late-arriving/backdated data and deciding which batch owns the backdated records without breaking downstream reporting logic.

## One small next step
- [x] Practice writing a SQL `MERGE INTO` statement and implement the equivalent `QUALIFY ROW_NUMBER()` deduplication using Python/Pandas.

## Git checkpoint
- [x] I created or updated a file
- [x] I wrote a commit
- [x] I pushed my changes

## Decisions or assumptions 
- *Decision:* Always preserve raw metadata (ingestion timestamp, source payload/file, origin) upon initial intake into the Bronze layer for auditability and data provenance.
- *Assumption:* Scraping external sites (e.g., Lazada) is a last resort due to UI instability; structured APIs or file downloads should always take priority.

## Evidence from today 
- **Batch Deduplication Query:**
  ```sql
  SELECT *
  FROM dirty_batch
  QUALIFY ROW_NUMBER() OVER (
      PARTITION BY customer_id
      ORDER BY updated_at DESC
  ) = 1;

## Reflection
### What felt easy today? 
Reading different file types (CSV, JSON, Parquet) into Pandas DataFrames and writing basic incremental WHERE queries for database ingestion.

### What felt difficult today? 
Understanding how to properly handle late-arriving data and deciding which processing batch should own backdated records, as well as distinguishing CDC from SCD Type 1 vs Type 2 logic.

### What do I want to understand better next time? 
How to implement rate limiting, handling timeouts, and implementing API pagination loops safely in Python.

## Mood or meme 
🛠️ "Failure is an expected state." (Designing for when things break, not just when they work!)

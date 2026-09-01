# Journal - 2025-08-15 - Session 4: Databricks Foundations

## Today in one sentence
- I learned that good data engineering starts with understanding the data, how it changes, and how it moves through a modern data platform. 

## What I learned
- Data can be classified as master data, reference data, event data, and metadata, and each serves a different purpose in a business. 
- Data can be static, mutable, append-only, or captured as snapshots depending on how it changes over time. 
- Different file formats have different strengths. CSV is easy to read, JSON is flexible, and Parquet is more efficient for analytics workloads. 
- OLTP systems are optimized for transactions, while OLAP systems are optimized for analysis and reporting. 
- Databricks follows an ELT approach and supports the Lakehouse architecture, which combines the flexibility of a data lake with the governance of a data warehouse. 
- A data engineer's goal is to produce trusted, clean, and usable data for the business. 

## Terms I am still learning
- **metadata** - data that describes other data, such as where it came from or how it was processed. 
- **OLTP** - systems designed for recording transactions quickly and accurately. 
- **OLAP** - systems designed for analysis, reporting, and decision-making. 
- **Lakehouse** - a platform that combines features of both data lakes and data warehouses. 
- **ELT** - Extract, Load, Transform; data is loaded first and transformed later. 

## What confused me
- I was still trying to understand when a company should use a database, data warehouse, data lake, or lakehouse.
- The differences between master data, reference data, and event data were clear in examples but harder to identify in real datasets.
- I understood the idea of ELT but was not yet sure how Databricks performs transformations behind the scenes.

## One small next step
- [x] Review the differences between database, data warehouse, data lake, and lakehouse.
- [x] Read more about the Medallion Architecture and how it relates to the sari-sari store pipeline assignment.
- [x] Practice identifying different data types and file formats from real datasets.

## Git checkpoint
- [ ] I created or updated a file
- [ ] I wrote a commit
- [ ] I pushed my changes

## Decisions or assumptions (optional)
- I assumed that understanding data fundamentals first is more important than memorizing Databricks features.
- I decided to focus on understanding data flow concepts before learning platform-specific tools.

## Evidence from today (optional)
- Session 4 notes on Databricks Foundations. 
- Sari-sari store Medallion Architecture pipeline assignment. 

## Reflection (optional)
- What felt easy today? Understanding the business examples used to explain data concepts.
- What felt difficult today? Remembering the different platform types and when each should be used.
- What do I want to understand better next time? How raw data actually moves through Bronze, Silver, and Gold layers in Databricks.

## Mood or meme (optional)
- "Every answer in data engineering somehow creates three new terms to learn. 😅"

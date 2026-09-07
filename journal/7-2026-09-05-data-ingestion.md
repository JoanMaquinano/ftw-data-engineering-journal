# Journal - 2026-09-07 - Session 7 Data Ingestion

## Today in one sentence

I learned how Apache Spark processes data at scale, why distributed computing introduces new challenges, and how data quality checks help ensure pipelines produce reliable results.

## What I learned

### Communication and Presentations

- Mehrabian's 7-38-55 model:
  - 55% body language
  - 38% tone of voice
  - 7% words
- Illustrative gestures help represent what you're saying.
- Emphatic gestures help stress important ideas.
- Open-hand gestures (such as palms facing upward) can make communication appear more welcoming.
- Good eye contact becomes easier when you know your material well.

### Data Engineering Insights

- A lot of the work performed by data engineers is invisible to end users.
- Spark is not always required for every data problem.
- Organizations that need Spark usually have larger-scale data environments and more mature data platforms.
- SQL is a language, while Spark is an execution engine.
- Spark allows SQL and data processing workloads to run across many machines.
- Scale is no longer only about row counts. It is also about distributing computation efficiently across clusters.
- Distributed systems introduce challenges related to networking, storage, memory, throughput, and data movement.

### Apache Spark

- Spark workloads are submitted through a driver node.
- The driver creates a DAG (Directed Acyclic Graph) of tasks.
- A cluster manager allocates resources to worker nodes.
- Executors perform computations on partitions of data.
- Network transfers become necessary when data needed for a computation exists on another node.
- Data movement is one of the most expensive operations in distributed computing.

### Partitions and Shuffles

- Partitioning data by dimensions such as day or month can improve processing efficiency.
- A shuffle occurs when data must move between partitions or nodes.
- Shuffle operations are expensive because they involve network transfers.

Commonly cheaper operations:

- Filter
- Select
- Simple transformations

Commonly expensive operations:

- GROUP BY
- JOIN
- DISTINCT
- SORT

### Databricks Usage

- Free accounts have compute limits.
- It is difficult to predict exactly when those limits will be reached.
- Running out of compute during demonstrations or presentations can be problematic.
- Use personal environments for experimentation.
- Use project environments for official exercises.
- Use `LIMIT` whenever possible instead of `SELECT *`.
- Temporary tables may be preferable to repeatedly executed CTEs for some workloads.
- Understanding Spark's computation sequence helps avoid unnecessary compute consumption.

### Data Quality

- A pipeline can run successfully and still produce incorrect data.
- Data quality should be defined before failures occur.
- Expectations should be converted into measurable checks.

Core dimensions of data quality:

- Complete
- Valid
- Unique
- Consistent
- Timely
- Accurate

Common data quality checks:

- Null checks
- Uniqueness checks
- Range checks
- Accepted value checks
- Referential integrity checks
- Volume checks

Possible outcomes:

- PASS
- WARN
- FAIL

### Data Quality Framework

For every check, define:

1. What are we checking?
2. What is the expected result?
3. What threshold is acceptable?
4. Is the severity WARN or FAIL?
5. Who owns the investigation?
6. How will results be recorded?

Data quality monitoring should help answer:

- What failed?
- When did the failure start?
- Is the issue getting worse?
- Which datasets fail most often?

### Data Quality Results Table

Example fields for a `dq_check_results` table:

- executed_at
- dataset
- check_name
- check_type
- status
- fail_count
- total_count
- fail_pct
- threshold
- severity

Useful monitoring metrics:

- Pass rate
- Failed checks
- Failures by dataset
- Failures by check type
- Last checked timestamp

## Terms I am still learning

- **Apache Spark** - A distributed processing engine for large-scale data workloads.
- **Driver Node** - The component that coordinates Spark jobs.
- **Executor** - A process that performs computations on worker nodes.
- **DAG (Directed Acyclic Graph)** - The execution plan Spark creates for processing tasks.
- **Shuffle** - Movement of data between partitions or nodes during computation.
- **Schema Evolution** - Changes made to a dataset structure over time.
- **Slowly Changing Dimension (SCD)** - Techniques for managing changes in dimension data.
- **Cluster Manager** - Service responsible for allocating resources across nodes.

## What confused me

- When Spark provides meaningful benefits over traditional SQL engines.
- The exact sequence Spark follows when executing jobs.
- How partitions are designed to minimize shuffle costs.
- How schema evolution is managed in production systems.
- The trade-offs between Spark performance and compute costs.

## One small next step

- [ ] Study Spark architecture in more detail (Driver, Executors, DAG, Cluster Manager).
- [ ] Review examples of shuffle-heavy versus shuffle-light queries.
- [ ] Create sample data quality checks using SQL.
- [ ] Build a mock `dq_check_results` monitoring table.
- [ ] Learn more about Slowly Changing Dimensions (SCDs).

## Git checkpoint

- [x] I created or updated a file.
- [x] I wrote a commit.
- [x] I pushed my changes.

## Decisions or assumptions

- Missing business keys should generally result in a rejection.
- Missing non-key values may result in warnings depending on business requirements.
- Data quality should be measured continuously, not only when issues occur.
- Spark should be used when scale justifies its overhead.

## Evidence from today 

- Session 7 notes
- Apache Spark architecture discussion
- Data quality framework examples
- Databricks compute management recommendations

## Reflection 

### What felt easy today?

Understanding the distinction between SQL as a language and Spark as an execution engine helped clarify where Spark fits in the data engineering ecosystem.

### What felt difficult today?

The distributed computing concepts, especially partitions, shuffles, executors, and network transfers, were harder to visualize than traditional SQL processing.

### What do I want to understand better next time?

I want to understand Spark execution plans, shuffle optimization techniques, and how production teams implement automated data quality monitoring.

## Mood or meme 

🤯 "Turns out the hardest part of big data isn't the data itself... it's moving the data around."

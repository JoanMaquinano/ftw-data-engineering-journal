# Journal - 2025-08-22 - Session 5: SQL + Data Modelling

## Today in one sentence
- I learned that good data modeling is less about creating tables and more about organizing data so it stays accurate, understandable, and useful. 

## What I learned
- Data engineering is easy to start learning but difficult to master because technical problems often become data modeling problems. 
- Data normalization helps reduce redundancy, prevent contradictions, and avoid insertion, update, and deletion anomalies. 
- First Normal Form (1NF) focuses on atomic values, proper keys, and avoiding repeating groups. 
- Second Normal Form (2NF) removes partial dependencies, while Third Normal Form (3NF) removes transitive dependencies. 
- OLTP systems prioritize transactional integrity, while OLAP systems are designed for answering business questions and analytics.
- Data models are usually designed in layers: conceptual, logical, and physical. 
- Different modeling approaches exist, including Kimball, Inmon, Data Vault, Wide Tables, and Medallion Architecture. The best choice depends on business requirements and trade-offs.
- In dimensional modeling, fact tables represent what happened, while dimension tables provide context such as who, what, when, and where. 

## Terms I am still learning
- **normalization** - organizing data to reduce duplication and improve consistency. 
- **1NF** - a normal form where each field contains a single value and repeating groups are removed. 
- **referential integrity** - rules that keep relationships between tables valid and consistent. 
- **fact table** - a table that stores business events or transactions. 
- **dimension table** - a table that provides descriptive information about facts. 
- **grain** - the level of detail represented by one row in a fact table. 

## What confused me
- I understood the theory behind 1NF, 2NF, and 3NF, but I still need more practice identifying violations in real datasets.
- The differences between Kimball, Inmon, Data Vault, and Medallion Architecture were still a little overwhelming.
- I understood what grain means conceptually, but I was not always sure how to define the correct grain for a business problem.
- It was not yet obvious when to keep data normalized versus when to denormalize it for analytics.

## One small next step
- [x] Practice normalizing a small dataset from 1NF to 3NF.
- [x] Review examples of fact and dimension tables in a star schema.
- [x] Identify the grain of each table in the Chinook project.

## Git checkpoint
- [x] I created or updated a file
- [x] I wrote a commit
- [x] I pushed my changes

## Decisions or assumptions (optional)
- I decided to focus on understanding fact tables, dimension tables, and grain first before comparing advanced modeling approaches.
- I assumed that most of the modeling decisions in the upcoming projects would become clearer once I started building actual star schemas.

## Evidence from today (optional)
- Session 5 notes on SQL and Data Modelling. 【1-479a9a】
- Examples discussing normalization, dimensional modeling, and star schemas. 

## Reflection (optional)
- What felt easy today? Understanding why duplicate or redundant data can cause problems.
- What felt difficult today? Keeping track of the differences between normalization levels and modeling frameworks.
- What do I want to understand better next time? How professional data teams decide between normalized models, star schemas, and Medallion Architecture.

## Mood or meme (optional)
- "So the answer isn't 'add more tables'... it's 'design better tables.' 🤯"

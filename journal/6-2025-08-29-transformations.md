# Journal - 2025-08-29 - Session 6: Spark & Transformations

## Today in one sentence
- I learned that a good data engineering project is not just about producing the right answer, but building a system that others can understand, validate, maintain, and reuse. 
## What I learned
- Dimensional modeling starts with the business process, not the tables. We begin by identifying what we want to understand, then determine the grain, facts, dimensions, and eventually arrive at a star schema. 【1-d3155f】【2-c77f57】
- The grain is the contract of the fact table. In Chinook, one row representing one invoice line preserves more detail than one row per invoice.
- Facts describe what happened and what can be measured, while dimensions provide the context needed to analyze those measurements. Revenue by genre, country, or month all depend on dimensions.
- Normalized models and dimensional models serve different purposes. One is optimized for running the business, while the other is optimized for understanding the business.
- A successful dimensional model should preserve business truth even when the structure changes. Revenue and counts should still match the source system after transformation. 
- Validation is a core part of data engineering. We should validate grain, uniqueness, and business metrics before trusting the output. 
- A pipeline is software. Creating tables is only part of the work. The project also needs version control, collaboration, documentation, validation, and maintainability. 
- Git tracks changes while GitHub enables collaboration. Together they create a history of what changed, why it changed, and who changed it. 
- Documentation is engineering infrastructure. README files, architecture diagrams, data models, validation documents, and decision logs all help future engineers understand and maintain a project. 
- The Instacart project should demonstrate the full engineering process: Bronze → Silver → Gold, dimensional modeling, validation, Git history, documentation, and dashboards. 

## Terms I am still learning
- **grain** - the level of detail represented by one row in a fact table. 
- **fact table** - a table containing measurable business events such as sales. 
- **dimension table** - a table providing descriptive context for facts such as customer, date, or product. 
- **star schema** - a dimensional model where a central fact table connects to multiple dimension tables. 
- **version control** - a system that tracks changes to code and allows teams to collaborate safely. 
- **validation** - checks used to verify that transformed data still matches business expectations and source data. 

## What confused me
- I understood that star schemas are built around business questions, but I was still not completely confident choosing the correct grain for new datasets.
- It was easier to understand dimensional modeling using Chinook than explaining why certain dimensions should be combined or separated.
- I was still learning where modeling decisions end and engineering decisions begin.
- I understood the need for documentation, but I was unsure about what level of detail belongs in README, Architecture, Data Model, Validation, and Decisions documents.

## One small next step
- [x] Review our Chinook star schema and identify the grain, facts, and dimensions without looking at the presentation.
- [x] Add journal entries and commit them to GitHub.
- [x] Continue documenting the Instacart project using README, Architecture, Data Model, Validation, and Decisions files.
- [x] Practice writing validation queries to verify row counts, uniqueness, and business metrics.

## Git checkpoint
- [x] I created or updated a file
- [x] I wrote a commit
- [x] I pushed my changes

## Decisions or assumptions (optional)
- Our team chose an invoice-line level grain because it preserves the detail needed for product, genre, and revenue analysis. 
- We assumed that changing the structure of the data should not change the business truth represented by the data. 
- We treated documentation as part of the project itself rather than something to add at the end. 

## Evidence from today (optional)
- Chinook dimensional modeling presentation. 
- Grain, fact, and dimension validation exercises. 
- Git and GitHub collaboration workflow discussion. 
- Instacart engineering project assignment. 

## Reflection (optional)
- What felt easy today? Understanding why business questions drive dimensional modeling decisions.
- What felt difficult today? Thinking like a data engineer instead of just a SQL user.
- What do I want to understand better next time? How experienced engineers decide what belongs in Gold and how they validate those decisions.
- One thing that clicked today: a dashboard is not the product. Trusted and well-documented data is the product.

## Mood or meme (optional)
- "Last week I thought data engineering was mostly SQL. This week I'm realizing the SQL is just one small piece of the system. 😅"

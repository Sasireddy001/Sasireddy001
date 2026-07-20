# Data Engineering / ETL Flash Cards

## Core Concepts

**Q: What is ETL?**  
**A:** ETL stands for Extract, Transform, Load. It's the process of extracting data from source systems, transforming it to fit operational needs, and loading it into a target data warehouse.

**Q: What is the difference between ETL and ELT?**  
**A:** ETL transforms data before loading. ELT loads raw data first and transforms it in the target system (e.g., data warehouse, lakehouse).

**Q: What is a data warehouse?**  
**A:** A data warehouse is a centralized repository for structured data from various sources, optimized for analytics and reporting.

**Q: What is a data lake?**  
**A:** A data lake is a storage repository for raw, structured, and unstructured data at any scale. It stores data in its native format until needed.

**Q: What is a lakehouse?**  
**A:** A lakehouse combines the flexibility of data lakes with the performance and ACID transactions of data warehouses. Examples: Delta Lake, Apache Iceberg, Apache Hudi.

## Data Pipelines

**Q: What is a data pipeline?**  
**A:** A data pipeline is a series of steps that move data from source systems to destination systems, including extraction, transformation, and loading.

**Q: What are the stages of a data pipeline?**  
**A:** Ingestion, validation, transformation, enrichment, loading, and monitoring. Each stage ensures data quality and reliability.

**Q: What is batch processing?**  
**A:** Batch processing processes large volumes of data at scheduled intervals (e.g., daily, hourly). Suitable for high-volume, low-latency-tolerant workloads.

**Q: What is stream processing?**  
**A:** Stream processing processes data in real-time as it arrives, with low latency. Suitable for real-time analytics, monitoring, and alerting.

**Q: What is the difference between batch and stream processing?**  
**A:** Batch processes data in chunks at intervals. Stream processes data continuously with low latency. Batch is simpler; stream requires handling late data and state.

## Data Modeling

**Q: What is a star schema?**  
**A:** A star schema is a data warehouse model with a central fact table connected to dimension tables. It's simple and optimized for queries.

**Q: What is a snowflake schema?**  
**A:** A snowflake schema is a normalized version of a star schema where dimension tables are further normalized. It saves space but adds join complexity.

**Q: What is a fact table?**  
**A:** A fact table contains quantitative data (facts) and foreign keys to dimension tables. Examples: sales, orders, transactions.

**Q: What is a dimension table?**  
**A:** A dimension table contains descriptive attributes (dimensions) about facts. Examples: customer, product, time, location.

**Q: What is a slowly changing dimension (SCD)?**  
**A:** SCD is a technique to track historical changes in dimension data. Type 1 overwrites, Type 2 keeps history with effective dates, Type 3 adds new columns.

## Data Quality

**Q: What is data quality?**  
**A:** Data quality refers to the accuracy, completeness, consistency, timeliness, and validity of data.

**Q: How do you measure data quality?**  
**A:** Use metrics like completeness (missing values), accuracy (correctness), consistency (format), timeliness (freshness), and validity (constraints).

**Q: What are common data quality issues?**  
**A:** Missing values, duplicates, inconsistent formats, out-of-range values, referential integrity violations, and stale data.

**Q: How do you handle missing data?**  
**A:** Impute with mean/median/mode, use default values, drop rows/columns, or use advanced techniques like ML-based imputation.

**Q: What is data validation?**  
**A:** Data validation ensures data meets defined rules and constraints before it enters the pipeline. Examples: schema validation, range checks, regex validation.

## Data Ingestion

**Q: What is data ingestion?**  
**A:** Data ingestion is the process of importing data from various sources into a data system (lake, warehouse, or database).

**Q: What are the types of data ingestion?**  
**A:** Batch ingestion (scheduled), real-time ingestion (streaming), and change data capture (CDC) for incremental updates.

**Q: What is change data capture (CDC)?**  
**A:** CDC captures changes in source databases (inserts, updates, deletes) and applies them to the target system in near real-time.

**Q: What are common CDC techniques?**  
**A:** Log-based CDC (reads database transaction logs), trigger-based CDC (uses database triggers), and timestamp-based CDC (queries by timestamp).

**Q: What is the difference between full load and incremental load?**  
**A:** Full load extracts all data from the source. Incremental load extracts only changes since the last load, reducing time and resource usage.

## Data Transformation

**Q: What are common data transformations?**  
**A:** Cleaning, normalization, aggregation, enrichment, joining, pivoting, and filtering.

**Q: What is data normalization?**  
**A:** Normalization organizes data to reduce redundancy and improve integrity. In databases, it's splitting tables into related tables.

**Q: What is data denormalization?**  
**A:** Denormalization combines tables to improve read performance at the cost of redundancy. Common in data warehousing.

**Q: What is data enrichment?**  
**A:** Data enrichment adds value to data by joining with other sources, calculating derived fields, or adding contextual information.

**Q: What is data aggregation?**  
**A:** Aggregation summarizes data (sum, count, avg, etc.) to provide insights at different granularities (daily, weekly, monthly).

## Data Storage Formats

**Q: What are common data storage formats?**  
**A:** Parquet, ORC, Avro, JSON, CSV, Delta Lake, Apache Iceberg, Apache Hudi.

**Q: Why use Parquet for data engineering?**  
**A:** Columnar storage, efficient compression, predicate pushdown, and schema evolution. Optimized for analytical queries.

**Q: What is the difference between Parquet and Avro?**  
**A:** Parquet is columnar and optimized for analytics. Avro is row-based and optimized for write-heavy workloads and schema evolution.

**Q: What is the difference between CSV and Parquet?**  
**A:** CSV is plain text, human-readable, but inefficient for large datasets. Parquet is binary, compressed, and optimized for performance.

**Q: What is the difference between JSON and Parquet?**  
**A:** JSON is flexible, schema-less, and verbose. Parquet is schema-aware, compressed, and efficient for analytics.

## Data Partitioning

**Q: What is data partitioning?**  
**A:** Partitioning divides data into smaller chunks based on column values, improving query performance and manageability.

**Q: What are common partitioning strategies?**  
**A:** Range partitioning (e.g., date ranges), hash partitioning (hash of key), and list partitioning (explicit values).

**Q: What is the difference between partitioning and bucketing?**  
**A:** Partitioning splits data by column values into directories. Bucketing hashes data into a fixed number of files for efficient joins.

**Q: How do you choose partition columns?**  
**A:** Choose columns with high cardinality and frequently used in filters (e.g., date, country). Avoid over-partitioning (too many small files).

**Q: What is partition pruning?**  
**A:** Partition pruning skips reading partitions that don't match the query filter, improving performance.

## Data Skew

**Q: What is data skew?**  
**A:** Data skew occurs when data is unevenly distributed across partitions or nodes, causing some tasks to run much slower.

**Q: How do you detect data skew?**  
**A:** Monitor task durations, check partition sizes, and use Spark UI or query statistics to identify uneven distribution.

**Q: How do you handle data skew?**  
**A:** Salting keys, broadcasting smaller tables, using AQE (Adaptive Query Execution), or implementing custom partitioners.

**Q: What is salting in data engineering?**  
**A:** Salting adds a random suffix to a key to distribute data more evenly, reducing skew.

**Q: What is the impact of data skew on performance?**  
**A:** Skew causes slow tasks, longer job times, and resource waste. It can lead to out-of-memory errors or timeouts.

## Data Orchestration

**Q: What is data orchestration?**  
**A:** Data orchestration is the coordination and scheduling of data pipelines, ensuring tasks run in the right order and dependencies are met.

**Q: What are common orchestration tools?**  
**A:** Apache Airflow, Prefect, Dagster, Luigi, AWS Step Functions, Azure Data Factory, Google Cloud Composer.

**Q: What is a DAG in orchestration?**  
**A:** DAG (Directed Acyclic Graph) is a workflow definition that defines tasks and dependencies without cycles.

**Q: What is the difference between Airflow and Prefect?**  
**A:** Airflow is a mature platform with a rich UI. Prefect is newer, more Pythonic, and supports dynamic workflows and better error handling.

**Q: What is the difference between Airflow and Dagster?**  
**A:** Airflow is task-oriented. Dagster is data-oriented, focusing on data assets and their dependencies.

## Data Governance

**Q: What is data governance?**  
**A:** Data governance is the management of data availability, usability, integrity, and security in an organization.

**Q: What are data governance frameworks?**  
**A:** DAMA (Data Management Association), GDPR, CCPA, and internal policies for data classification, access control, and lineage.

**Q: What is data lineage?**  
**A:** Data lineage tracks the origin and movement of data from source to destination, helping with debugging, compliance, and impact analysis.

**Q: What is data catalog?**  
**A:** A data catalog is a metadata repository that helps organizations discover, understand, and govern their data assets.

**Q: What is data classification?**  
**A:** Data classification labels data based on sensitivity (e.g., public, internal, confidential) to apply appropriate security measures.

## Data Security

**Q: What are common data security practices?**  
**A:** Encryption at rest and in transit, access control (RBAC, ABAC), data masking, tokenization, and audit logging.

**Q: What is data masking?**  
**A:** Data masking obfuscates sensitive data (e.g., PII) while preserving format for testing and development.

**Q: What is the difference between encryption and hashing?**  
**A:** Encryption is reversible with a key. Hashing is one-way and used for integrity checks.

**Q: What is the difference between RBAC and ABAC?**  
**A:** RBAC (Role-Based Access Control) assigns permissions based on roles. ABAC (Attribute-Based Access Control) uses attributes (user, resource, environment).

**Q: What is tokenization?**  
**A:** Tokenization replaces sensitive data with non-sensitive tokens, while the original data is stored securely in a vault.

## Data Performance

**Q: How do you optimize ETL performance?**  
**A:** Use partitioning, caching, parallel processing, incremental loads, efficient data formats, and monitor bottlenecks.

**Q: What is the difference between row-based and columnar storage?**  
**A:** Row-based stores data row by row (good for OLTP). Columnar stores data column by column (good for OLAP, analytics).

**Q: What is predicate pushdown?**  
**A:** Predicate pushdown applies filters as early as possible (e.g., at the source) to reduce data transferred and processed.

**Q: What is projection pushdown?**  
**A:** Projection pushdown selects only needed columns as early as possible, reducing I/O and memory usage.

**Q: What is the difference between lazy and eager evaluation?**  
**A:** Lazy evaluation delays computation until needed. Eager evaluation computes immediately. Spark uses lazy evaluation for transformations.

## Data Testing

**Q: What is data testing?**  
**A:** Data testing validates the accuracy, completeness, and reliability of data pipelines through unit tests, integration tests, and data quality checks.

**Q: What are common data testing techniques?**  
**A:** Schema validation, data profiling, reconciliation, anomaly detection, and golden dataset comparison.

**Q: What is data reconciliation?**  
**A:** Data reconciliation compares data between source and target to ensure consistency and identify discrepancies.

**Q: What is a golden dataset?**  
**A:** A golden dataset is a trusted reference dataset used for testing and validation of data pipelines.

**Q: How do you test data pipelines?**  
**A:** Unit tests for transformations, integration tests for end-to-end pipelines, and data quality checks for output validation.

## Data Monitoring

**Q: What is data monitoring?**  
**A:** Data monitoring tracks the health, performance, and quality of data pipelines in real-time, enabling proactive issue detection.

**Q: What are common data monitoring metrics?**  
**A:** Pipeline latency, throughput, error rates, data freshness, data volume, and data quality metrics.

**Q: What is data drift?**  
**A:** Data drift occurs when the statistical properties of data change over time, affecting model performance or pipeline behavior.

**Q: How do you detect data drift?**  
**A:** Monitor distribution changes, compare with baseline, use statistical tests (KS test, chi-square), or ML-based drift detection.

**Q: What is an alert in data monitoring?**  
**A:** An alert is a notification triggered when a metric crosses a threshold, indicating a potential issue (e.g., pipeline failure, data quality degradation).

## Data Engineering Best Practices

**Q: What are some data engineering best practices?**  
**A:** Use idempotent operations, document schemas, version control pipelines, monitor and alert, test thoroughly, and use modular design.

**Q: Why is idempotency important in data pipelines?**  
**A:** Idempotency ensures re-running a pipeline produces the same result, enabling safe retries and reprocessing without duplicates.

**Q: What is modular design in data engineering?**  
**A:** Modular design breaks pipelines into reusable components (extractors, transformers, loaders) for maintainability and reusability.

**Q: How do you handle schema changes in data pipelines?**  
**A:** Use schema evolution, backward compatibility, versioned schemas, and handle changes gracefully (e.g., default values for new columns).

**Q: What is the difference between idempotent and idempotent?**  
**A:** Idempotent operations produce the same result regardless of how many times they are executed. This is critical for safe reprocessing.

## Data Engineering Interview Questions

**Q: Describe a complex data pipeline you built.**  
**A:** Explain the problem, architecture, technologies used, challenges faced, and results achieved. Focus on scalability, reliability, and business impact.

**Q: How do you handle late-arriving data?**  
**A:** Use watermarking in streaming, reprocess with batch jobs, or use upsert logic in the target system.

**Q: How do you ensure data quality in your pipelines?**  
**A:** Implement validation rules, schema enforcement, data profiling, reconciliation, and automated alerts for quality issues.

**Q: How do you optimize a slow data pipeline?**  
**A:** Identify bottlenecks (CPU, I/O, network), optimize queries, use caching, increase parallelism, and tune configurations.

**Q: How do you design a data warehouse schema?**  
**A:** Understand business requirements, identify facts and dimensions, choose star or snowflake schema, and ensure performance and scalability.

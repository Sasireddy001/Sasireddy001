# Quick Definitions Flash Cards

## Data Engineering Terms

**Q: What is a data lakehouse?**  
**A:** A data lakehouse combines the flexibility of data lakes with the performance and ACID transactions of data warehouses. Examples: Delta Lake, Apache Iceberg, Apache Hudi.

**Q: What is data skew?**  
**A:** Data skew occurs when data is unevenly distributed across partitions or nodes, causing some tasks to run much slower than others.

**Q: What is partitioning?**  
**A:** Partitioning divides data into smaller chunks based on column values, improving query performance and manageability.

**Q: What is bucketing?**  
**A:** Bucketing hashes data into a fixed number of files for efficient joins. Unlike partitioning, bucketing doesn't create directories.

**Q: What is data lineage?**  
**A:** Data lineage tracks the origin and movement of data from source to destination, helping with debugging, compliance, and impact analysis.

**Q: What is a data catalog?**  
**A:** A data catalog is a metadata repository that helps organizations discover, understand, and govern their data assets.

**Q: What is data profiling?**  
**A:** Data profiling analyzes data to understand its structure, quality, and patterns (e.g., null counts, distinct values, distributions).

**Q: What is data reconciliation?**  
**A:** Data reconciliation compares data between source and target to ensure consistency and identify discrepancies.

**Q: What is idempotency?**  
**A:** Idempotency means an operation produces the same result regardless of how many times it is executed. Critical for safe reprocessing.

**Q: What is a golden dataset?**  
**A:** A golden dataset is a trusted reference dataset used for testing and validation of data pipelines.

## Spark Terms

**Q: What is a DAG in Spark?**  
**A:** DAG (Directed Acyclic Graph) is the logical plan of transformations in Spark, representing dependencies between operations.

**Q: What is Catalyst optimizer?**  
**A:** Catalyst is Spark's query optimizer that improves performance through rule-based and cost-based optimizations.

**Q: What is Tungsten?**  
**A:** Tungsten is Spark's memory management and binary processing engine that improves CPU and memory efficiency.

**Q: What is AQE?**  
**A:** AQE (Adaptive Query Execution) optimizes queries at runtime by coalescing partitions, converting joins, and handling skew.

**Q: What is a shuffle?**  
**A:** A shuffle is the process of redistributing data across partitions, typically required for wide transformations like joins and aggregations.

**Q: What is a broadcast variable?**  
**A:** A broadcast variable is a read-only variable cached on each executor to avoid shipping large data repeatedly in tasks.

**Q: What is an accumulator?**  
**A:** An accumulator is a shared variable that can only be added to, used for aggregating values across executors.

**Q: What is a narrow transformation?**  
**A:** A narrow transformation does not require shuffling data between partitions (e.g., map, filter).

**Q: What is a wide transformation?**  
**A:** A wide transformation requires shuffling data across partitions (e.g., groupBy, join, reduceByKey).

**Q: What is the difference between `cache()` and `persist()`?**  
**A:** `cache()` stores in memory only. `persist()` lets you choose storage levels (MEMORY_ONLY, MEMORY_AND_DISK, DISK_ONLY).

## Streaming Terms

**Q: What is a watermark?**  
**A:** A watermark is a threshold for how late data can arrive in streaming, allowing state cleanup and handling late data.

**Q: What is exactly-once semantics?**  
**A:** Exactly-once semantics ensures each event is processed exactly once, even in the presence of failures. Requires idempotent sinks and checkpointing.

**Q: What is a micro-batch?**  
**A:** A micro-batch is a small batch of data processed at short intervals in streaming (e.g., every 1 second).

**Q: What is continuous processing?**  
**A:** Continuous processing is an experimental low-latency streaming mode that processes events one by one.

**Q: What is checkpointing?**  
**A:** Checkpointing saves the query's progress (offsets, state) to reliable storage for fault tolerance and exactly-once semantics.

**Q: What is state in streaming?**  
**A:** State is information maintained across batches for operations like aggregations, joins, and deduplication.

**Q: What is state TTL?**  
**A:** State TTL (Time To Live) automatically removes state that hasn't been updated for a specified duration.

**Q: What is the difference between `append`, `complete`, and `update` output modes?**  
**A:** Append writes only new rows. Complete writes the entire result table. Update writes changed rows.

**Q: What is a trigger?**  
**A:** A trigger defines when to output results in streaming (e.g., Trigger.Once, Trigger.ProcessingTime, Trigger.Continuous).

**Q: What is a streaming query?**  
**A:** A streaming query is a continuous query that reads from a source, processes data, and writes to a sink indefinitely.

## Delta Lake Terms

**Q: What is the Delta transaction log?**  
**A:** The `_delta_log` directory contains JSON files that record every operation (commit) on a Delta table.

**Q: What is time travel?**  
**A:** Time travel allows you to query previous versions of a Delta table using a version number or timestamp.

**Q: What is schema enforcement?**  
**A:** Schema enforcement ensures that writes to a Delta table match the table's schema. Mismatched columns or types are rejected.

**Q: What is schema evolution?**  
**A:** Schema evolution allows you to add new columns to a Delta table without breaking existing queries.

**Q: What is OPTIMIZE?**  
**A:** `OPTIMIZE` compacts small files into larger files and can use Z-Ordering for efficient predicate pushdown.

**Q: What is VACUUM?**  
**A:** `VACUUM` physically deletes old data files that are no longer referenced by the Delta log.

**Q: What is Z-Ordering?**  
**A:** Z-Ordering is a technique to co-locate related data in files based on column values, improving query performance.

**Q: What is the difference between `UPDATE` and `MERGE`?**  
**A:** `UPDATE` modifies existing rows. `MERGE` can update, insert, or delete rows based on match conditions (upsert).

**Q: What is a Delta Lake table?**  
**A:** A Delta Lake table is a Parquet table with a transaction log, providing ACID, time travel, and schema evolution.

**Q: What is the difference between Delta Lake and Parquet?**  
**A:** Delta Lake adds a transaction log on top of Parquet, enabling ACID, time travel, and schema evolution.

## Kafka Terms

**Q: What is a Kafka topic?**  
**A:** A topic is a logical channel or category to which events are published. Topics are split into partitions for scalability.

**Q: What is a Kafka partition?**  
**A:** A partition is an ordered, immutable sequence of events. Each partition is stored on one or more brokers.

**Q: What is a Kafka offset?**  
**A:** An offset is a unique identifier for each event within a partition. Consumers track offsets to know where they are in the stream.

**Q: What is a consumer group?**  
**A:** A consumer group is a set of consumers that work together to consume a topic. Each partition is assigned to one consumer.

**Q: What is consumer lag?**  
**A:** Consumer lag is the difference between the latest offset in a partition and the consumer's current offset.

**Q: What is rebalancing?**  
**A:** Rebalancing occurs when consumers join or leave a group. Kafka reassigns partitions among active consumers.

**Q: What is the difference between `acks=1` and `acks=all`?**  
**A:** `acks=1` waits for the leader to acknowledge. `acks=all` waits for all replicas to acknowledge (more durable).

**Q: What is log compaction?**  
**A:** Log compaction keeps only the latest value for each key in a Kafka topic, useful for changelog topics.

**Q: What is the difference between Kafka and RabbitMQ?**  
**A:** Kafka is designed for high-throughput event streaming. RabbitMQ is a traditional message broker for work queues.

**Q: What is Kafka Connect?**  
**A:** Kafka Connect is a tool for scalably and reliably streaming data between Kafka and other systems (databases, file systems).

## DevOps Terms

**Q: What is CI/CD?**  
**A:** CI (Continuous Integration) merges code frequently and runs tests. CD (Continuous Delivery/Deployment) automates the release process.

**Q: What is IaC?**  
**A:** IaC (Infrastructure as Code) is managing infrastructure using code (e.g., Terraform) instead of manual processes.

**Q: What is a container?**  
**A:** A container is a lightweight, standalone package that includes everything needed to run an application (Docker).

**Q: What is a Kubernetes Pod?**  
**A:** A Pod is the smallest deployable unit in Kubernetes, containing one or more containers that share the same network and storage.

**Q: What is a Kubernetes Deployment?**  
**A:** A Deployment manages a set of Pods, ensuring the desired number of replicas are running and handling rolling updates.

**Q: What is a Kubernetes Service?**  
**A:** A Service exposes a set of Pods as a network service, providing stable networking and load balancing.

**Q: What is a ConfigMap?**  
**A:** A ConfigMap stores configuration data as key-value pairs, used to inject configuration into Pods.

**Q: What is a Secret?**  
**A:** A Secret stores sensitive data (passwords, tokens, keys) in an encoded form, used to inject credentials into Pods.

**Q: What is Helm?**  
**A:** Helm is a package manager for Kubernetes, using charts to define complex applications.

**Q: What is the difference between Docker and Kubernetes?**  
**A:** Docker builds and runs containers. Kubernetes orchestrates containers at scale (deployment, scaling, networking).

## Cloud Terms

**Q: What is EC2?**  
**A:** EC2 (Elastic Compute Cloud) is AWS's virtual machine service (IaaS).

**Q: What is Lambda?**  
**A:** Lambda is AWS's serverless compute service that runs code in response to events without managing servers.

**Q: What is S3?**  
**A:** S3 (Simple Storage Service) is AWS's object storage service for files (unstructured data).

**Q: What is EBS?**  
**A:** EBS (Elastic Block Store) is AWS's block storage service attached to EC2 instances (structured data).

**Q: What is Azure Functions?**  
**A:** Azure Functions is Azure's serverless compute service, similar to AWS Lambda.

**Q: What is Azure Blob Storage?**  
**A:** Azure Blob Storage is Azure's object storage service, similar to AWS S3.

**Q: What is BigQuery?**  
**A:** BigQuery is GCP's serverless data warehouse for analytics.

**Q: What is Google Kubernetes Engine (GKE)?**  
**A:** GKE is Google's managed Kubernetes service.

**Q: What is the difference between IaaS, PaaS, and SaaS?**  
**A:** IaaS provides infrastructure (e.g., EC2). PaaS provides platforms (e.g., Heroku). SaaS provides software (e.g., Gmail).

**Q: What is a VPC?**  
**A:** A VPC (Virtual Private Cloud) is a logically isolated network in the cloud.

## SQL Terms

**Q: What is a primary key?**  
**A:** A primary key is a column (or set of columns) that uniquely identifies each row in a table.

**Q: What is a foreign key?**  
**A:** A foreign key is a column that references the primary key of another table, establishing a relationship.

**Q: What is a composite key?**  
**A:** A composite key is a primary key made up of two or more columns.

**Q: What is an index?**  
**A:** An index is a data structure that improves query performance by allowing faster data retrieval.

**Q: What is the difference between clustered and non-clustered indexes?**  
**A:** A clustered index sorts and stores data physically. A non-clustered index stores a separate structure with pointers.

**Q: What is a view?**  
**A:** A view is a virtual table based on the result-set of an SQL statement, used to simplify complex queries.

**Q: What is a stored procedure?**  
**A:** A stored procedure is a prepared SQL code that can be saved and reused, often with parameters.

**Q: What is a trigger?**  
**A:** A trigger is a stored procedure that automatically executes in response to certain events (e.g., INSERT, UPDATE, DELETE).

**Q: What is the difference between `DELETE` and `TRUNCATE`?**  
**A:** `DELETE` removes rows one by one and can be rolled back. `TRUNCATE` removes all rows quickly and cannot be rolled back.

**Q: What is the difference between `WHERE` and `HAVING`?**  
**A:** `WHERE` filters rows before grouping. `HAVING` filters groups after aggregation.

## System Design Terms

**Q: What is the CAP theorem?**  
**A:** CAP theorem states that a distributed system can only guarantee two of Consistency, Availability, and Partition tolerance.

**Q: What is the difference between horizontal and vertical scaling?**  
**A:** Horizontal scaling adds more machines (scale out). Vertical scaling adds more power to existing machines (scale up).

**Q: What is a load balancer?**  
**A:** A load balancer distributes incoming traffic across multiple servers to improve responsiveness and availability.

**Q: What is a CDN?**  
**A:** A CDN (Content Delivery Network) distributes content to edge servers closer to users, reducing latency.

**Q: What is the difference between monolithic and microservices architecture?**  
**A:** Monolithic is a single, unified application. Microservices is a collection of loosely coupled, independently deployable services.

**Q: What is service discovery?**  
**A:** Service discovery is the process of dynamically finding network locations of service instances.

**Q: What is a service mesh?**  
**A:** A service mesh is a dedicated infrastructure layer for managing service-to-service communication (e.g., Istio).

**Q: What is the difference between synchronous and asynchronous communication?**  
**A:** Synchronous communication requires the sender to wait for a response. Asynchronous does not block the sender.

**Q: What is a message queue?**  
**A:** A message queue stores messages until they are consumed, enabling asynchronous communication.

**Q: What is a dead letter queue (DLQ)?**  
**A:** A DLQ stores messages that failed to be processed, allowing later analysis or reprocessing.

## Behavioral Terms

**Q: What is the STAR method?**  
**A:** STAR is a framework for answering behavioral questions: Situation, Task, Action, Result.

**Q: What is a behavioral interview?**  
**A:** A behavioral interview assesses how you've handled past situations to predict future performance.

**Q: What is a situational interview?**  
**A:** A situational interview asks how you would handle hypothetical scenarios.

**Q: What is a technical interview?**  
**A:** A technical interview assesses your technical skills through coding, system design, or problem-solving.

**Q: What is a case study interview?**  
**A:** A case study interview presents a business problem and asks you to analyze and propose a solution.

**Q: What is a panel interview?**  
**A:** A panel interview involves multiple interviewers asking questions simultaneously.

**Q: What is a phone screen?**  
**A:** A phone screen is a brief initial interview to assess basic qualifications and fit.

**Q: What is a take-home assignment?**  
**A:** A take-home assignment is a coding or design task given to complete outside the interview.

**Q: What is a whiteboard interview?**  
**A:** A whiteboard interview asks you to solve problems on a whiteboard or screen, often without an IDE.

**Q: What is a coding challenge?**  
**A:** A coding challenge is a timed test to solve algorithmic problems, often on platforms like HackerRank or LeetCode.

## General Terms

**Q: What is API?**  
**A:** API (Application Programming Interface) is a set of rules that allows different software applications to communicate.

**Q: What is REST?**  
**A:** REST (Representational State Transfer) is an architectural style for designing networked applications using HTTP methods.

**Q: What is GraphQL?**  
**A:** GraphQL is a query language for APIs that allows clients to request exactly the data they need in a single request.

**Q: What is JSON?**  
**A:** JSON (JavaScript Object Notation) is a lightweight data-interchange format, easy for humans to read and write.

**Q: What is XML?**  
**A:** XML (eXtensible Markup Language) is a markup language that defines rules for encoding documents in a human-readable and machine-readable format.

**Q: What is YAML?**  
**A:** YAML (YAML Ain't Markup Language) is a human-readable data serialization language, often used for configuration files.

**Q: What is a token?**  
**A:** A token is a piece of data that represents a security credential or a unit of data in a text stream.

**Q: What is authentication vs authorization?**  
**A:** Authentication verifies who you are (e.g., password). Authorization determines what you can do (e.g., permissions).

**Q: What is OAuth?**  
**A:** OAuth is an open standard for access delegation, allowing users to grant third-party applications access to their resources without sharing credentials.

**Q: What is JWT?**  
**A:** JWT (JSON Web Token) is a compact, URL-safe means of representing claims to be transferred between two parties.

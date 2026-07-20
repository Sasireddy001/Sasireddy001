# Delta Lake Flash Cards

## Core Concepts

**Q: What is Delta Lake?**  
**A:** Delta Lake is an open-source storage layer that brings ACID transactions to Apache Spark and big data workloads. It provides reliability, performance, and security for data lakes.

**Q: What are the key features of Delta Lake?**  
**A:** ACID transactions, schema enforcement and evolution, time travel, scalable metadata handling, unified batch and streaming processing, and data versioning.

**Q: How does Delta Lake differ from Parquet?**  
**A:** Parquet is a columnar file format without transaction support. Delta Lake adds a transaction log (_delta_log) on top of Parquet, enabling ACID, time travel, and schema evolution.

**Q: What is the Delta transaction log?**  
**A:** The `_delta_log` directory contains JSON files that record every operation (commit) performed on the Delta table. Each file represents a commit with metadata like add/remove files, schema changes, and statistics.

## ACID Transactions

**Q: What does ACID mean in Delta Lake?**  
**A:** Atomicity (transactions are all-or-nothing), Consistency (data remains valid), Isolation (transactions don't interfere), Durability (committed data survives failures).

**Q: How does Delta Lake achieve ACID?**  
**A:** Through optimistic concurrency control with the transaction log. Writers serialize commits using the log, ensuring no conflicting writes and atomic updates.

**Q: What is optimistic concurrency control?**  
**A:** Writers assume no conflicts and proceed. On commit, they check if the log version matches their expectation. If not, they retry. This avoids locking and enables high throughput.

**Q: What happens if two writers try to write to the same Delta table simultaneously?**  
**A:** One writer succeeds, the other detects a version mismatch and retries. The retry mechanism ensures only valid commits are applied.

## Time Travel

**Q: What is time travel in Delta Lake?**  
**A:** Time travel allows you to query previous versions of a Delta table using a version number or timestamp. Useful for auditing, rollback, and debugging.

**Q: How do you query a specific version of a Delta table?**  
**A:** `spark.read.format("delta").option("versionAsOf", 5).load("/path/to/table")` or `option("timestampAsOf", "2024-01-01")`.

**Q: How do you restore a Delta table to a previous version?**  
**A:** Use `spark.sql("RESTORE TABLE delta.`/path/to/table` TO VERSION 5")` or `TO TIMESTAMP '2024-01-01'`.

**Q: What are the use cases for time travel?**  
**A:** Auditing data changes, rolling back bad updates, debugging by comparing versions, and reproducing issues with historical data.

## Schema Enforcement & Evolution

**Q: What is schema enforcement in Delta Lake?**  
**A:** Schema enforcement ensures that writes to a Delta table match the table's schema. Mismatched columns or types are rejected by default.

**Q: How do you enable schema enforcement?**  
**A:** It is enabled by default. Use `option("mergeSchema", "false")` to enforce strictly, or `option("overwriteSchema", "true")` to allow schema changes during overwrite.

**Q: What is schema evolution?**  
**A:** Schema evolution allows you to add new columns to a Delta table without breaking existing queries. Old queries see null values for new columns.

**Q: How do you add a new column to a Delta table?**  
**A:** Use `ALTER TABLE table_name ADD COLUMN column_name data_type` or write with `option("mergeSchema", "true")` to automatically add new columns.

## Delta Operations

**Q: What are the main Delta operations?**  
**A:** `MERGE`, `UPDATE`, `DELETE`, `VACUUM`, `OPTIMIZE`, `DESCRIBE HISTORY`, and `RESTORE`.

**Q: How do you perform an upsert (merge) in Delta Lake?**  
**A:** Use `MERGE INTO target USING source ON target.id = source.id WHEN MATCHED THEN UPDATE SET ... WHEN NOT MATCHED THEN INSERT ...`.

**Q: What is the difference between `UPDATE` and `MERGE`?**  
**A:** `UPDATE` modifies existing rows. `MERGE` can update existing rows, insert new rows, or delete rows based on match conditions (upsert).

**Q: How do you delete rows from a Delta table?**  
**A:** Use `DELETE FROM table_name WHERE condition` or `MERGE` with a delete clause. Deleted rows are marked for removal in the log.

## OPTIMIZE & VACUUM

**Q: What is the `OPTIMIZE` operation?**  
**A:** `OPTIMIZE` compacts small files into larger files to improve query performance. It uses Z-Ordering for efficient predicate pushdown.

**Q: What is Z-Ordering?**  
**A:** Z-Ordering is a technique to co-locate related data in files based on column values. It improves performance for queries filtering on those columns.

**Q: What is the `VACUUM` operation?**  
**A:** `VACUUM` physically deletes old data files that are no longer referenced by the Delta log. It frees up storage space.

**Q: What is the default retention period for VACUUM?**  
**A:** The default retention is 7 days. Files older than the retention period are eligible for deletion. Use `VACUUM table_name RETAIN N HOURS` to change.

**Q: Why should you be careful with VACUUM?**  
**A:** VACUUM permanently deletes files, so you lose the ability to time travel to versions older than the retention period. Ensure no readers need those versions.

## Delta Streaming

**Q: How do you read Delta Lake as a streaming source?**  
**A:** `spark.readStream.format("delta").load("/path/to/table")`. This reads new data as it arrives.

**Q: How do you write streaming data to Delta Lake?**  
**A:** `df.writeStream.format("delta").outputMode("append").option("checkpointLocation", "...").start("/path/to/table")`.

**Q: What are the benefits of using Delta Lake for streaming?**  
**A:** Exactly-once semantics, schema enforcement, time travel for debugging, and unified batch and streaming processing.

**Q: How do you handle schema evolution in streaming writes?**  
**A:** Use `option("mergeSchema", "true")` to automatically add new columns from streaming data to the Delta table.

## Performance & Optimization

**Q: How does Delta Lake improve query performance?**  
**A:** Through file statistics in the log (min/max values, null counts), data skipping, Z-Ordering, and automatic file compaction with OPTIMIZE.

**Q: What is data skipping?**  
**A:** Data skipping uses statistics from the log to skip reading files that don't match the query predicate. For example, if a file's min/max values don't overlap the filter, it's skipped.

**Q: How do you enable Z-Ordering?**  
**A:** Use `OPTIMIZE table_name ZORDER BY (column1, column2)` to co-locate data based on those columns.

**Q: What is the difference between `OPTIMIZE` and `ZORDER BY`?**  
**A:** `OPTIMIZE` compacts files. `ZORDER BY` additionally reorders data within files for better predicate pushdown. Use together for best results.

## Delta Lake on Databricks

**Q: What is Databricks Delta?**  
**A:** Databricks Delta is the managed version of Delta Lake on Databricks, with additional features like auto-compaction, photon acceleration, and integration with Unity Catalog.

**Q: What is Photon in Databricks?**  
**A:** Photon is a vectorized query engine on Databricks that accelerates SQL and DataFrame operations, including Delta Lake operations.

**Q: What is Unity Catalog?**  
**A:** Unity Catalog is a unified governance solution for Databricks that provides fine-grained access control, lineage, and discovery for Delta tables across workspaces.

**Q: How do you enable auto-compaction in Databricks?**  
**A:** Set `spark.databricks.delta.autoCompact.enabled = true`. It automatically compacts small files after writes.

## Delta Lake on Azure

**Q: How do you use Delta Lake on Azure?**  
**A:** Delta Lake works with Azure Data Lake Storage (ADLS) Gen2. Use the `abfss://` protocol to access ADLS paths.

**Q: What is the difference between Delta Lake and Azure Synapse Analytics?**  
**A:** Delta Lake is an open-source storage layer. Azure Synapse Analytics is a managed analytics service that can use Delta Lake as its storage format.

**Q: How do you mount ADLS in Databricks?**  
**A:** Use `dbutils.fs.mount(source="abfss://...", mount_point="/mnt/data", extra_configs={...})` to mount ADLS to Databricks.

## Delta Lake on AWS

**Q: How do you use Delta Lake on AWS?**  
**A:** Delta Lake works with S3. Use the `s3a://` protocol with Hadoop-AWS configuration to access S3 paths.

**Q: What are the considerations for using Delta Lake on S3?**  
**A:** S3 is eventually consistent, so use consistent object storage (like S3 Express One Zone) or configure Delta Lake to handle eventual consistency.

**Q: How do you configure S3 credentials for Delta Lake?**  
**A:** Set Hadoop configuration in Spark: `spark.hadoop.fs.s3a.access.key`, `spark.hadoop.fs.s3a.secret.key`, or use IAM roles.

## Delta Lake vs Alternatives

**Q: How does Delta Lake compare to Apache Iceberg?**  
**A:** Both are open table formats with ACID, time travel, and schema evolution. Delta Lake is tightly integrated with Spark. Iceberg has broader engine support (Spark, Flink, Trino).

**Q: How does Delta Lake compare to Apache Hudi?**  
**A:** Both support ACID, time travel, and upserts. Hudi has more built-in indexing and incremental query support. Delta Lake has simpler integration with Spark.

**Q: When should you choose Delta Lake over Iceberg or Hudi?**  
**A:** Choose Delta Lake if you use Spark heavily and want simplicity. Choose Iceberg if you need multi-engine support. Choose Hudi if you need advanced indexing and incremental processing.

## Best Practices

**Q: What are some Delta Lake best practices?**  
**A:** Use `OPTIMIZE` regularly, set appropriate VACUUM retention, enable schema enforcement, use time travel for debugging, and monitor file sizes.

**Q: How do you monitor Delta Lake tables?**  
**A:** Use `DESCRIBE HISTORY table_name` to see commit history, `DESCRIBE DETAIL table_name` for table details, and monitor file sizes and count.

**Q: How do you handle large numbers of small files in Delta Lake?**  
**A:** Use `OPTIMIZE` to compact files, tune write partitions to avoid too many small files, and use auto-compaction in Databricks.

**Q: What is the recommended file size for Delta Lake?**  
**A:** Aim for 128MB to 1GB files. Too small files hurt performance; too large files slow down reads. Use OPTIMIZE to achieve this.

## Error Handling

**Q: What happens if a write to Delta Lake fails?**  
**A:** The transaction is rolled back, and no data is committed. The log ensures atomicity, so partial writes are not visible.

**Q: How do you handle schema mismatch errors?**  
**A:** Use `option("mergeSchema", "true")` to allow schema evolution, or fix the schema mismatch before writing.

**Q: What is a "concurrent modification exception"?**  
**A:** This occurs when multiple writers try to modify the same Delta table simultaneously. Retry the operation or use a single writer pattern.

## Delta Lake & Structured Streaming

**Q: How do you handle late data in Delta Lake streaming?**  
**A:** Use watermark in Structured Streaming and Delta Lake's ability to handle updates. Delta Lake's ACID ensures exactly-once semantics.

**Q: Can you read and write to the same Delta table in streaming?**  
**A:** Yes, but be careful with infinite loops. Use different paths for source and sink, or use `foreachBatch` for custom logic.

**Q: How do you achieve exactly-once semantics with Delta Lake streaming?**  
**A:** Use checkpointing in Structured Streaming, idempotent writes (Delta Lake MERGE), and watermark to handle late data.

## Delta Lake & Machine Learning

**Q: How does Delta Lake support ML workflows?**  
**A:** Provides versioned datasets for reproducibility, time travel for debugging, and ACID transactions for reliable feature store updates.

**Q: What is a feature store in Delta Lake?**  
**A:** A feature store is a centralized repository for ML features. Delta Lake's ACID and versioning make it a good backend for feature stores.

**Q: How do you version training data with Delta Lake?**  
**A:** Use time travel to query specific versions of training data, or use `COPY INTO` to snapshot data at a point in time.

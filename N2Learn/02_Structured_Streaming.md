# Structured Streaming Flash Cards

## Core Concepts

**Q: What is Structured Streaming in Spark?**  
**A:** Structured Streaming is a scalable and fault-tolerant stream processing engine built on the Spark SQL engine. It treats streaming data as a continuously appended table and uses the same DataFrame/Dataset API as batch processing.

**Q: What is the difference between DStream and Structured Streaming?**  
**A:** DStream is the older micro-batch API based on RDDs. Structured Streaming is the newer API based on DataFrames/Datasets with better performance, exactly-once semantics, and integration with Spark SQL.

**Q: What is a streaming query in Structured Streaming?**  
**A:** A streaming query is a continuous query that reads from a source, processes data, and writes to a sink. It runs indefinitely until stopped with `streamingQuery.stop()`.

**Q: What is the difference between `readStream` and `read`?**  
**A:** `readStream` creates a streaming DataFrame that continuously reads data. `read` creates a static DataFrame for batch processing.

## Sources & Sinks

**Q: What are common sources in Structured Streaming?**  
**A:** Kafka, Kinesis, File sources (JSON, CSV, Parquet, ORC), Socket source (for testing), Rate source (generates data for testing), and Delta Lake.

**Q: What are common sinks in Structured Streaming?**  
**A:** File sinks (JSON, CSV, Parquet, ORC, Delta Lake), Kafka, Kinesis, Console sink (for testing), Foreach sink (for custom write logic), and Memory sink (for testing).

**Q: How do you read from Kafka in Structured Streaming?**  
**A:** `spark.readStream.format("kafka").option("kafka.bootstrap.servers", "localhost:9092").option("subscribe", "topic").load()`

**Q: How do you write to Delta Lake in Structured Streaming?**  
**A:** `streamingQuery = df.writeStream.format("delta").outputMode("append").option("checkpointLocation", "/path/to/checkpoint").start("/path/to/delta/table")`

## Output Modes

**Q: What are the three output modes in Structured Streaming?**  
**A:** Append, Complete, and Update. Append writes only new rows. Complete writes the entire result table. Update writes changed rows.

**Q: When should you use Append mode?**  
**A:** Append mode for queries that only add new rows (e.g., filtering, map). Not supported for aggregations without watermark.

**Q: When should you use Complete mode?**  
**A:** Complete mode for aggregations where you want the entire result table each time (e.g., global counts). Used only for queries without watermark.

**Q: When should you use Update mode?**  
**A:** Update mode for aggregations with watermark where you want only changed rows. More efficient than Complete for large result tables.

## Watermarks

**Q: What is a watermark in Structured Streaming?**  
**A:** A watermark is a threshold for how late data can arrive. It tells Spark to drop data older than the threshold and allows state cleanup.

**Q: How do you define a watermark?**  
**A:** `df.withWatermark("eventTime", "5 minutes")` where `eventTime` is a timestamp column and `5 minutes` is the allowed lateness.

**Q: Why are watermarks important?**  
**A:** Watermarks allow Spark to drop old state, limit memory usage, and handle late data. Without watermarks, state grows indefinitely.

**Q: What happens to data that arrives after the watermark?**  
**A:** Data that arrives after the watermark threshold is dropped (late data) and not included in the result. This is the trade-off for bounded state.

**Q: What is the difference between event time and processing time?**  
**A:** Event time is when the event actually occurred (embedded in the data). Processing time is when the stream processes the event. Use event time for correctness.

## State Management

**Q: What is state in Structured Streaming?**  
**A:** State is information maintained across batches for operations like aggregations, joins, and deduplication. State is stored in executors' memory and disk.

**Q: How does Spark handle state failure?**  
**A:** State is checkpointed to reliable storage (HDFS, S3, ADLS). On failure, Spark recovers state from checkpoints and continues processing.

**Q: What is the difference between mapGroupsWithState and flatMapGroupsWithState?**  
**A:** Both allow custom stateful operations. `mapGroupsWithState` outputs one result per group. `flatMapGroupsWithState` can output multiple results per group.

**Q: What is state TTL (Time To Live)?**  
**A:** State TTL automatically removes state that hasn't been updated for a specified duration. Useful for cleaning up inactive groups.

## Exactly-Once Semantics

**Q: What is exactly-once semantics?**  
**A:** Exactly-once semantics ensures each event is processed exactly once, even in the presence of failures. Requires idempotent sinks and checkpointing.

**Q: How does Structured Streaming achieve exactly-once?**  
**A:** Through checkpointing (write-ahead logs), idempotent sinks, and deterministic queries. The combination ensures no duplicates or lost data.

**Q: What is an idempotent sink?**  
**A:** An idempotent sink produces the same result when the same data is written multiple times. Delta Lake, upserts to databases, and deduplication are examples.

**Q: What is the difference between at-least-once and exactly-once?**  
**A:** At-least-once guarantees no data loss but may have duplicates. Exactly-once guarantees no loss and no duplicates but requires more complex logic.

## Checkpointing

**Q: What is checkpointing in Structured Streaming?**  
**A:** Checkpointing saves the query's progress (offsets, state) to reliable storage. It enables recovery from failures and exactly-once semantics.

**Q: Where should checkpoints be stored?**  
**A:** In durable storage like HDFS, S3, ADLS Gen2, or GCS. Do not store on local disk because it may not survive node failures.

**Q: What happens if you change the checkpoint location?**  
**A:** Spark loses track of previous progress and may reprocess data from the beginning or from the last committed offset. Use a stable checkpoint location.

**Q: Can you delete checkpoint files?**  
**A:** Only delete checkpoint files after you are sure the query is stopped and you want to reset progress. Deleting checkpoints may cause reprocessing.

## Triggers

**Q: What is a trigger in Structured Streaming?**  
**A:** A trigger defines when to output results. Options: `Trigger.Once` (process available data once), `Trigger.ProcessingTime(interval)` (micro-batch), `Trigger.Continuous` (low-latency experimental).

**Q: What is the default trigger?**  
**A:** The default is `Trigger.ProcessingTime("0 seconds")`, which means output as soon as a batch is complete (essentially micro-batch mode).

**Q: When should you use Trigger.Once?**  
**A:** Trigger.Once for batch-on-demand processing, such as testing or when you want to process all available data once and stop.

**Q: What is continuous processing trigger?**  
**A:** Continuous processing is an experimental low-latency mode that processes events one by one with sub-second latency. Not all operations are supported.

## Deduplication

**Q: How do you deduplicate events in Structured Streaming?**  
**A:** Use `dropDuplicates()` or `dropDuplicatesWithinWatermark()` with a watermark to remove duplicates based on a key within a time window.

**Q: What is the difference between `dropDuplicates()` and `dropDuplicatesWithinWatermark()`?**  
**A:** `dropDuplicates()` removes duplicates across all data (unbounded state). `dropDuplicatesWithinWatermark()` removes duplicates only within the watermark window (bounded state).

**Q: How do you implement idempotent writes to a sink?**  
**A:** Use upsert operations (e.g., Delta Lake MERGE), deduplicate before writing, or use unique keys and `INSERT ... ON CONFLICT` in databases.

## Joins in Streaming

**Q: Can you join a streaming DataFrame with a static DataFrame?**  
**A:** Yes, stream-static joins are supported. The static DataFrame is broadcasted to all executors and joined with the streaming data.

**Q: Can you join two streaming DataFrames?**  
**A:** Yes, stream-stream joins are supported with watermark on both sides. Both streams must have a watermark on the join key.

**Q: What are the requirements for stream-stream joins?**  
**A:** Both DataFrames must have a watermark on the join key, and the join condition must include the timestamp column. This ensures bounded state.

**Q: How do you handle late data in stream-stream joins?**  
**A:** Watermarks on both sides define the allowed lateness. Late data is dropped if it arrives after the watermark threshold.

## Aggregations

**Q: How do you perform aggregations in Structured Streaming?**  
**A:** Use `groupBy()` and aggregate functions like `count()`, `sum()`, `avg()`. Must use a watermark for stateful aggregations to limit state growth.

**Q: What is the difference between `groupBy()` and `groupBy().agg()`?**  
**A:** `groupBy()` alone is not sufficient; you need `agg()` to specify aggregation functions. `groupBy().agg(F.count("*"), F.sum("value"))`.

**Q: How do you perform windowed aggregations?**  
**A:** Use `groupBy(window("eventTime", "5 minutes"))` to group events into time windows. Combine with watermark to drop old state.

**Q: What is the difference between tumbling and sliding windows?**  
**A:** Tumbling windows are non-overlapping (e.g., 5-minute windows). Sliding windows overlap (e.g., 5-minute window sliding every 1 minute). Use `window()` and `slide()` respectively.

## Monitoring & Debugging

**Q: How do you monitor Structured Streaming queries?**  
**A:** Use `streamingQuery.lastProgress()` to get metrics, `streamingQuery.status()` for status, and the Spark UI (Streaming tab) for visualization.

**Q: What metrics are available in `lastProgress()`?**  
**A:** Batch ID, start time, end time, num input rows, processed rows per second, duration, watermark, state operators, and more.

**Q: How do you debug a streaming query?**  
**A:** Use `df.printSchema()` to check schema, `df.writeStream.format("console").start()` for console output, and check logs for errors.

**Q: What is the difference between `awaitTermination()` and `awaitTermination(timeout)`?**  
**A:** `awaitTermination()` blocks indefinitely until the query stops. `awaitTermination(timeout)` blocks for the specified duration and returns false if not stopped.

## Error Handling

**Q: How do you handle corrupt records in streaming?**  
**A:** Use `option("mode", "PERMISSIVE")` (default) to put corrupt records in a `_corrupt_record` column, or `option("mode", "DROPMALFORMED")` to drop them.

**Q: What happens if a streaming query fails?**  
**A:** The query stops. On restart, Spark recovers from the last checkpoint and continues from where it left off, ensuring exactly-once semantics.

**Q: How do you handle schema evolution in streaming?**  
**A:** Use `option("schemaEvolution", "true")` in Delta Lake, or handle schema changes manually with `from_json()` and `to_json()`.

## Performance Tuning

**Q: How do you optimize streaming query performance?**  
**A:** Use appropriate watermark, tune shuffle partitions, cache frequently used DataFrames, use broadcast joins, and monitor state size.

**Q: What is the impact of large state on performance?**  
**A:** Large state increases memory usage and GC pressure, slows down processing, and can cause out-of-memory errors. Use watermarks and state TTL to limit state.

**Q: How do you reduce state size?**  
**A:** Use watermarks, state TTL, reduce cardinality of groupBy keys, use `mapGroupsWithState` for custom state management, and avoid unnecessary aggregations.

**Q: What is the difference between micro-batch and continuous processing latency?**  
**A:** Micro-batch latency is typically 100ms to seconds. Continuous processing can achieve sub-millisecond latency but has limited operation support.

## Best Practices

**Q: What are some Structured Streaming best practices?**  
**A:** Always use watermarks for stateful operations, store checkpoints in durable storage, use idempotent sinks, monitor query progress, and test with small data first.

**Q: How do you test Structured Streaming queries?**  
**A:** Use rate source or socket source for testing, write to console sink, and use `Trigger.Once` to simulate batch processing.

**Q: What is the difference between `foreach` and `foreachBatch` sinks?**  
**A:** `foreach` processes each row individually (slow). `foreachBatch` processes each batch as a DataFrame (fast and flexible).

**Q: How do you handle backpressure in streaming?**  
**A:** Increase batch size, increase parallelism, optimize the query, or use a message queue with consumer lag monitoring.

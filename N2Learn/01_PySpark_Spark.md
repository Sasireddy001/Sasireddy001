# PySpark / Apache Spark Flash Cards

## Core Concepts

**Q: What is Apache Spark?**  
**A:** Apache Spark is a unified analytics engine for large-scale data processing with built-in modules for SQL, streaming, machine learning, and graph processing. It provides in-memory computing capabilities and is faster than Hadoop MapReduce.

**Q: What is the difference between RDD, DataFrame, and Dataset?**  
**A:** RDD is a low-level, untyped distributed collection. DataFrame is a higher-level, schema-aware abstraction with Catalyst optimization. Dataset is a typed version of DataFrame available in Scala/Java. DataFrames/Datasets are preferred for performance and ease of use.

**Q: What is SparkSession?**  
**A:** SparkSession is the entry point for Spark functionality since Spark 2.0. It combines SparkContext, SQLContext, HiveContext, and StreamingContext into a single interface. Use `spark = SparkSession.builder.appName("...").getOrCreate()`.

**Q: What are the different deployment modes in Spark?**  
**A:** Client mode (driver runs on the machine submitting the job), Cluster mode (driver runs inside the cluster), Local mode (for testing), and Standalone/YARN/Mesos/Kubernetes cluster managers.

## Transformations & Actions

**Q: What is the difference between transformations and actions?**  
**A:** Transformations are lazy operations that build a logical plan (e.g., `map`, `filter`, `groupBy`). Actions trigger execution and return results (e.g., `collect`, `count`, `write`).

**Q: What is a narrow transformation?**  
**A:** A transformation that does not require shuffling data between partitions, such as `map`, `filter`, `union`. Data stays within the same partition.

**Q: What is a wide transformation?**  
**A:** A transformation that requires shuffling data across partitions, such as `groupBy`, `join`, `reduceByKey`, `repartition`. These are more expensive operations.

**Q: What is the difference between `map()` and `mapPartitions()`?**  
**A:** `map()` applies a function to each element individually. `mapPartitions()` applies a function to each partition as a whole, which can be more efficient when the function has high initialization overhead (e.g., database connections).

**Q: What is `flatMap()`?**  
**A:** `flatMap()` returns zero, one, or many output elements per input element by flattening the result. Useful for splitting strings or generating multiple records from one.

## Partitioning & Performance

**Q: What is partitioning in Spark?**  
**A:** Partitioning divides data into smaller chunks that can be processed in parallel. Each partition is processed by a task on an executor. Proper partitioning improves performance.

**Q: What is the difference between `repartition()` and `coalesce()`?**  
**A:** `repartition()` performs a full shuffle to increase or decrease partitions. `coalesce()` reduces partitions without a full shuffle, so it's cheaper but can lead to skewed data. Use `coalesce()` when decreasing partitions.

**Q: What is a partitioner?**  
**A:** A partitioner determines how data is distributed across partitions during shuffles. Spark provides `HashPartitioner` (default) and `RangePartitioner`. Custom partitioners can be implemented.

**Q: What is data skew and how do you handle it?**  
**A:** Data skew occurs when some partitions have significantly more data than others, causing some tasks to run much slower. Solutions: salting keys, broadcasting smaller DataFrames, using AQE (Adaptive Query Execution), or implementing custom partitioners.

**Q: What is Adaptive Query Execution (AQE)?**  
**A:** AQE optimizes queries at runtime in Spark 3.x: coalescing shuffle partitions, converting sort-merge join to broadcast join, handling skew joins, and optimizing query plans based on runtime statistics.

## Caching & Persistence

**Q: What is the difference between `cache()` and `persist()`?**  
**A:** `cache()` stores data in memory only (equivalent to `persist(StorageLevel.MEMORY_ONLY)`). `persist()` lets you choose storage levels: MEMORY_ONLY, MEMORY_AND_DISK, DISK_ONLY, MEMORY_ONLY_SER, etc.

**Q: When should you use caching?**  
**A:** When a DataFrame is reused multiple times in an action, such as iterative ML algorithms or when joining the same DataFrame multiple times. Avoid caching very large DataFrames that don't fit in memory.

**Q: What is the difference between `unpersist()` and `cache()`?**  
**A:** `cache()` keeps data in memory. `unpersist()` removes cached data from memory/disk to free up resources. Use `unpersist()` when you no longer need the cached DataFrame.

**Q: What is checkpointing?**  
**A:** Checkpointing truncates the lineage of an RDD/DataFrame by saving it to reliable storage (HDFS, S3). Useful for long lineages in streaming jobs or when you want to cut the dependency graph for fault tolerance.

## Joins

**Q: What are the different join types in Spark?**  
**A:** Inner, outer, left, right, left semi, left anti, and cross joins. Each behaves differently based on matching and non-matching records.

**Q: What is the difference between broadcast join and sort-merge join?**  
**A:** Broadcast join sends the smaller DataFrame to all executors and performs map-side joins (fast for small datasets). Sort-merge join sorts both sides and merges them (default for large datasets). Spark automatically chooses based on size.

**Q: How do you optimize join performance?**  
**A:** Use broadcast hints for small DataFrames, ensure join keys are partitioned properly, cache frequently joined DataFrames, use AQE, and consider bucketing for large joins.

**Q: What is a skewed join and how does Spark handle it?**  
**A:** A skewed join occurs when one partition has many more records than others. Spark 3.x AQE can detect and handle skewed joins by splitting the large partition and processing it in multiple tasks.

## UDFs & Performance

**Q: What is a UDF (User Defined Function)?**  
**A:** A UDF allows you to define custom logic in Python/Scala/Java and apply it to DataFrame columns. Python UDFs are slower than native Spark functions due to serialization overhead.

**Q: How can you improve UDF performance?**  
**A:** Use Pandas UDFs (vectorized UDFs) which use Apache Arrow for zero-copy serialization, or use native Spark functions when possible. Pandas UDFs are 10-100x faster than regular Python UDFs.

**Q: What is a Pandas UDF?**  
**A:** A Pandas UDF uses Apache Arrow to transfer data between JVM and Python, allowing vectorized operations. Define with `@pandas_udf` annotation and return a pandas Series.

**Q: What is the difference between `udf()` and `pandas_udf()`?**  
**A:** `udf()` processes one row at a time (slow). `pandas_udf()` processes batches of rows as pandas Series (fast due to vectorization and Arrow).

## Window Functions

**Q: What are window functions in Spark?**  
**A:** Window functions perform calculations across a set of rows related to the current row without reducing the number of rows. Examples: `row_number()`, `rank()`, `dense_rank()`, `lag()`, `lead()`, `sum()` over window.

**Q: What is the syntax for window functions?**  
**A:** `from pyspark.sql.window import Window; windowSpec = Window.partitionBy("column").orderBy("column"); df.withColumn("rank", F.row_number().over(windowSpec))`

**Q: What is the difference between `rank()` and `dense_rank()`?**  
**A:** `rank()` leaves gaps in ranking when there are ties. `dense_rank()` does not leave gaps. For values [10, 10, 8]: rank() = [1, 1, 3]; dense_rank() = [1, 1, 2].

**Q: What is the difference between `row_number()` and `rank()`?**  
**A:** `row_number()` assigns unique sequential numbers to each row regardless of ties. `rank()` assigns the same rank to tied values.

## File Formats & Compression

**Q: What are common file formats in Spark?**  
**A:** Parquet, ORC, Avro, JSON, CSV, Delta Lake. Parquet and ORC are columnar and optimized for performance.

**Q: Why is Parquet preferred for Spark?**  
**A:** Columnar storage allows reading only needed columns, efficient compression, predicate pushdown, and better performance for analytical queries.

**Q: What is the difference between Parquet and ORC?**  
**A:** Both are columnar formats. Parquet is more widely used and has better compression. ORC is optimized for Hive and has better indexing features.

**Q: What compression codecs does Spark support?**  
**A:** Snappy (default, fast), Gzip (better compression but slower), LZO, Zstandard (Zstd), Brotli, LZ4. Choose based on speed vs compression ratio.

## Error Handling & Debugging

**Q: How do you handle errors in PySpark?**  
**A:** Use try-except blocks in UDFs, handle null values with `F.coalesce()` or `F.when()`, and use `df.printSchema()` and `df.show()` for debugging.

**Q: What is the difference between `NaN` and `null` in Spark?**  
**A:** `NaN` is a floating-point special value for invalid numeric operations. `null` represents missing data. Use `F.isnan()` for NaN and `F.isnull()` for null.

**Q: How do you debug Spark jobs?**  
**A:** Use Spark UI (4040 port), check executor logs, use `df.explain()` to see the query plan, and use `df.count()` to force execution for testing.

**Q: What is the difference between `printSchema()` and `explain()`?**  
**A:** `printSchema()` shows the DataFrame schema (column names and types). `explain()` shows the logical and physical query plans.

## Spark SQL

**Q: What is Spark SQL?**  
**A:** Spark SQL is a module for working with structured data using SQL queries and DataFrame API. It provides a unified interface for batch and streaming data.

**Q: What is the difference between DataFrame API and Spark SQL?**  
**A:** DataFrame API is programmatic (Python/Scala/Java). Spark SQL uses SQL syntax. Both compile to the same logical plan and have the same performance.

**Q: How do you register a DataFrame as a temporary view?**  
**A:** `df.createOrReplaceTempView("table_name")` or `df.createOrReplaceGlobalTempView("global_table_name")`. Temporary views are session-scoped; global temp views are system-wide.

**Q: What is the difference between `createOrReplaceTempView()` and `createOrReplaceGlobalTempView()`?**  
**A:** Temp views are session-scoped and dropped when the session ends. Global temp views are system-scoped and persist across sessions until explicitly dropped.

## Spark Configurations

**Q: What is `spark.sql.shuffle.partitions`?**  
**A:** Controls the number of partitions after a shuffle operation. Default is 200. Increase for large datasets, decrease for small datasets to avoid too many small files.

**Q: What is `spark.executor.memory`?**  
**A:** Amount of memory to use per executor. Set based on cluster resources and data size. Formula: `executor memory = (total cluster memory / number of executors) - memory overhead`.

**Q: What is `spark.driver.memory`?**  
**A:** Amount of memory allocated to the Spark driver. Set based on data collected to the driver (e.g., `collect()` operations). Default is 1g.

**Q: What is `spark.sql.adaptive.enabled`?**  
**A:** Enables Adaptive Query Execution (AQE) which optimizes queries at runtime. Default is true in Spark 3.x.

## Spark Streaming

**Q: What is the difference between Spark Streaming (DStream) and Structured Streaming?**  
**A:** DStream is the older micro-batch API based on RDDs. Structured Streaming is the newer API based on DataFrames/Datasets with better performance and features. Use Structured Streaming.

**Q: What is a micro-batch in Spark Streaming?**  
**A:** Spark Streaming processes data in small batches (e.g., every 1 second, 5 seconds). Each batch is treated as a DataFrame and processed using the same engine as batch.

**Q: What is continuous processing in Structured Streaming?**  
**A:** Continuous processing is an experimental low-latency mode that processes events one by one with sub-second latency, instead of micro-batches. Not all operations are supported.

**Q: What is the difference between `append`, `complete`, and `update` output modes?**  
**A:** Append: only new rows are written. Complete: entire result table is written each time. Update: changed rows are written. Choose based on use case.

## Spark on Kubernetes

**Q: How do you run Spark on Kubernetes?**  
**A:** Use `spark-submit --master k8s://...` or the Spark Operator. Submit jobs as Kubernetes pods. Executors run as pods in the cluster.

**Q: What is the Spark Operator?**  
**A:** The Spark Operator is a Kubernetes operator that manages Spark applications using custom resources (`SparkApplication`). It provides better integration with Kubernetes ecosystem.

**Q: What are the benefits of running Spark on Kubernetes?**  
**A:** Dynamic resource allocation, isolation, better resource utilization, integration with Kubernetes ecosystem, and no need for a separate Spark cluster manager.

## Best Practices

**Q: What are some Spark performance best practices?**  
**A:** Use appropriate partitioning, cache reused DataFrames, avoid shuffles when possible, use broadcast joins, use AQE, use columnar formats, avoid UDFs, and use Pandas UDFs when needed.

**Q: How do you handle large datasets that don't fit in memory?**  
**A:** Use `persist(StorageLevel.MEMORY_AND_DISK)`, increase executor memory, use more partitions, or use disk-based operations. Consider using Spark on Kubernetes with dynamic scaling.

**Q: What is the difference between `collect()` and `take()`?**  
**A:** `collect()` returns all rows as a list to the driver (use only for small datasets). `take(n)` returns the first n rows (safer for large datasets).

**Q: How do you monitor Spark jobs?**  
**A:** Use Spark UI (4040 port), Spark History Server, metrics (Prometheus, Grafana), and logs. Monitor executor memory, GC time, shuffle read/write, and task duration.

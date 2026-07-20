# Kafka / Event Streaming Flash Cards

## Core Concepts

**Q: What is Apache Kafka?**  
**A:** Apache Kafka is a distributed event streaming platform for high-throughput, low-latency, and fault-tolerant data pipelines. It decouples producers and consumers using topics.

**Q: What are the key components of Kafka?**  
**A:** Producers (write events), Consumers (read events), Topics (logical streams), Partitions (sharded logs), Brokers (Kafka servers), and Zookeeper/KRaft (cluster coordination).

**Q: What is a Kafka topic?**  
**A:** A topic is a logical channel or category to which events are published. Topics are split into partitions for scalability and parallelism.

**Q: What is a Kafka partition?**  
**A:** A partition is an ordered, immutable sequence of events. Each partition is stored on one or more brokers and allows parallel consumption.

**Q: What is an offset in Kafka?**  
**A:** An offset is a unique identifier for each event within a partition. Consumers track offsets to know where they are in the stream.

## Producers & Consumers

**Q: What is a Kafka producer?**  
**A:** A producer is an application that publishes events to Kafka topics. It can send events synchronously (wait for acknowledgment) or asynchronously (fire-and-forget).

**Q: What is a Kafka consumer?**  
**A:** A consumer is an application that reads events from Kafka topics. Consumers can be part of a consumer group for parallel processing.

**Q: What is a consumer group?**  
**A:** A consumer group is a set of consumers that work together to consume a topic. Each partition is assigned to one consumer in the group, enabling load balancing.

**Q: What is consumer group rebalancing?**  
**A:** Rebalancing occurs when consumers join or leave a group. Kafka reassigns partitions among active consumers to ensure each partition is consumed by exactly one consumer.

**Q: What is the difference between `assign()` and `subscribe()` in consumers?**  
**A:** `assign()` manually assigns partitions to a consumer. `subscribe()` joins a consumer group and lets Kafka assign partitions automatically.

## Message Keys & Ordering

**Q: What is the role of message keys in Kafka?**  
**A:** Keys are used to determine which partition an event goes to (via hashing). Events with the same key go to the same partition, preserving order for that key.

**Q: Does Kafka guarantee global ordering?**  
**A:** No, Kafka guarantees ordering only within a partition. Across partitions, ordering is not guaranteed. Use a single partition if global ordering is required.

**Q: What happens if you don't provide a key when sending an event?**  
**A:** Kafka uses a round-robin strategy to assign the event to a partition, which may result in out-of-order delivery for the same logical entity.

**Q: How do you ensure exactly-once processing with Kafka?**  
**A:** Use idempotent producers (enabled by default in newer versions), transactional writes (beginTransaction, commitTransaction), and idempotent consumers (deduplicate based on keys).

## Kafka Configuration

**Q: What is `acks` in Kafka producer configuration?**  
**A:** `acks` controls how many broker acknowledgments the producer requires. `acks=0` (no acknowledgment), `acks=1` (leader acknowledgment), `acks=all` (leader and replicas acknowledgment).

**Q: What is the difference between `acks=1` and `acks=all`?**  
**A:** `acks=1` waits for the leader to acknowledge (fast but less durable). `acks=all` waits for all replicas to acknowledge (slower but more durable).

**Q: What is `retries` in Kafka producer configuration?**  
**A:** `retries` specifies how many times the producer retries sending a message on failure. Default is 2147483647 (effectively infinite).

**Q: What is `enable.idempotence` in Kafka producer?**  
**A:** When enabled, the producer ensures exactly-once delivery to a partition even on retries. It uses a sequence number to detect duplicates.

**Q: What is `auto.offset.reset` in Kafka consumer configuration?**  
**A:** `auto.offset.reset` determines what to do when no initial offset exists: `earliest` (start from beginning), `latest` (start from newest), or `none` (throw exception).

## Kafka Retention

**Q: What is Kafka retention?**  
**A:** Retention is the policy for how long Kafka keeps events. Configured by time (`retention.ms`), size (`retention.bytes`), or log compaction.

**Q: What is log compaction in Kafka?**  
**A:** Log compaction keeps only the latest value for each key. Older events with the same key are removed, useful for changelog topics and state stores.

**Q: How do you configure retention time?**  
**A:** Set `retention.ms` at the topic level: `kafka-configs --alter --entity-type topics --entity-name my-topic --add-config retention.ms=86400000`.

**Q: What happens when retention expires?**  
**A:** Kafka deletes old log segments to free disk space. Consumers that lag beyond retention lose data and may need to reset offsets.

## Kafka Connect

**Q: What is Kafka Connect?**  
**A:** Kafka Connect is a tool for scalably and reliably streaming data between Kafka and other systems (databases, file systems, search indexes, etc.).

**Q: What is a source connector in Kafka Connect?**  
**A:** A source connector reads data from an external system and writes it to Kafka. Examples: JDBC source, file source, Elasticsearch source.

**Q: What is a sink connector in Kafka Connect?**  
**A:** A sink connector reads data from Kafka and writes it to an external system. Examples: JDBC sink, HDFS sink, Elasticsearch sink.

**Q: How do you deploy Kafka Connect?**  
**A:** Deploy as a standalone process (single JVM) or distributed cluster (multiple workers). Distributed mode provides scalability and fault tolerance.

## Kafka Streams

**Q: What is Kafka Streams?**  
**A:** Kafka Streams is a client library for building stream processing applications using Kafka. It provides high-level DSL and low-level processor API.

**Q: What is a stream-table duality in Kafka Streams?**  
**A:** A stream (KStream) represents an event log. A table (KTable) represents the latest state for each key. You can convert between them.

**Q: What is a topology in Kafka Streams?**  
**A:** A topology is the processing graph defined by the application, including sources, processors, and sinks. It is built using the DSL or processor API.

**Q: How does Kafka Streams handle state?**  
**A:** State is stored in local state stores (RocksDB) and backed up to Kafka changelog topics for fault tolerance. State is restored on restart.

## Kafka vs Alternatives

**Q: How does Kafka compare to RabbitMQ?**  
**A:** Kafka is designed for high-throughput, persistent event streaming. RabbitMQ is a traditional message broker for work queues and point-to-point messaging.

**Q: How does Kafka compare to AWS Kinesis?**  
**A:** Kinesis is a managed streaming service on AWS. Kafka is open-source and self-managed. Both support similar use cases but have different operational models.

**Q: How does Kafka compare to Azure Event Hubs?**  
**A:** Event Hubs is a managed event streaming service on Azure. Kafka is open-source. Event Hubs is Kafka-compatible for many operations.

**Q: How does Kafka compare to Apache Pulsar?****  
**A:** Pulsar is a multi-tenant, geo-distributed messaging system with built-in compute (Functions). Kafka is simpler but requires external tools for multi-tenancy and geo-replication.

## Kafka Security

**Q: What security features does Kafka provide?**  
**A:** Authentication (SASL, SSL), authorization (ACLs), encryption (SSL/TLS), and audit logging.

**Q: What is SASL in Kafka?**  
**A:** SASL (Simple Authentication and Security Layer) provides authentication mechanisms like PLAIN, SCRAM, GSSAPI (Kerberos), and OAuth2.

**Q: What is SSL/TLS in Kafka?**  
**A:** SSL/TLS encrypts data in transit between clients and brokers. It can also be used for client authentication (mutual TLS).

**Q: What are ACLs in Kafka?**  
**A:** ACLs (Access Control Lists) define who can perform what operations on which resources (topics, consumer groups, etc.).

## Kafka Monitoring

**Q: How do you monitor Kafka?**  
**A:** Use JMX metrics, tools like Kafka Manager, Burrow, Confluent Control Center, or Prometheus/Grafana dashboards.

**Q: What are important Kafka metrics to monitor?**  
**A:** Under-replicated partitions, offline partitions, consumer lag, broker throughput, disk usage, and error rates.

**Q: What is consumer lag?**  
**A:** Consumer lag is the difference between the latest offset in a partition and the consumer's current offset. High lag indicates the consumer is falling behind.

**Q: How do you measure consumer lag?**  
**A:** Use Burrow, Kafka Consumer Lag Exporter, or manually compare offsets via the consumer group API.

## Kafka Performance

**Q: How do you improve Kafka throughput?**  
**A:** Increase batch size, increase linger.ms (wait longer to batch), use compression, increase producer concurrency, and tune broker settings.

**Q: What is the impact of compression in Kafka?**  
**A:** Compression reduces network bandwidth and disk usage at the cost of CPU. Supported codecs: gzip, snappy, lz4, zstd.

**Q: What is linger.ms in Kafka producer?**  
**A:** linger.ms controls how long the producer waits to batch messages before sending. Higher values improve throughput but increase latency.

**Q: How do you reduce Kafka latency?**  
**A:** Decrease linger.ms, decrease batch size, use snappy compression (faster than gzip), and reduce network hops.

## Kafka on Kubernetes

**Q: How do you deploy Kafka on Kubernetes?**  
**A:** Use operators like Strimzi, Confluent for Kubernetes, or Kafka Operator. These manage Kafka clusters, topics, and users as Kubernetes resources.

**Q: What is Strimzi?**  
**A:** Strimzi is a Kubernetes operator for running Apache Kafka on Kubernetes. It provides custom resources for Kafka clusters, topics, and users.

**Q: What are the challenges of running Kafka on Kubernetes?**  
**A:** StatefulSet management, persistent storage, network policies, and ensuring low latency between brokers and clients.

## Kafka Best Practices

**Q: What are some Kafka best practices?**  
**A:** Use appropriate partition count, monitor consumer lag, set sensible retention, use compression, enable idempotence, and secure with ACLs.

**Q: How do you choose the number of partitions?**  
**A:** Based on throughput requirements and consumer parallelism. More partitions increase parallelism but also increase overhead. Start with a multiple of the number of consumers.

**Q: How do you handle backpressure in Kafka consumers?**  
**A:** Increase consumer parallelism (more consumers), tune `fetch.min.bytes` and `max.poll.records`, or use dynamic scaling in Kubernetes.

**Q: What is the difference between at-least-once and exactly-once in Kafka?**  
**A:** At-least-once ensures no data loss but may have duplicates. Exactly-once ensures no loss and no duplicates but requires idempotent producers and consumers.

## Kafka with Spark

**Q: How do you read from Kafka in Spark?**  
**A:** Use `spark.readStream.format("kafka").option("kafka.bootstrap.servers", "...").option("subscribe", "topic").load()`.

**Q: How do you write to Kafka in Spark?**  
**A:** Use `df.writeStream.format("kafka").option("kafka.bootstrap.servers", "...").option("topic", "topic").start()`.

**Q: What are the key considerations for Spark-Kafka integration?**  
**A:** Use appropriate offsets (earliest/latest), handle schema evolution, monitor consumer lag, and tune batch size for throughput.

**Q: How do you handle schema evolution in Kafka with Spark?**  
**A:** Use schema registry (Confluent Schema Registry) or handle schema changes manually with `from_json()` and `to_json()`.

## Kafka with Delta Lake

**Q: How do you integrate Kafka with Delta Lake?**  
**A:** Read from Kafka with Structured Streaming, process the data, and write to Delta Lake. Use checkpointing for exactly-once semantics.

**Q: What are the benefits of using Delta Lake as a Kafka sink?**  
**A:** ACID transactions, time travel for debugging, schema enforcement, and efficient query performance for downstream analytics.

**Q: How do you handle late data in Kafka-to-Delta pipelines?**  
**A:** Use watermark in Structured Streaming to drop late data, or use Delta Lake's MERGE to handle upserts for late-arriving events.

## Kafka Troubleshooting

**Q: What do you do if a Kafka broker is down?**  
**A:** Check logs, ensure Zookeeper/KRaft is running, verify network connectivity, and restart the broker if needed. The cluster should remain available if replication is configured.

**Q: What do you do if consumers are not consuming data?**  
**A:** Check consumer group status, offsets, lag, and logs. Ensure the consumer is subscribed to the correct topic and partitions.

**Q: What do you do if producers are failing?**  
**A:** Check broker availability, network connectivity, configuration (acks, retries), and producer logs for errors.

**Q: What is a "leader not available" error?**  
**A:** This occurs when the leader partition is not available, possibly due to broker failure or under-replicated partitions. Check broker status and replication.

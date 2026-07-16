# Hi, I'm Sasidhar Mopuru

Data Engineer building scalable streaming pipelines and lakehouse systems.

## About Me

I specialize in end-to-end data engineering with a focus on:

- Event streaming with **Apache Kafka**
- Distributed processing with **Apache Spark / PySpark**
- Lakehouse architectures with **Delta Lake** and **Databricks**
- Reliable, testable pipelines with **CI/CD**

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?logo=apachespark&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?logo=apachekafka&logoColor=white)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-00ADD8?logo=delta&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?logo=databricks&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?logo=githubactions&logoColor=white)

## Featured Project: Kafka -> PySpark -> Delta Lake

A production-style streaming pipeline demonstrating **Kafka ingestion**,
**PySpark Structured Streaming** transformations, and **Delta Lake** storage on
Databricks.

- Repository: [Sasireddy001/Kafka-pyspark-delta-pipeline](https://github.com/Sasireddy001/Kafka-pyspark-delta-pipeline)
- Includes automated **pytest** tests, **GitHub Actions** CI, a sample data
generator, and a performance benchmark.

```mermaid
graph LR
    A[Apache Kafka] -->|readStream| B[PySpark Structured Streaming]
    B --> C[JSON Parsing & Schema Enforcement]
    C --> D[Add Partitions & Deduplicate]
    D -->|writeStream| E[Delta Lake Bronze Table]
```

## GitHub Stats

![GitHub stats](https://github-readme-stats.vercel.app/api?username=Sasireddy001&show_icons=true&theme=default)
![Top languages](https://github-readme-stats.vercel.app/api/top-langs/?username=Sasireddy001&layout=compact)

## Connect

- Email: sasidharmopuru@gmail.com
- GitHub: [@Sasireddy001](https://github.com/Sasireddy001)

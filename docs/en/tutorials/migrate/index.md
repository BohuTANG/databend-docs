---
title: Data Migration to Databend
---

# Data Migration to Databend

Select your source database and migration requirements to find the most suitable migration method to Databend.

## MySQL to Databend

### When to Choose Real-time Migration (CDC)

> **Recommendation**: For real-time migration, we recommend **Debezium** as the default choice.

- You need continuous data synchronization with minimal latency
- You need to capture all data changes (inserts, updates, deletes)

| Tool | Capabilities | Best For | Choose When |
|------|------------|----------|-------------|
| [Debezium](/tutorials/migrate/migrating-from-mysql-with-debezium) | CDC, Full Load | Capturing row-level changes with minimal latency | You need complete CDC with all DML operations (INSERT/UPDATE/DELETE); You want binlog-based replication for minimal impact on source database |
| [Flink CDC](/tutorials/migrate/migrating-from-mysql-with-flink-cdc) | CDC, Full Load, Transformation | Complex ETL with real-time transformation | You need to filter or transform data during migration; You need a scalable processing framework; You want SQL-based transformation capabilities |
| [Kafka Connect](/tutorials/migrate/migrating-from-mysql-with-kafka-connect) | CDC, Incremental, Full Load | Existing Kafka infrastructure | You already use Kafka; You need simple configuration; You can use timestamp or auto-increment columns for incremental sync |

### When to Choose Batch Migration

> **Recommendation**: For batch migration, we recommend **db-archiver** as the default choice.

- You need one-time or scheduled data transfers
- You have large volumes of historical data to migrate
- You don't need real-time synchronization

| Tool | Capabilities | Best For | Choose When |
|------|------------|----------|-------------|
| [db-archiver](/tutorials/migrate/migrating-from-mysql-with-db-archiver) | Full Load, Incremental | Efficient historical data archiving | You have time-partitioned data; You need to archive historical data; You want a lightweight, focused tool |
| [DataX](/tutorials/migrate/migrating-from-mysql-with-datax) | Full Load, Incremental | High-performance large dataset transfers | You need high throughput for large datasets; You want parallel processing capabilities; You need a mature, widely-used tool |
| [Addax](/tutorials/migrate/migrating-from-mysql-with-addax) | Full Load, Incremental | Enhanced DataX with better performance | You need better error handling than DataX; You want improved monitoring capabilities; You need more recent updates and features |

## Snowflake to Databend

### When to Choose Snowflake Migration

| Tool | Capabilities | Best For | Choose When |
|------|------------|----------|-------------|
| [Snowflake Migration](/tutorials/migrate/migrating-from-snowflake) | Full Load | Complete data warehouse transition | You need to migrate your entire Snowflake warehouse; You want to use Parquet format for efficient data transfer; You need to maintain schema compatibility between systems |

## Related Topics

- [Loading Data](/guides/load-data/)
- [Unloading Data](/guides/unload-data/)

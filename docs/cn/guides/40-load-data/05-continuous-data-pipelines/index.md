---
title: 持续数据管道
---

## 数据管道简介

数据管道可以自动将来自不同来源的数据移动和更改到 Databend 中。它们确保数据流畅流动，对于快速、持续地处理和分析数据至关重要。

在持续数据管道中，一种名为 **变更数据捕获 (CDC)** 的特殊功能起着关键作用。借助 Databend，CDC 变得简单高效，只需通过 Streams 和 Tasks 执行几个简单的命令即可。

## 了解变更数据捕获 (CDC)

CDC 是一种流对象捕获应用于数据库表的插入、更新和删除的过程。它包括有关每次更改的元数据，从而可以根据修改后的数据执行操作。Databend 中的 CDC 在源表中跟踪行级别的更改，创建一个“更改表”，反映两个事务时间点之间的修改。

## 使用变更数据捕获 (CDC) 的优势

1. **快速实时数据加载**：简化了从事务数据库加载实时数据的过程，几乎在几秒钟内即可完成。
2. **不影响原始数据**：使用安全，因为它不会损坏数据或数据来源的系统。
3. **克服批量 ETL 的局限性**：超越了传统的批量 ETL 方法，后者速度较慢，对于持续数据更新效果较差。

## Databend 持续数据管道的主要特性

Databend 通过以下特性增强了持续数据管道：

- **持续数据跟踪和转换**：支持实时跟踪和转换数据。[了解更多关于通过 Streams 跟踪和转换数据的信息](./01-stream.md)。

- **周期性 Tasks**：支持调度和管理周期性数据处理任务，以确保数据管道的效率和可靠性。此功能目前为私有预览版。
---
title: SHOW METRICS
---
import FunctionDescription from '@site/src/components/FunctionDescription';

<FunctionDescription description="Introduced or updated: v1.2.190"/>

显示 [系统指标](../../00-sql-reference/31-system-tables/system-metrics.md) 列表。

## 语法

```sql
SHOW METRICS [LIKE '<pattern>' | WHERE <expr>] | [LIMIT <limit>]
```

## 示例

```sql
SHOW METRICS;
+-----------------------------------+---------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| metric                            | kind    | labels | value                                                                                                                                                                                                                                                                    |
+-----------------------------------+---------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| session_connect_numbers           | counter | {}     | 1.0                                                                                                                                                                                                                                                                      |
| optimizer_optimize_usedtime_sum   | untyped | {}     | 0.000438079                                                                                                                                                                                                                                                              |
| optimizer_optimize_usedtime_count | untyped | {}     | 1.0                                                                                                                                                                                                                                                                      |
| parser_parse_usedtime_sum         | untyped | {}     | 0.000254307                                                                                                                                                                                                                                                              |
| parser_parse_usedtime_count       | untyped | {}     | 2.0                                                                                                                                                                                                                                                                      |
| optimizer_optimize_usedtime       | summary | {}     | [{"quantile":0.0,"count":0.000438079},{"quantile":0.5,"count":0.000438079},{"quantile":0.9,"count":0.000438079},{"quantile":0.95,"count":0.000438079},{"quantile":0.99,"count":0.000438079},{"quantile":0.999,"count":0.000438079},{"quantile":1.0,"count":0.000438079}] |
| parser_parse_usedtime             | summary | {}     | [{"quantile":0.0,"count":0.000107972},{"quantile":0.5,"count":0.000107972},{"quantile":0.9,"count":0.000107972},{"quantile":0.95,"count":0.000107972},{"quantile":0.99,"count":0.000107972},{"quantile":0.999,"count":0.000107972},{"quantile":1.0,"count":0.000107972}] |
+-----------------------------------+---------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
```
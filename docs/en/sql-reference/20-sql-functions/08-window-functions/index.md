---
title: 'Window Functions'
---

## Overview 

Window functions perform calculations across a set of related rows while returning one result per input row. Unlike aggregate functions, window functions don't collapse rows into a single output.

**Key characteristics:**
- Operate on a "window" of rows related to the current row
- Return one value per input row (no grouping/collapsing)
- Can access values from other rows in the window
- Support partitioning and ordering for flexible calculations

## Window Function Categories

Databend supports two main categories of window functions:

### 1. Dedicated Window Functions

These functions are specifically designed for window operations.

**Ranking Functions:**

| Function | Description | Ties Handling | Example Output |
|----------|-------------|---------------|----------------|
| [ROW_NUMBER](row-number.md) | Sequential numbering | Always unique | `1, 2, 3, 4, 5` |
| [RANK](rank.md) | Ranking with gaps | Same rank, gaps after | `1, 2, 2, 4, 5` |
| [DENSE_RANK](dense-rank.md) | Ranking without gaps | Same rank, no gaps | `1, 2, 2, 3, 4` |

**Distribution Functions:**

| Function | Description | Range | Example Output |
|----------|-------------|-------|----------------|
| [PERCENT_RANK](percent_rank.md) | Relative rank as percentage | 0.0 to 1.0 | `0.0, 0.25, 0.5, 0.75, 1.0` |
| [CUME_DIST](cume-dist.md) | Cumulative distribution | 0.0 to 1.0 | `0.2, 0.4, 0.6, 0.8, 1.0` |
| [NTILE](ntile.md) | Divide into N buckets | 1 to N | `1, 1, 2, 2, 3, 3` |

**Value Access Functions:**

| Function | Description | Use Case |
|----------|-------------|----------|
| [FIRST_VALUE](first-value.md) | First value in window | Get highest/earliest value |
| [LAST_VALUE](last-value.md) | Last value in window | Get lowest/latest value |
| [NTH_VALUE](nth-value.md) | Nth value in window | Get specific positioned value |
| [LAG](lag.md) | Previous row value | Compare with previous |
| [LEAD](lead.md) | Next row value | Compare with next |

**Aliases:**

| Function | Alias For |
|----------|----------|
| [FIRST](first.md) | FIRST_VALUE |
| [LAST](last.md) | LAST_VALUE |

### 2. Aggregate Functions Used as Window Functions

These are standard aggregate functions that can be used with the OVER clause to perform window operations.

| Function | Description | Window Frame Support | Example |
|----------|-------------|---------------------|---------|  
| [SUM](../07-aggregate-functions/aggregate-sum.md) | Calculates sum over window | ✓ | `SUM(sales) OVER (PARTITION BY region ORDER BY date)` |
| [AVG](../07-aggregate-functions/aggregate-avg.md) | Calculates average over window | ✓ | `AVG(score) OVER (ORDER BY id ROWS BETWEEN 2 PRECEDING AND CURRENT ROW)` |
| [COUNT](../07-aggregate-functions/aggregate-count.md) | Counts rows over window | ✓ | `COUNT(*) OVER (PARTITION BY department)` |
| [MIN](../07-aggregate-functions/aggregate-min.md) | Returns minimum value in window | ✓ | `MIN(price) OVER (PARTITION BY category)` |
| [MAX](../07-aggregate-functions/aggregate-max.md) | Returns maximum value in window | ✓ | `MAX(price) OVER (PARTITION BY category)` |
| [ARRAY_AGG](../07-aggregate-functions/aggregate-array-agg.md) | Collects values into array | | `ARRAY_AGG(product) OVER (PARTITION BY category)` |
| [STDDEV_POP](../07-aggregate-functions/aggregate-stddev-pop.md) | Population standard deviation | ✓ | `STDDEV_POP(value) OVER (PARTITION BY group)` |
| [STDDEV_SAMP](../07-aggregate-functions/aggregate-stddev-samp.md) | Sample standard deviation | ✓ | `STDDEV_SAMP(value) OVER (PARTITION BY group)` |
| [MEDIAN](../07-aggregate-functions/aggregate-median.md) | Median value | ✓ | `MEDIAN(response_time) OVER (PARTITION BY server)` |

**Conditional Variants**

| Function | Description | Window Frame Support | Example |
|----------|-------------|---------------------|---------|  
| [COUNT_IF](../07-aggregate-functions/aggregate-count-if.md) | Conditional count | ✓ | `COUNT_IF(status = 'complete') OVER (PARTITION BY dept)` |
| [SUM_IF](../07-aggregate-functions/aggregate-sum-if.md) | Conditional sum | ✓ | `SUM_IF(amount, status = 'paid') OVER (PARTITION BY customer)` |
| [AVG_IF](../07-aggregate-functions/aggregate-avg-if.md) | Conditional average | ✓ | `AVG_IF(score, passed = true) OVER (PARTITION BY class)` |
| [MIN_IF](../07-aggregate-functions/aggregate-min-if.md) | Conditional minimum | ✓ | `MIN_IF(temp, location = 'outside') OVER (PARTITION BY day)` |
| [MAX_IF](../07-aggregate-functions/aggregate-max-if.md) | Conditional maximum | ✓ | `MAX_IF(speed, vehicle = 'car') OVER (PARTITION BY test)` |

## Basic Syntax

All window functions follow this pattern:

```sql
FUNCTION() OVER (
    [ PARTITION BY column ]
    [ ORDER BY column ]
    [ window_frame ]
)
```

- **PARTITION BY**: Divides data into groups
- **ORDER BY**: Sorts rows within each partition  
- **window_frame**: Defines which rows to include (optional)


## Common Use Cases

- **Ranking**: Create leaderboards and top-N lists
- **Analytics**: Calculate running totals, moving averages, percentiles
- **Comparison**: Compare current vs previous/next values
- **Grouping**: Divide data into buckets without losing detail

For detailed syntax and examples, see individual function documentation above.

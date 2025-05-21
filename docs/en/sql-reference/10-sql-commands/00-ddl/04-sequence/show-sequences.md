---
title: SHOW SEQUENCES
sidebar_position: 3
---

Returns a list of the created sequences.

## Syntax

```sql
SHOW SEQUENCES [ LIKE '<pattern>' | WHERE <expr> ]
```

## Examples

```sql
-- Create a sequence
CREATE SEQUENCE seq;

-- Show all sequences
SHOW SEQUENCES;

╭───────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│  name  │  start │ interval │ current │         created_on         │         updated_on         │      comment     │
├────────┼────────┼──────────┼─────────┼────────────────────────────┼────────────────────────────┼──────────────────┤
│ seq    │      1 │        1 │       1 │ 2025-05-20 02:48:49.749338 │ 2025-05-20 02:48:49.749338 │ NULL             │
╰───────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯

-- Use the sequence in an INSERT statement
CREATE TABLE tmp(a int, b uint64, c int);
INSERT INTO tmp select 10,nextval(seq),20 from numbers(3);

-- Show sequences after usage
SHOW SEQUENCES;

╭───────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│  name  │  start │ interval │ current │         created_on         │         updated_on         │      comment     │
├────────┼────────┼──────────┼─────────┼────────────────────────────┼────────────────────────────┼──────────────────┤
│ seq    │      1 │        1 │       4 │ 2025-05-20 02:48:49.749338 │ 2025-05-20 02:49:14.302917 │ NULL             │
╰───────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
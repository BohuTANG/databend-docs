---
title: Stage
---

This page provides a comprehensive overview of stage operations in Databend, organized by functionality for easy reference.

## Stage Management

| Command | Description |
|---------|-------------|
| [CREATE STAGE](01-ddl-create-stage.md) | Creates a new stage for storing files |
| [DROP STAGE](02-ddl-drop-stage.md) | Removes a stage |
| [PRESIGN](presign.md) | Generates a pre-signed URL for stage access |

## Stage Operations

| Command | Description |
|---------|-------------|
| [LIST STAGE](04-ddl-list-stage.md) | Lists files in a stage |
| [REMOVE STAGE](05-ddl-remove-stage.md) | Removes files from a stage |

## Stage Information

| Command | Description |
|---------|-------------|
| [DESC STAGE](03-ddl-desc-stage.md) | Shows detailed information about a stage |
| [SHOW STAGES](06-ddl-show-stages.md) | Lists all stages in the current or specified database |

## Related Topics

- [Working with Stages](/guides/load-data/stage/)
- [Loading from Stage](/guides/load-data/load/stage)
- [Querying & Transforming](/guides/load-data/transform/querying-stage)

:::note
Stages in Databend are used as temporary storage locations for data files that you want to load into tables or unload from tables.
:::
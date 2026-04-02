---
name: sql
description: "Design safe MySQL or MariaDB schema changes, migrations, indexes, and validation steps."
argument-hint: "the schema change, table, query, or migration task"
---

# SQL Design

Design the database change for this repository with MySQL or MariaDB safety in mind.

## Mission

- Produce a schema, migration, or query change that is explicit, reversible when possible, and safe for shared hosting.

## Inputs

- The schema, table, query, or migration task.
- The app area that depends on the database change.
- Any existing schema or query code that already constrains the design.

## Before You Start

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check the unified SQL skill for both review and optimization guidance.
- Inspect the current schema or query code before proposing a change.
- If the task touches many files, split the work and use the manager-agent workflow.

## SQL Rules

- Use parameterized queries in application code.
- Keep schema changes minimal and explicit.
- Prefer reversible migrations when possible.
- Do not guess at column types or indexes when the repo or docs can confirm them.
- If a change affects stored data, note the migration and validation path clearly.
- If the host is shared hosting, keep the plan compatible with limited deployment control.

## Workflow

1. Identify the entities, relationships, and query patterns that actually exist.
2. Decide whether the change is a new table, a column change, an index, or a migration fix.
3. Design the smallest schema shape that supports the request.
4. Check foreign keys, nullability, uniqueness, and delete behavior.
5. Add only the indexes that the query patterns justify.
6. Plan rollback and data backfill steps if stored data changes.

## Common Tasks

- Table design
- Migration planning
- Index selection
- Query cleanup
- Seed data
- Data integrity checks

## Validation

- Table purpose is clear from the column names and constraints.
- Indexes map to real query paths.
- Migrations are safe to apply in the stated hosting or deployment model.
- Parameterized queries are used in backend code.
- Seed data does not violate constraints.

## Output Contract

- Schema or SQL changes.
- Why each index or constraint exists.
- Risks, rollback notes, and data backfill concerns.
- File and line references when possible.

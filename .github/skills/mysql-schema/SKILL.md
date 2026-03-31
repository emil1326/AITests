---
name: mysql-schema
description: Design and review MySQL or MariaDB schemas, migrations, indexes, and query safety.
---

# MySQL Schema Skill

Use this skill when the task touches schema design, migrations, or SQL.

## When to Use This Skill

- You need to add or change a table, column, foreign key, or index.
- The task changes how the backend stores or queries data.
- You need a migration plan that fits MySQL or MariaDB.
- You need to check query safety before touching PHP code.

## Before You Start

- Read the global instructions.
- Read the shared lessons file.
- Read any database-related instructions or agents.
- Check whether the change is schema-only or also affects the backend.

## What This Skill Is For

- Designing tables that match the app's query patterns.
- Adding or changing indexes with a real reason.
- Writing safe migrations that can be reasoned about later.
- Catching query or schema drift before it reaches the backend.

## Design Checklist

- What entity or relationship does the schema represent?
- What queries must be fast or safe?
- What values must be unique, required, or nullable?
- What happens on delete or update?
- What should be reversible if the migration fails?

## Controlled Flow

1. Identify the entities, relationships, and query patterns that actually exist.
2. Check whether the change is a new table, a column change, an index, or a migration fix.
3. Design the smallest schema shape that supports the request.
4. Check foreign keys, nullability, uniqueness, and delete behavior.
5. Add only the indexes that the query patterns justify.
6. Plan rollback and data backfill steps if stored data changes.

## Hard Limits

- Do not add indexes because they feel safer without checking the queries.
- Do not make columns nullable by default if the data model does not need it.
- Do not guess at collations, charset, or size limits when the app context can answer them.
- Do not use destructive migrations unless the plan explicitly accepts that risk.

## Concrete Patterns

### Good: Lookup Table With Real Query Support

```sql
CREATE TABLE user_roles (
	id INT UNSIGNED NOT NULL AUTO_INCREMENT,
	user_id INT UNSIGNED NOT NULL,
	role_name VARCHAR(64) NOT NULL,
	created_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
	PRIMARY KEY (id),
	UNIQUE KEY uq_user_role (user_id, role_name),
	KEY idx_role_name (role_name)
);
```

Why this is good:

- The key shapes match likely access patterns.
- The uniqueness rule is explicit.
- The schema tells you what the data means.

### Good: Query-Supporting Index

```sql
CREATE INDEX idx_orders_created_status ON orders (created_at, status);
```

Use this only when the app actually filters or sorts by those columns together.

### Bad: Decorative Index

```sql
CREATE INDEX idx_status ON orders (status);
```

Why this is bad:

- Low-cardinality indexes often do little by themselves.
- The index does not explain the query it exists for.

## Validation

- Table purpose is clear from the column names and constraints.
- Indexes map to real query paths.
- Migrations are safe to apply in the stated hosting or deployment model.
- Parameterized queries are used in backend code.
- Seed data does not violate constraints.

## Output Contract

- Schema or migration changes.
- Why each index or constraint exists.
- Risks, rollback notes, and data backfill concerns.
- File and line references when possible.

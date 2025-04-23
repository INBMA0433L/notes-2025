# Lab notes 2025

This repository contains notes and exercises for the subject *Database Systems and Knowledge Representation*. Note that the official announcements and other important pieces of information can be found in our Moodle course.

## Agenda

1. [Topic `A1`: Environment. Projection.](#topic-a1)
1. [Topic `A2`: Selection and pattern matching.](#topic-a2)
1. [Topic `A3`: Sorting. Aggregation.](#topic-a3)
1. [Topic `A4`: Built-in functions.](#topic-a4)
1. [Topic `B1`: Joining tables #1.](#topic-b1)
1. [Topic `B2`: Joining tables #2.](#topic-b2)
1. [Topic `C1`: Subselects #1.](#topic-c1)
1. [Topic `C2`: Subselects #2.](#topic-c2)
1. [Topic `D1`: DML statements #1.](#topic-d1)
1. Topic `D2`: DML statements #2.
1. Topic `X`: Warmup session.

## Topic `A1`

Environment. Projection.

### Notes

1. [`A101` - Environment](./A101-environment.md)
1. [`A102` - Projection](./A102-projection.md)
1. [`A102` - Projection (with possible solutions)](./A102-projection-full.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to download and set up the *SQL Developer*.
1. You must be able to create a connection using *SQL Developer*.
1. You must be able to establish a connection using *SQL Developer*.
1. You must be able to initialize a schema by executing a given script.
1. You must be able to identify a table, its columns, and primary key(s) on a schema diagram.
1. You must be able to use *Projection*:

   1. return any column of a table
   1. return all the columns of a table
   1. return any arithmetic expression as an additional column
   1. provide aliases for the columns

---

## Topic `A2`

Selection and pattern matching.

### Notes

1. [`A201` - Selection](./A201-selection.md)
1. [`A201` - Selection (with possible solutions)](./A201-selection-full.md)
1. [`A202` - Pattern matching](./A202-pattern-matching.md)
1. [`A202` - Pattern matching (with possible solutions)](./A202-pattern-matching-full.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to use *Selection*:

   1. use the arithmetic and comparison operators
   1. check for `IS NULL` and `IS NOT NULL` conditions
   1. use the `BETWEEN` condition

1. You must be able to use *Pattern matching*:
   1. use the `LIKE` condition
   1. use the `_` and `%` placeholders

---

## Topic `A3`

Sorting. Aggregation.

### Notes

1. [`A301` - Sorting](./A301-sorting.md)
1. [`A301` - Sorting (with possible solutions)](./A301-sorting-full.md)
1. [`A302` - Aggregation](./A302-aggregation.md)
1. [`A302` - Aggregation (with possible solutions)](./A302-aggregation-full.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to use *Sorting*:

   1. use the `ORDER BY` clause's syntax
   1. use both ascending and descending orders
   1. use multiple stages

1. You must be able to use *Aggregation*:

   1. use the mentioned grouping functions without `GROUP BY`
   1. use the `GROUP BY` clause's syntax (single column)
   1. use the `GROUP BY` clause's syntax (multiple columns)

---

## Topic `A4`

Built-in functions.

### Notes

1. [`A401` - Built-in functions](./A401-built-in-functions.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to understand the official documentation of a function.
1. You must be able to use the following functions and features without documentation:

   1. the `dual` table
   1. **handling `NULL` values**: `NVL()` and `NVL2()`
   1. **handling strings**: `LOWER()`, `UPPER()`, `CONCAT()` (or the `||` operator), `SUBSTR()`, `LENGTH()`, `INSTR()`
   1. **math functions**: `ROUND()`, `ABS()`
   1. **handling dates**: `SYSDATE`, `EXTRACT()`, `TRUNC()`, `TO_DATE()` (year, month, and day)

---

## Topic `B1`

Joining tables and subselects #1.

### Notes

1. [`B101` - Joining tables / The Cars Schema](./B101-join-cars-schema.md)
1. [`B102` - Joining tables / The Olympics Schema](./B102-join-olympics-schema.md)
1. [`B102` - Joining tables / The Olympics Schema (with possible solutions)](./B102-join-olympics-schema-full.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to `JOIN` two tables using all the variants:

   1. `CROSS JOIN`
   1. `INNER JOIN`
   1. `LEFT OUTER JOIN`
   1. `RIGHT OUTER JOIN`
   1. `FULL OUTER JOIN`
   1. `NATURAL JOIN`

---

## Topic `B2`

Joining tables and subselects #2.

### Notes

Continue with the remaining exercises from the last lab:

1. [`B102` - Joining tables / The Olympics Schema](./B102-join-olympics-schema.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to use self-JOINs.
1. You must be able to `JOIN` more than two tables.

---

## Topic `C1`

Subselects #1.

### Notes

1. [`C101` - Subselects, single (0D) result](./C101-subselects-0d.md)
1. [`C102` - Subselects, vector (1D) result](./C102-subselects-1d.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to use subselects that return a single value.
1. You must be able to use subselects that return a vector.
1. You must be able to use the `IN` and `NOT IN` conditions.

---

## Topic `C2`

Subselects #2.

### Notes

1. [`C201` - Subselects, matrix (2D) result](./C201-subselects-2d.md)
1. [`C202` - Conditions `ANY`, `ALL`, and `EXISTS`](./C202-subselects-any-all-exists.md)
1. [`C203` - Set Operators](./C203-set-operators.md)
1. [`C204` - `ROWNUM` Pseudocolumn](./C204-rownum.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to use subselects that return a matrix.
1. You must be able to use the `ANY`, `ALL`, and `EXISTS` conditions.
1. You must be able to use the `UNION`, `INTERSECT`, `EXCEPT`, and `MINUS`  conditions.
1. You must be able to use the `ROWNUM` pseudocolumn.

---

## Topic `D1`

DML statements #1.

### Notes

1 [`D101` - `UPDATE` statement](./D101-subselects-update.md)

### Highlights

The next lab will be based on the following expectations. Please ensure that you are aware of all the skills mentioned. Ask your questions using the available Q&A form in Moodle:

1. You must be able to use the `ROLLBACK` and `COMMIT` statements.
1. You must be able to use basic `UPDATE` statements.
1. You must be able to use subselect-based `UPDATE` statements.

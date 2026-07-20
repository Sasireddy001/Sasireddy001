# SQL Flash Cards

## Core Concepts

**Q: What is SQL?**  
**A:** SQL (Structured Query Language) is a standard language for managing relational databases, including querying, updating, and defining data.

**Q: What are the main categories of SQL commands?**  
**A:** DDL (Data Definition Language): CREATE, ALTER, DROP. DML (Data Manipulation Language): SELECT, INSERT, UPDATE, DELETE. DCL (Data Control Language): GRANT, REVOKE. TCL (Transaction Control Language): COMMIT, ROLLBACK.

**Q: What is a primary key?**  
**A:** A primary key is a column (or set of columns) that uniquely identifies each row in a table. It cannot contain NULL values and must be unique.

**Q: What is a foreign key?**  
**A:** A foreign key is a column that references the primary key of another table, establishing a relationship between tables and enforcing referential integrity.

**Q: What is a composite key?**  
**A:** A composite key is a primary key made up of two or more columns to uniquely identify a row.

## SELECT & Filtering

**Q: What is the difference between `WHERE` and `HAVING`?**  
**A:** `WHERE` filters rows before grouping. `HAVING` filters groups after aggregation.

**Q: What is the difference between `WHERE` and `ON` in joins?**  
**A:** `ON` specifies the join condition between tables. `WHERE` filters the result after the join.

**Q: What is the difference between `AND` and `OR`?**  
**A:** `AND` returns true if all conditions are true. `OR` returns true if at least one condition is true. `AND` has higher precedence than `OR`.

**Q: What is the difference between `IN` and `EXISTS`?**  
**A:** `IN` checks if a value matches any value in a list or subquery. `EXISTS` checks if a subquery returns any rows. `EXISTS` is often faster with correlated subqueries.

**Q: What is the difference between `LIKE` and `=`?**  
**A:** `=` checks for exact match. `LIKE` allows pattern matching with wildcards (`%` for any characters, `_` for single character).

## Joins

**Q: What are the types of joins in SQL?**  
**A:** INNER JOIN (matching rows), LEFT JOIN (all rows from left table + matches), RIGHT JOIN (all rows from right table + matches), FULL OUTER JOIN (all rows from both tables), CROSS JOIN (Cartesian product).

**Q: What is a self-join?**  
**A:** A self-join joins a table to itself, useful for hierarchical data (e.g., employees and managers).

**Q: What is the difference between INNER JOIN and LEFT JOIN?**  
**A:** INNER JOIN returns only matching rows. LEFT JOIN returns all rows from the left table and matching rows from the right table (NULLs for non-matches).

**Q: What is the difference between LEFT JOIN and LEFT OUTER JOIN?**  
**A:** They are the same. `OUTER` is optional in SQL.

**Q: What is a cross join?**  
**A:** A cross join returns the Cartesian product of two tables (every row from the first table combined with every row from the second table).

## Aggregation

**Q: What are common aggregate functions?**  
**A:** COUNT, SUM, AVG, MIN, MAX, STDDEV, VARIANCE.

**Q: What is the difference between `COUNT(*)` and `COUNT(column)`?**  
**A:** `COUNT(*)` counts all rows including NULLs. `COUNT(column)` counts non-NULL values in the column.

**Q: What is the difference between `SUM()` and `COUNT()`?**  
**A:** `SUM()` adds numeric values. `COUNT()` counts rows.

**Q: What is the difference between `AVG()` and `SUM()/COUNT()`?**  
**A:** `AVG()` automatically excludes NULLs. `SUM()/COUNT()` may include NULLs depending on implementation.

**Q: What is the difference between `DISTINCT` and `GROUP BY`?**  
**A:** `DISTINCT` removes duplicate rows. `GROUP BY` groups rows for aggregation. `DISTINCT` is often used for deduplication.

## Grouping

**Q: What is `GROUP BY` used for?**  
**A:** `GROUP BY` groups rows with the same values for specified columns, allowing aggregate functions to be applied to each group.

**Q: Can you use `WHERE` with `GROUP BY`?**  
**A:** No, use `WHERE` before `GROUP BY` to filter rows before grouping. Use `HAVING` after `GROUP BY` to filter groups.

**Q: What is the difference between `GROUP BY` and `DISTINCT`?**  
**A:** `GROUP BY` groups rows for aggregation. `DISTINCT` removes duplicates without aggregation.

**Q: What is the difference between `GROUP BY` and `PARTITION BY`?**  
**A:** `GROUP BY` reduces rows (one row per group). `PARTITION BY` in window functions keeps all rows but assigns them to groups.

**Q: What is `ROLLUP` in SQL?**  
**A:** `ROLLUP` generates subtotals and grand totals in `GROUP BY` queries. Example: `GROUP BY ROLLUP (a, b)` creates groups for (a,b), (a), and ().

## Window Functions

**Q: What are window functions?**  
**A:** Window functions perform calculations across a set of rows related to the current row without reducing the number of rows. Examples: `ROW_NUMBER()`, `RANK()`, `LAG()`, `LEAD()`.

**Q: What is the syntax for window functions?**  
**A:** `FUNCTION() OVER (PARTITION BY column ORDER BY column)` where `PARTITION BY` groups rows and `ORDER BY` defines the order within the partition.

**Q: What is the difference between `ROW_NUMBER()` and `RANK()`?**  
**A:** `ROW_NUMBER()` assigns unique sequential numbers. `RANK()` assigns the same rank to ties and skips subsequent ranks.

**Q: What is the difference between `RANK()` and `DENSE_RANK()`?**  
**A:** `RANK()` skips ranks after ties. `DENSE_RANK()` does not skip ranks. For values [10,10,8]: rank() = [1,1,3]; dense_rank() = [1,1,2].

**Q: What is the difference between `LAG()` and `LEAD()`?**  
**A:** `LAG()` accesses data from a previous row. `LEAD()` accesses data from a subsequent row. Both take an offset argument.

## Subqueries

**Q: What is a subquery?**  
**A:** A subquery is a query nested inside another query, used for filtering, aggregation, or data retrieval.

**Q: What is the difference between correlated and non-correlated subqueries?**  
**A:** A correlated subquery references columns from the outer query and is executed for each row. A non-correlated subquery is independent and executed once.

**Q: What is the difference between `EXISTS` and `IN` in subqueries?**  
**A:** `EXISTS` checks for existence (returns true if subquery returns any rows). `IN` checks if a value matches any value in the subquery result.

**Q: What is the difference between `ANY` and `ALL` in subqueries?**  
**A:** `ANY` returns true if the condition is true for any value in the subquery. `ALL` returns true if the condition is true for all values.

**Q: What is a CTE (Common Table Expression)?**  
**A:** A CTE is a temporary result set defined with `WITH`, used to simplify complex queries and improve readability.

## Set Operations

**Q: What are set operations in SQL?**  
**A:** UNION, UNION ALL, INTERSECT, EXCEPT (or MINUS in some databases).

**Q: What is the difference between `UNION` and `UNION ALL`?**  
**A:** `UNION` removes duplicate rows. `UNION ALL` keeps all rows (faster because no deduplication).

**Q: What is the difference between `INTERSECT` and `INNER JOIN`?**  
**A:** `INTERSECT` returns rows common to two queries (set operation). `INNER JOIN` joins tables based on a condition (relational operation).

**Q: What is the difference between `EXCEPT` and `LEFT JOIN` with NULL check?**  
**A:** `EXCEPT` returns rows from the first query not in the second. `LEFT JOIN` with NULL check achieves similar results but is more verbose.

**Q: Can you use `ORDER BY` with set operations?**  
**A:** Yes, but the `ORDER BY` must be in the final query, not in the individual queries being combined.

## Data Types

**Q: What are common SQL data types?**  
**A:** INTEGER, BIGINT, SMALLINT, DECIMAL/NUMERIC, FLOAT/DOUBLE, VARCHAR/CHAR, TEXT, DATE, TIME, TIMESTAMP, BOOLEAN, BLOB.

**Q: What is the difference between `CHAR` and `VARCHAR`?**  
**A:** `CHAR` is fixed-length and pads with spaces. `VARCHAR` is variable-length and stores only the actual characters.

**Q: What is the difference between `DECIMAL` and `FLOAT`?**  
**A:** `DECIMAL` stores exact decimal values (fixed precision). `FLOAT` stores approximate binary floating-point values.

**Q: What is the difference between `DATE` and `TIMESTAMP`?**  
**A:** `DATE` stores year, month, day. `TIMESTAMP` stores date and time, often with timezone.

**Q: What is the difference between `TEXT` and `VARCHAR`?**  
**A:** `TEXT` is unlimited length (in some databases). `VARCHAR` has a maximum length. Performance differences are minimal in modern databases.

## NULL Handling

**Q: What is NULL in SQL?**  
**A:** NULL represents missing or unknown data. It is not equal to any value, including NULL.

**Q: What is the difference between `IS NULL` and `= NULL`?**  
**A:** `IS NULL` checks for NULL values. `= NULL` always returns NULL (false) because NULL is not equal to anything.

**Q: What is the difference between `COALESCE()` and `ISNULL()`?**  
**A:** `COALESCE()` is ANSI SQL and accepts multiple arguments. `ISNULL()` is specific to some databases (e.g., SQL Server) and accepts two arguments.

**Q: What is the difference between `COALESCE()` and `NULLIF()`?**  
**A:** `COALESCE()` returns the first non-NULL value. `NULLIF()` returns NULL if two arguments are equal, otherwise the first argument.

**Q: How do you handle NULL in calculations?**  
**A:** Use `COALESCE()` to replace NULL with a default value, or use functions that ignore NULL (e.g., `SUM()` ignores NULL).

## Indexing

**Q: What is an index?**  
**A:** An index is a data structure that improves query performance by allowing faster data retrieval. It is like a book index.

**Q: What are the types of indexes?**  
**A:** B-tree (default), Hash, Bitmap, Full-text, Spatial, and Composite (multi-column).

**Q: What is the difference between clustered and non-clustered indexes?**  
**A:** A clustered index sorts and stores data physically in the index order. A non-clustered index stores a separate structure with pointers to data.

**Q: What is the difference between unique and non-unique indexes?**  
**A:** Unique indexes enforce uniqueness of values. Non-unique indexes allow duplicates.

**Q: What is the trade-off of indexing?**  
**A:** Indexes improve read performance but slow down writes (INSERT, UPDATE, DELETE) and consume storage space.

## Transactions

**Q: What is a transaction in SQL?**  
**A:** A transaction is a sequence of operations treated as a single unit of work. It follows ACID properties: Atomicity, Consistency, Isolation, Durability.

**Q: What is the difference between `COMMIT` and `ROLLBACK`?**  
**A:** `COMMIT` saves changes permanently. `ROLLBACK` undoes changes since the last commit or transaction start.

**Q: What are the isolation levels in transactions?**  
**A:** Read Uncommitted, Read Committed, Repeatable Read, Serializable. Each level balances consistency and concurrency.

**Q: What is a dirty read?**  
**A:** A dirty read occurs when a transaction reads uncommitted changes from another transaction.

**Q: What is a phantom read?**  
**A:** A phantom read occurs when a transaction re-executes a query and sees new rows that were not there before, due to another transaction's inserts.

## Performance

**Q: How do you optimize SQL queries?**  
**A:** Use appropriate indexes, avoid `SELECT *`, use `WHERE` instead of `HAVING`, limit joins, use `EXPLAIN` to analyze query plans, and avoid functions on indexed columns.

**Q: What is an execution plan?**  
**A:** An execution plan is the sequence of steps the database uses to execute a query, including table scans, index scans, joins, and sorts.

**Q: What is the difference between table scan and index scan?**  
**A:** A table scan reads the entire table. An index scan uses an index to find relevant rows, which is faster for selective queries.

**Q: What is the difference between `IN` and `EXISTS` for performance?**  
**A:** `EXISTS` is often faster with correlated subqueries because it stops at the first match. `IN` may materialize the entire subquery result.

**Q: What is query caching?**  
**A:** Query caching stores query results to avoid re-executing the same query. Useful for read-heavy workloads but can cause stale data.

## Advanced SQL

**Q: What is a recursive CTE?**  
**A:** A recursive CTE references itself to query hierarchical data (e.g., organization charts, bill of materials). It has an anchor member and a recursive member.

**Q: What is a pivot table in SQL?**  
**A:** A pivot transforms rows into columns, aggregating data. Some databases have `PIVOT` syntax; others use conditional aggregation.

**Q: What is a window frame in window functions?**  
**A:** A window frame defines the set of rows relative to the current row in a window function, specified with `ROWS BETWEEN` or `RANGE BETWEEN`.

**Q: What is the difference between `ROWS` and `RANGE` in window frames?**  
**A:** `ROWS` specifies a physical number of rows. `RANGE` specifies a logical range of values based on the order column.

**Q: What is the difference between `UNBOUNDED PRECEDING` and `CURRENT ROW`?**  
**A:** `UNBOUNDED PRECEDING` includes all rows from the start of the partition. `CURRENT ROW` includes only the current row.

## SQL Functions

**Q: What are string functions in SQL?**  
**A:** `CONCAT`, `SUBSTRING`, `LENGTH`, `TRIM`, `UPPER`, `LOWER`, `REPLACE`, `CHARINDEX`, `PATINDEX`.

**Q: What are date functions in SQL?**  
**A:** `NOW()`, `CURRENT_DATE`, `DATE_ADD`, `DATE_DIFF`, `EXTRACT`, `DATE_FORMAT`.

**Q: What are mathematical functions in SQL?**  
**A:** `ABS`, `ROUND`, `CEILING`, `FLOOR`, `POWER`, `SQRT`, `MOD`.

**Q: What are conditional functions in SQL?**  
**A:** `CASE WHEN`, `COALESCE`, `NULLIF`, `ISNULL`.

**Q: What is the difference between `SUBSTRING` and `SUBSTR`?**  
**A:** They are the same in most databases. `SUBSTRING` is ANSI SQL; `SUBSTR` is a shorthand in some databases.

## SQL Interview Questions

**Q: Write a query to find duplicates in a table.**  
**A:** `SELECT id, COUNT(*) FROM table GROUP BY id HAVING COUNT(*) > 1;`

**Q: Write a query to find the nth highest salary.**  
**A:** `SELECT DISTINCT salary FROM employee ORDER BY salary DESC LIMIT 1 OFFSET n-1;` or use `DENSE_RANK()` window function.

**Q: Write a query to delete duplicates from a table.**  
**A:** `DELETE FROM table WHERE id NOT IN (SELECT MIN(id) FROM table GROUP BY columns);` or use window functions.

**Q: Write a query to find employees with higher salary than their manager.**  
**A:** Self-join: `SELECT e.name FROM employee e JOIN employee m ON e.manager_id = m.id WHERE e.salary > m.salary;`

**Q: Write a query to calculate running total.**  
**A:** Use window function: `SELECT id, value, SUM(value) OVER (ORDER BY id) AS running_total FROM table;`

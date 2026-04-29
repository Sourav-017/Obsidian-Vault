[[string_functions_sql]]
[[Aggregate_functions_sql]]

#### Select Query with Constraints

```
SELECT column_name, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```

| Operator            | Condition                             | SQL Example                     |
| ------------------- | ------------------------------------- | ------------------------------- |
| =, !=, <, <=, >, >= | Standard numerical comparisons        | `col_name != 4`                 |
| BETWEEN … AND …     | Number is within a specific range     | `col_name BETWEEN 1.5 AND 10.5` |
| NOT BETWEEN … AND … | Number is not within a specific range | `col_name NOT BETWEEN 1 AND 10` |
| IN (…)              | Number exists in a list of values     | `col_name IN (2, 4, 6)`         |
| NOT IN (…)          | Number is not in a list of values     | `col_name NOT IN (1, 3, 5)`     |
#### **Filtering Results with DISTINCT**

In a database, some queries may return duplicate rows even if the data is unique. For example, movies can be released in the same year, causing repetition in results. To eliminate duplicates, SQL provides the **DISTINCT** keyword.

**Select Query with Unique Results:**

```
SELECT DISTINCT column, another_column, …
FROM mytable
WHERE condition(s);
```

The **DISTINCT** keyword filters out rows where all selected columns have identical values, ensuring only unique results are returned.
#### **Sorting Results with ORDER BY**

In most real databases, data is not stored in a particular order. SQL allows you to sort query results by a specific column using the **ORDER BY** clause, making it easier to read and interpret data.

**Select Query with Ordered Results:**

```
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

- **ASC**: Sorts in ascending order (default).
- **DESC**: Sorts in descending order.

Sorting can be done alpha-numerically based on the specified column, and collation settings can affect how text is sorted, especially for international characters.

#### **Limiting Results with LIMIT and OFFSET**

When working with large datasets, returning all rows may be inefficient. The **LIMIT** clause allows you to restrict the number of rows returned, and **OFFSET** specifies the starting point of rows to return.

**Select Query with Limited Rows:**

```
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

- **LIMIT**: Specifies the maximum number of rows to return.
- **OFFSET**: Specifies the starting row number (default is 0).

This is useful in paginating results, for example, displaying a few items per page on websites like Reddit or Pinterest.



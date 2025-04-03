### ### Aggregation functions in SQL are used to perform calculations on multiple rows of data and return a single result

## Aggregation in SQL
### Basic Aggregation Concepts

- COUNT() – Counting rows in a table
- SUM() – Adding up values in a column
- AVG() – Calculating the average of a column
- MIN() / MAX() – Finding the smallest or largest value

### Intermediate Aggregation

- GROUP BY – Grouping data for aggregation
- HAVING Clause – Filtering aggregated results
- DISTINCT with Aggregation – Counting unique values
- ORDER BY with Aggregation – Sorting aggregated data
- Nested Aggregations – Using aggregations within aggregations

### Advanced Aggregation

- ROLLUP – Hierarchical aggregation (useful for reporting)
- CUBE – Multi-dimensional aggregation (cross-tab reports)
- GROUPING SETS – Custom grouping combinations
- Window Functions (Analytical Aggregations):
- ROW_NUMBER() – Assigns a unique number to each row
- RANK() / DENSE_RANK() – Ranking within partitions
- NTILE() – Dividing data into equal-sized groups
- SUM() OVER() / AVG() OVER() – Aggregation without collapsing rows
- Common Table Expressions (CTE) with Aggregation
- Recursive Aggregation using CTEs
- JSON Aggregation Functions (For handling JSON data)
- String Aggregation using STRING_AGG() (PostgreSQL, SQL Server)
- Pivoting Data using PIVOT (SQL Server)

### Example 1

- SELECT category, SUM(price) AS total_sales<br/>
   FROM sales<br/>
   GROUP BY category<br/>
   HAVING total_sales > 5000;  -- ❌ Incorrect<br/>
- SELECT category, SUM(price) AS total_sales<br/> -- ✅ Correct way
   FROM sales<br/>
   GROUP BY category<br/>
   HAVING SUM(price) > 5000;<br/>


### Why?
- SQL processes HAVING before SELECT, so total_sales alias does not yet exist when HAVING runs.
- You must use SUM(price) > 5000 instead of total_sales > 5000.
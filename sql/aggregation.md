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

### Example 1 Can We Use total_sales > 5000 in HAVING Instead of SUM(price) > 5000?

- SELECT category, SUM(price) AS total_sales<br/>
   FROM sales<br/>
   GROUP BY category<br/>
   HAVING total_sales > 5000;  -- ❌ Incorrect<br/>
- SELECT category, SUM(price) AS total_sales -- ✅ Correct way<br/>
   FROM sales<br/>
   GROUP BY category<br/>
   HAVING SUM(price) > 5000;<br/>


### Why?
- SQL processes HAVING before SELECT, so total_sales alias does not yet exist when HAVING runs.
- You must use SUM(price) > 5000 instead of total_sales > 5000.

### 2. Can We Use WHERE Instead of HAVING?

- SELECT category, SUM(price) AS total_sales<br/>
  FROM sales<br/>
  WHERE SUM(price) > 5000   -- ❌ Incorrect<br/>
  GROUP BY category;

### ❌ This is NOT possible because WHERE works on individual rows, NOT aggregated results.

- SELECT category, SUM(price) AS total_sales -- ✅ Correct way using <br/>
  FROM sales<br/>
  WHERE price > 5000  -- ✅ Filters individual rows before aggregation<br/>
  GROUP BY category;<br/>

### 🚨 Problem: This filters rows where price > 5000 before aggregation, which is NOT the same as filtering after summing the prices. ✅ If we want to filter based on total sales, we must use HAVING

- SELECT category, SUM(price) AS total_sales<br/>
  FROM sales<br/>
  GROUP BY category<br/>
  HAVING SUM(price) > 5000;
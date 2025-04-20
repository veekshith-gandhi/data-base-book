# 🧱 1. Basics of Indexing

## ✅ What is an Index?
An index in SQL is like the index of a book. It helps the database find rows quickly without scanning the entire table.

### 🔍 Technical Definition:
An index is a data structure (often a B-Tree or Hash) that improves the speed of data retrieval operations on a database table.

---

## ✅ Why Use Indexes?

- ✅ **Faster searches**: Helps quickly locate data without scanning all rows.
- ✅ **Efficient JOINs and WHERE filters**: Improves the performance of joins and queries with `WHERE`, `ORDER BY`, `GROUP BY`, etc.
- ✅ **Better performance for large datasets**

---

## 📌 Example:

```sql
SELECT * FROM users WHERE email = 'veekshith@example.com';
-- Without index: full table scan
-- With index: fast lookup
```
### Indexes are amazing for finding things fast but slow things down a bit when you're adding, changing, or removing data because the database has to keep both the data and the index in sync.

## 📊 Index Type Comparison: SQL vs MongoDB vs DynamoDB

| **Index Type**           | **SQL**                    | **MongoDB**                     | **DynamoDB**                          | **Description**                                                   |
|--------------------------|----------------------------|----------------------------------|---------------------------------------|-------------------------------------------------------------------|
| **Single**               | ✅                          | ✅                                | ✅                                     | Index on a single column/field for faster lookups.               |
| **Composite / Compound** | ✅                          | ✅                                | ✅ (GSI)                               | Index on multiple fields for optimized multi-field queries.      |
| **Unique**               | ✅                          | ✅                                | ❌ (Must handle manually)              | Ensures all values in the indexed field are unique.              |
| **Full-Text / Text**     | ✅                          | ✅                                | ❌                                     | Enables advanced text search with relevance scoring.             |
| **Spatial / Geo**        | ✅                          | ✅                                | ❌                                     | Used for location-based or geospatial queries.                   |
| **Clustered / Primary**  | ✅                          | N/A                               | ✅                                     | Determines data's physical order or partitioning.                |
| **Hashed**               | ❌ (rare)                   | ✅                                | ✅ (partition hash)                    | Uses hashed values for indexing or partitioning data.            |

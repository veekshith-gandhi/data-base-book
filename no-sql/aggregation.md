### Aggregation functions in SQL are used to perform calculations on multiple rows of data and return a single result

## Aggregation in NoSQL (MongoDB)
### Basic Aggregation Concepts

- $match – Filtering documents (like SQL WHERE)
- $group – Grouping documents for aggregation
- $count – Counting documents
- $sum – Summing up field values
- $avg – Calculating the average of a field
- $min / $max – Finding minimum and maximum values

### Intermediate Aggregation

- $sort – Sorting aggregation results
- $project – Selecting and reshaping fields in output
- $unwind – Deconstructing arrays into separate documents
- $limit / $skip – Pagination with aggregation
- $addFields – Adding new computed fields
- $facet – Running multiple aggregations in parallel
- $bucket / $bucketAuto – Grouping data into buckets (like histogram bins)

### Advanced Aggregation

- $lookup (Join in MongoDB) – Joining collections (like SQL JOIN)
- $graphLookup – Recursive aggregation for hierarchical data
- $merge – Writing aggregation results to another collection
- $out – Storing aggregation results into a new collection
- $redact – Filtering documents dynamically based on conditions
- $geoNear – Aggregating geospatial data
- $setWindowFields – Window functions in MongoDB (similar to SQL window functions)
- $densify – Filling gaps in time-series data
- $fill – Replacing missing values in time-series data
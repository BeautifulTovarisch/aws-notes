# DAX - DynamoDB Accelerator #

Fully managed in-memory cache for DynamoDB. Only for read performance.

- 10x read performance improvement
- microsecond performance for millions of requests/second
- Read-heavy + burst workloads

Write-through caching service. Data is written to cache and database simultaneously. Can point application to DAX cluster before database.

- Performs **eventually consistent** *GetItem* operation if not found in cache
- Reduces read load
- May allow reduction in RCUs

Not suitable for:

- Strongly consistent reads
- Write intensive apps
- Applications that do not need microsecond responses

## Exam Tips ##

- In-memory caching
- Eventually consistent reads only
- Queries search DAX first, then database if not found
- Not optimal for write-intensive applications


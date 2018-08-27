# Elasticache 101 #

In-memory cache in the cloud! Faster than disk-based storage ( database ). Useful for improving latency, storing computationally or IO expensive results.

## Caches ##

While Redis and Memcached may appear to be very similar, their features require AWS to treat them differently and enable different capabilities as a result.

* Redis
    * Multi-AZ enabled
    * Master-slave replication
    * Elasticache clusters automatically failover
    * Persistent

* Memcached
    * Pure caching
    * Scalable pool of nodes
    * Automatic node replacement
    * Auto Discovery
    * **Not** Persistent

## Use Cases ##

|Redis|Memcached|
|-----|---------|
|Advanced Datatypes|Simple solution|
|Sorting & Ranking|Large cache nodes|
|Persistence|Horizontal scaling|
|Multi-AZ|Multi-threaded capability|

## Databases ##

Sits between application and database. Stores frequently requested information, reducing latency. Reduces load on databases. Can be used to store I/O or compute intensive operations from the database.

## Caching Strategies ##

- Lazy Loading
    - Loads only when necessary
    - If data is in cache, returns the data
    - Returns `null` if data is not found
    - Applications fetches data from database and writes to cache
    - Treats expired key as cache miss, triggering database query

|Advantages|Disadvantages|
|----------|-------------|
|Only requested data is cached|Cache miss penalty: Queries database after request|
|Node failure just resets cache|Data can become stale, doesn't automatically update|


- Write-Through
    - Adds/updates cache when data is updated in table

|Advantages|Disadvantages|
|----------|-------------|
|Never Stale|Every write must write to cache|
||Failed nodes won't update until database writes[^1]|
||Wasted resources if data is rarely read|


## Exam Tips ##

Elasticache is good for read-heavy applications. Exam may present scenario of poorly performing application and ask for the correct service. If the application is failing due to OLAP ( business analytics and processing ), AWS Redshift is a better answer.

- In-memory caches
- Sits between application and database
- Lazy Load vs Write-Through
- TTL ( time to live )

[^1]: Can be mitigated by implementing Lazy Loading to supplement

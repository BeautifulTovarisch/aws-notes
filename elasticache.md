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
|Multi-AZ|multi-thread|

## Exam Tips ##

Elasticache is good for read-heavy applications. Exam may present scenario of poorly performing application and ask for the correct service. If the application is failing to due OLAP ( business analytics and processing ), AWS Redshift is a better answer.

# Kinesis 101 #

AWS service that consumes streaming data[^1]. Provides the ability to build custom data streaming applications.

- Kinesis Streams
    - *Producers* ( EC2, Phones, Laptops etc.. ) send data to Kinesis
    - Data is stored in *shards* for 24 hours be default ( up to 7 days )
    - Data send from shards to *consumers* to process data
    - Consumers send data to other AWS services or client
    - 5 transactions per second for reads up to 2MB/second
    - 1000 records per second for write up to 1MB/second
    - Data capacity is a function of the number of shards
- Kinesis Firehose
    - Producers send data into firehouse
    - Shards are completely automated
    - Can analyze data using Lambda in real-time
    - Analysis can be sent to S3
    - No retention period
- Kinesis Analytics
    - Can run SQL queries on Firehose
    - Can store results of queries in S3, Redshift, and elasticache

# Exam Tips #

- Difference between services
- Kinesis Analytics

[^1]: Data that is generated continously, typically in small sizes.

# DynamoDB #

AWS Managed NoSQL service. Can accommodate applications that need consistent single-digit millisecond latency at scale. Supports key-value pair and document structures.

- Stored on SSD
- Spread across three regions
- Two consistency models
    - Eventual Consistent Reads ( default )
    - Strongly Consistent Reads

## Consistency Model ##

Eventually Consistent Reads:

Consistency achieved across all copies within one second.

Strongly Consistent Reads:

Reads always return successful writes across all locations.

## Terminology ##

- Tables
- Items ( row )
- Attributes( columns )
- Key-value and document storage available
- Documents can be JSON, HTML, or XML

## Primary Keys ##

DynamoDB retrieves data based on Primary Keys:

- Partition Key
    - Unique Attribute ( user id )
    - Value is run through hash function to determine partition
    - If using Partition Key as primary, must be **unique**
- Composite Key
    - Primary Key + Sort Key
    - e.g. ( userId, timestamp )
    - Useful when partition key may not be unique
    - All items with same partition key are stored together, then sorted

## Access Control ##

Entirely managed by IAM. Create IAM user/role with access to DynamoDB tables. Can use IAM Condition to restrict user access to their own records. Conditions are added to IAM **policy documents**.

Example:

```
...

"Condition": {
    "ForAllValues:StringEquals": {
        "dynamodb:LeadingKeys": [
            "${www.mygame.com:user_id}"
        ]
    }
}
...
```

## Indexes ##

Allows for faster queries on particular columns. Queries run on indexed columns rather than entire dataset.

DynamoDB has two types of **Secondary Indexes**:

- Local Secondary Index
    - Can only be created on table creation
    - Cannot be added, removed, or modified
    - Same **partition** key as original table
    - Different **sort** key
    - Queries based on this sort key are much faster

- Global Secondary Index
    - More flexible, create and modify later
    - Can choose different partition and sort keys

## Scan vs. Query ##

Different methods for retrieving data from DynamoDB table.

### Query ###

Returns items based on a Primary ( Partition ) Key and distinct value. Can use an optionally provided sort key to refine results. Uses the *ProjectionExpression* to specify returned attributes.

- Results **always** sorted by sort key
- Numeric and ASCII code values sorted ascending by default
- Can reverse order by specifying *ScanIndexForward* in query
- Queries are ***Eventually Consistent*** by default
- Can specify if Strongly Consistent behavior is desired

### Scan ###

Examines **every** item in table. By default returns all items but can be specified with *ProjectionExpression* as above. Scans allow arbitrary filters on attributes.

- Scans ***are not searches***
- Scans retrieve the entire table then filter
- Scans on large tables can use up the throughput allocated in a single operation
- Can be configured to scan in parallel
    - Avoid if table is undergoing heavy use

The impact of Queries and Scans can be mitigated by reducing the *page size*. This will allow a larger number of smaller operations.

## Provisioned Throughput ##

Defines capacity and performance requirements. Measured in Capacity Units. Read and write capacity units:

- 1RCU ( read capacity unit )
    - **1 Strongly consistent** 4 KB read per second
    - **2 Eventually consistent** 4 KB read per second
- 1WCU ( write capacity unit ) = 1KB Write per second

### Example ###

Table with 5RCUs and 5WCUs provisioned

- 20 KB/s strongly consistent reads ( 5RCU * 4KB/s = 20 )
or
- 40 KB/s eventual consistent reads ( ( 5 * 2 )RCU * 4KB/s = 40 )
- 5 KB/s writes ( 5WCU * 1KB/s )

More capacity units = more cost

### Example ###

Application needs 80 items per second, each item is 3KB. **Strongly Consistent** reads are required.

- RCUs required = item size / 4KB
    - 3KB / 4KB = 0.75KB per item
    - Round up to 1RCU
    - 1RCU[^1] x 80 items = 80RCU

### Example ###

100 items per second. Each item is 512 bytes.

- WCUs required = item size / 1KB
    - 512b / 1KB = 0.5 WCU per item
    - Round up to 1WCU
    - 1WCU x 100 items = 100WCU

## Exam Tips ##

- Low latency NoSQL Database
- Items + Attributes
- document and key-value storage
- JSON, HTML, and XML documents
- Primary key types
- Two consistency models
- `dynamodb:LeadingKeys` for fine-grained control
- Indexes = faster queries on specific columns
- Can be thought of as SQL *views*

|Local Secondary Index|Global Secondary Index|
|---------------------|----------------------|
|Must be created on table create|Can create anytime|
|Same Partition Key|Different partition key as table|
|Different Sort Key|Different Sort Key|

- Queries are more efficient than scans
- Scans take longer as the table grows
- Be careful with throughput when running scans ( reduce page size )
- Avoid using scans when possible ( use Query, Get, BatchGetItem )
- RCU and WCU calculations

[^1]: Use 2RCU for eventually consistent reads ( 80 / 2RCUs )

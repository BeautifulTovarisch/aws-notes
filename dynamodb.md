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

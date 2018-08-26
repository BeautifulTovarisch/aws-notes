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

## Exam Tips ##

- Low latency NoSQL Database
- Items + Attributes
- document and key-value storage
- JSON, HTML, and XML documents
- Primary key types
- Two consistency models
- `dynamodb:LeadingKeys` for fine-grained control

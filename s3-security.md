# S3 - Simple Storage Service Security #

## Buckets ##

By default all buckets are private. Only the owner has access. No public access.

Access Control for buckets:

* Bucket Policies
    - Bucket-level policy documents ( JSON )
    - Apply to all objects in buckets
    - Can use policy generator tool
* Access Controls Lists
    - Applied at object level
    - Can vary within bucket
    - Different types of access
* S3 Access logs
    - Logs all actions on S3 bucket
    - Can be written into another S3 bucket

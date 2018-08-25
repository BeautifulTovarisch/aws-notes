# S3 - Simple Storage Service Security #

## Buckets ##

By default all buckets are private. Only the owner has access. No public access.

Access Control for buckets:

- Bucket Policies
    - Bucket-level policy documents ( JSON )
    - Apply to all objects in buckets
    - Can use policy generator tool
- Access Controls Lists
    - Applied at object level
    - Can vary within bucket
    - Different types of access
- S3 Access logs
    - Logs all actions on S3 bucket
    - Can be written into another S3 bucket


## Encryption ##

- In Transit
    - HTTPS/SSL/TLS
- At Rest
    - Server-side encryption ( AES-256 )
        - S3 managed keys ( SSE-S3 )
            - Multifactored, auto-rotated encryption
            - Key itself is encrypted
        - AWS KMS ( S3-KMS )
            - Separate permission for envelope key ( encrypts key )
            - Audit trail for use of keys
        - Customer provided keys ( SSE-C )
    - Client Side Encryption
        - Encrypt before uploading

## Enforcing Encryption ##

A PUT request is initiated every time a file is uploaded. x-amz-server-side-encryption header will be included in the request header. This will encrypt at the time of upload. Deny any request without either of the following:

`x-amz-server-side-encryption: AES256` ( SSE-S3 )

`x-amz-server-side-encryption: ams:kms` ( SSE-KMS )

## CORS - Cross Origin Resource Sharing ##

Allow code from one S3 bucket to access another. S3 buckets can host static websites. Use endpoint URL instead of file or object URL. CORS configuration is XML *not* JSON.

## Exam Tips ##

- Encryption In-Transit/Rest
- Encryption at Rest
    - Server-side
    - Client-side
- How to enforce encryption on upload ( bucket policy )
- CORS

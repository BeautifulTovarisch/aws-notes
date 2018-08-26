# API Gateway #

Managed AWS service for building APIs

- Exposes HTTPs endpoints to RESTful API
- Serverless communication with other AWS services
- Cost-effective and scales easily
- Can throttle requests


## Configure ##

- Define API
- Define Resources ( URL routes )
- Resources
    - Select method ( GET, PUT, POST, DELETE )
    - Set Security
    - Choose target service
    - Set request and response tranforms
- Deploy api to an environment ( dev, staging, production )
    - Uses API Gateway domain by default
    - Can use custom domain
- Supports AWS Certification Manager: free TLS certs

## API Caching ##

Allows the developer to cache the endpoint response, reducing the number of calls to the API and improving latency. Similar to Elasticache.

## Same Origin Policy ##

Browers allow scripts on one webpage to access another **only** if they are of the same-origin ( same domain name ). This prevents Cross-Site scripting ( XSS ) attacks.

CORS can be set to allow restricted resources to be requested from an external domain.

## Exam Tips ##

- What is API Gateway
- Caching abilities
- Throttling
- Integrates with Cloudwatch for logging
- Enable CORS

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

## Import APIs ##

API Gateway allows a user to import Swagger files. Can POST a new API definition, or PUT to update. Updating can create a new API or merge a definition.

## Throttling ##

By default API Gateway is throttled to 10,000 requests per second. 10k rps or 5,000 concurrent requests results in 429 Too Many Requests error. This limit applies to all APIs in an AWS account.

- 10,000 requests spread evenly will process without dropping requests
- 10,000 requests in the first millisecond serves 5,000 and throttles the rest over the one-second period
- 5,000 requests in the first millisecond and then 5,000 more evenly spread over the remaining 999ms will process all requests without returning 429 error.

## SOAP Passthrough ##

Can be configured as a SOAP passthrough.

## Exam Tips ##

- What is API Gateway
- Caching abilities
- Import APIs with swagger imports
- Throttling
- Integrates with Cloudwatch for logging
- Enable CORS
- Can configure to use with SOAP

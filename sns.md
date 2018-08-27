# SNS - Simple Notification Service #

Web services that allows developers to send notifcations from the cloud. Can use push notifications to nearly all devices. SNS can deliver via SMS, Email, SQS, HTTP endpoints. Can be used to trigger Lambda functions.

## Topics ##

Group multiple recipients using an "access point". Can group multiple endpoint types. SNS will handle delivery to subscribers.

All messages are stored across AZs.

## Benefits ##

- Push-based delivery
- Easy integration
- Multiple tranport protocols
- Pay as you go
- Available on AWS console

## Pricing ##

- $0.50 per 1 million SNS requests.
- $0.06 per 100,000 Notifications over HTTP
- $0.75 per 100 Notifications over SMS
- $2.00 per 100,000 Notifications over Email

## Pub Sub ##

Follows the Publish-Subscribe paradigm. Eliminates need to constantly poll.

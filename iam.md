# IAM - Identity Access Management 101 #

**First step in any AWS Project.**

Manage users and manage access to AWS services:

* Centralized control of user/service access
* Shared access to AWS account
* Identity Federation ( Active Directory, Facebook, LinkedIn )
* Multi-factor Authentication

## Users ##

End users. Developers, Admins, HR etc... Users have *no permissions* by default

## Groups ##

Collection of users

## Roles ##

**Not Permissions!**

Authenticates users, groups, services to access AWS resources

## Policy Documents ##

JSON Permission configuration file. Implicit deny by default. Allows author to whitelist or blacklist AWS services and permissions on resources. Can be assigned to Users, Groups, Roles etc...

*A policy document can be shared among multiple entities*

## Web Identity Federation ##

Allows users to access AWS resource after authenticating with web-based authentication provider ( Amazon, Facebook, Google ). Users given a token to "exchange" for temporary credentials.

### Amazon Cognito ###

- Sign-up and sign-in to apps
- Guest Users
- No additional code needed for authenticating users
- Synchronizes data across multiple devices
- Recommended for mobile

Recommended when authenticating users from social media. Avoids need to store AWS credentials on local device.

### Cognito User Pools ###

User directories used to manage authentication for mobile and web apps. Users sign-in to user pool directly or through Facebook, Google etc... Successful authentication generates JSON web tokens ( JWTs )

### Identity Pools ###

Allows the creation of unique identities for users and authentication with identity providers. Grants temporary, limited credentials.

Cognito tracks user identity and syncs to multiple devices. Utilizes *push synchronization* to keep updates consistent.

## Inline Policies vs Managed Policies vs Custom Policies ##

- Mangaged Policies
    - IAM policy managed by AWS
    - Good for common use cases ( S3 full access )
    - Cannot change permissions in managed policy
- Customer Managed Policies
    - Standalone policy created by user
    - Can copy existing policy and customize to create new policy
- Inline Policies
    - Policy attached to **exactly one** entity ( user, group, role )
    - Useful for ensuring policies that can only be assigned to one user

## Exam Tips ##

- Secret Access Key displayed ***once***
- Cognito
- Policy Types

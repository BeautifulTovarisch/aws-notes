# IAM - Identity Access Management 101 #

**First step in any AWS Project.**

Manage users and manage access to AWS services:

* Centralized control of user/service access
* Shared access to AWS account
* Identity Federation ( Active Directory, Facebook, LinkedIn )
* Multi-factor Authentication

# Users #

End users. Developers, Admins, HR etc... Users have *no permissions* by default

# Groups #

Collection of users

# Roles #

**Not Permissions!**

Authenticates users, groups, services to access AWS resources

# Policy Documents #

JSON Permission configuration file. Implicit deny by default. Allows author to whitelist or blacklist AWS services and permissions on resources. Can be assigned to Users, Groups, Roles etc...

*A policy document can be shared among multiple entities*

-------------------------------------------------------------------------------

# Exam Tips #

When creating a user: Secret Access Key displayed ***once***

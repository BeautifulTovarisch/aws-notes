# EC2 with Roles #

## Use IAM to assign Roles ##

IAM can manage an AWS security feature called Roles. Roles allow users, groups, and services to ***authenticate*** in place of Access Key ID and Secret Access Key. Roles also allow services to access other services. E.g EC2 gaining access to S3 buckets.

Roles = ***Temporary*** keys

Always apply the Principle of Least Privilege[^1]. If you've already configured an EC2 instance with keys, you can run `rm ~/.aws/credentials` and `rm ~/.aws/config` on the machine and proceed with Roles.

## Exam Tips ##

* Roles allow you to not use Access Key IDs and Secret Access Keys
* Roles are ***always*** preferred to keys for security
* Roles are controlled by policies ( policy documents )
* Change a policy on a document takes effect **immediately**
* It is now possible to attach/detach a role from a running instance

[^1]: Allow users only the amount of access they need to perform their duties.

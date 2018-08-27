# Elastic Beanstalk #

Service for deploying and scaling web applications. Can deploy Java, .NET, PHP, Node.js, Python, Ruby, Go, Docker onto Tomcat, Nginx, Passenger, and IIS. Similar to cloudformation except used through console.

Developers upload a zip with code and Elastic Beanstalk automatically provisions resources.

- Fastest way to deploy
- Automatically scales
- Select EC2 instances
- Retain full admin control
- Can enable platform updates automatically
- Integrates with CloudWatch + X-Ray

## Deployment Policies ##

Several options for deployments:

- All at once
    - Deploys instances simultaneously
    - All instance will be out of service while deploying
    - Not ideal for mission-critical
    - If update fails, re-deploy rollback
- Rolling
    - Deploys new version in batches
    - Each batch taken out of service while deploying
    - Capacity reduced during deployment
    - Perform additional rolling update on fail
- Rolling with additional batch
    - Launches batch of instances
    - Maintains full capacity
    - Perform rolling update on failure
- Immutable
    - Deploys to completely new instances
    - New instances that pass are moved into auto-scaling group
    - Maintains full capacity
    - Rollback only requires terminating new auto scaling group
    - Preferred for mission-critical production systems

You can customize Elastic Beanstalk with YAML or JSON files with *.config* extention. Must be saved in .ebextenions. Must be included in top level directory of application code.

Example:

The following configures an application health check URL to be used by the Elastic Load Balancer.

```
{
    "option_settings": [
        {
            "namespace": "aws:elasticbeanstalk:application",
            "option_name": "My Application Healthcheck URL",
            "value": "/healthcheck"

        }
    ]
}
```

## EBS with RDS ##

Two options: Launch RDS instance from EBS environment. **Note:** Deleting your Elastic Beanstalk environment will delete your database with this method.

For production it is better to decouple EBS from the RDS instance. Launch from RDS, not Elastic Beanstalk.

Must add additional security group and provide connection string of RDS database.

## Exam Tips ##

- Deployment Policies
- How to customize Elastic Beanstalk environment

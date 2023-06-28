# Amazon Aurora Global Database

Use the AWS CloudFormation template to create Amazon Aurora global database.


___
![Architecture Diagram](https://github.com/dakshjat/aws-aurora-global-database/assets/47545538/9392bd81-fd22-4d53-949a-e48de64f17d1)

___


**To create an AWS CloudFormation stack, you can use the following options:**

**#1.** From the AWS console, create an AWS CloudFormation stack with new resources, specify the template, and enter appropriate parameters.

**#2** Use the below AWS CLI command to create an AWS CloudFormation stack with a parameter file:

* Primary cluster: `aws cloudformation deploy --stack-name amazon-aurora-global-database-primary --template-file amazon-aurora-global-database-primary.yaml --parameter-overrides file://parameters.json --capabilities CAPABILITY_NAMED_IAM`     

* Secondary cluster: `aws cloudformation deploy --stack-name amazon-aurora-global-database-secondary --template-file amazon-aurora-global-database-secondary.yaml --parameter-overrides file://parameters.json  --capabilities CAPABILITY_NAMED_IAM`
___
**Failover in an Amazon Aurora global database:**

**#1.** To perform manual unplanned failover:
* `aws rds promote-read-replica-db-cluster --db-cluster-identifier <db-cluster-identifier>`
* [AWS CLI promote-read-replica-db-cluster](https://docs.aws.amazon.com/cli/latest/reference/rds/promote-read-replica-db-cluster.html)

**#2.** To perform managed planned failover: 
*  `aws rds failover-global-cluster --global-cluster-identifier <global-cluster-identifier> --target-db-cluster-identifier <target-db-cluster-identifier>`
* [AWS CLI failover-global-cluster](https://docs.aws.amazon.com/cli/latest/reference/rds/failover-global-cluster.html)
___

For more information on Amazon Aurora global databases, visit [Using Amazon Aurora global databases](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database.html).

For more information on failover in an Amazon Aurora global databases, visit [Working with read replicas for Amazon RDS for Oracle](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database-disaster-recovery.html).
#### Monitoring Security Groups with AWS Config

how to use AWS Config Rules with an AWS Lambda function to monitor the ingress ports associated with an EC2 security group.
The Lambda function will be triggered whenever the security group is modified.If the ingress rule configuration differs from that which is coded in the function, the Lambda function will revert the ingress rules back to the appropriate configuration.  The activity from the Lambda function can then be viewed through Amazon CloudWatch Logs.

### Architecture Overview

![](./images/diagramm3.png)

<img src="https://github.com/abhinavkorpal/AWS/images/logo.png" width="100">

### Topics covered

By the end of this module, you will be able to:

1.  Upload a preconfigured Lambda function

2.  Enable AWS Config

3.  Create and enable a custom AWS Config rule

4.  Use CloudWatch Logs to review the execution of the AWS Config rule

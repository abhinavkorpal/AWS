#### Monitoring Security Groups with AWS Config

how to use AWS Config Rules with an AWS Lambda function to monitor the ingress ports associated with an EC2 security group.
The Lambda function will be triggered whenever the security group is modified.If the ingress rule configuration differs from that which is coded in the function, the Lambda function will revert the ingress rules back to the appropriate configuration.  The activity from the Lambda function can then be viewed through Amazon CloudWatch Logs.

### Architecture Overview

![](https://github.com/abhinavkorpal/AWS/blob/master/images/architecture.png)


### Topics covered

By the end of this module, you will be able to:

1.  Upload a preconfigured Lambda function

2.  Enable AWS Config

3.  Create and enable a custom AWS Config rule

4.  Use CloudWatch Logs to review the execution of the AWS Config rule

### Prerequisites

To successfully complete this module, you should be familiar with EC2 security groups. Python programming skills are helpful, although full solution code is provided.

### 1. Select a Region

Login to the AWS Console. Make sure that the user has "Admin" rights to the AWS services. Not using an Admin user will create permission issues during the module. Make a note of the AWS *region name*, for example, *EU (Ireland),*

**Tip** The AWS region name is always listed in the upper-right corner of the AWS Management Console, in the navigation bar.

For more information about regions, see [AWS Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html).

___Complete all the steps below unless they are marked "optional". Use left arrow to expand sections marked with (expand for details).___

### 2. Complete Initial Environment Configuration

<details open>
<summary><strong>2.1. Enable AWS Config (expand for details)
</strong></summary><p>
<br/>

- __2.1.1.__  On the **Services** menu, click **Config**.

- __2.1.2.__  Click **Get Started** if you see a button with that text, else click
    **Settings**.

- __2.1.3.__  Under Resource types to record, ***uncheck*** the box **Record all resources supported in this region**.

- __2.1.4.__  Click inside of the **Specific types** box. A scroll box field will appear. Scroll down to the EC2 section and click **SecurityGroup**. You should see **EC2: Security Group** appear in the **Specific types** box. Click outside of the box to close the scroll box field.

- __2.1.5.__  Under **Amazon S3 bucket**, select **Create a bucket**. In the **Bucket name** field, use the default name that is provided. Leave the **Prefix (optional)** text box empty. *Make sure that the Bucket Name is not already created else you will get a bucket already exist error.*

- __2.1.6.__  Under **AWS Config Role**, select **Create a Role**. In the **Role name** field, use the default name that is provided.

- __2.1.7.__  Click the **Next** button at the bottom right of the web page.

- __2.1.8.__  On the **AWS Config Rules** page, do not select any rules. You will add a custom rule later. Click **Next**.

- __2.1.9.__  On the **Review** page, click **Confirm.** After a while, you will see the **Config Dashboard** page appear.

![](./images/image3.png)


</details>

<details open>
<summary><strong>2.2. Create an EC2 Security Group (expand for details)
</strong></summary><p>
<br/>

- __2.2.1.__ Click the **Services** menu and select **VPC.** The **VPC Dashboard** will appear.

- __2.2.2.__ On the left hand side of the window click **Security Groups**.

- __2.2.3.__ Click **Create Security Group button**.

- __2.2.4.__ In the **Name tag** text box, enter "SID402Module3SG". The **Group name** text box should populate automatically.

- __2.2.5.__ In the Description text box, enter "Module 3 Security Group". Keep the default VPC in the **VPC** drop down list.

- __2.2.6.__	Click **Yes, Create** button.

- __2.2.7.__	Select the **SID402Module3SG** Security Group.  Copy the group identifier which will be in the form of sg-######## to a scratch file as you will need it later.

- __2.2.8.__	Click on the **Inbound Rules** tab and click the **Edit** button.

- __2.2.9.__	Add the Inbound Rules. Your Inbound Rules should look like this:

<p/>

![](./images/image4.png)

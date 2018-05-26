# AWS CloudFormation Template: Rubrik CloudOut

Complete the AWS configuration process required for the Rubrik CloudOut which uses an S3 bucket for archiving to Amazon.

Amazon S3 Template URL
------------------
[https://s3-us-west-1.amazonaws.com/cloudformation-templates-rubrik-prod/rubrik_cloudout.template
](https://s3-us-west-1.amazonaws.com/cloudformation-templates-rubrik-prod/rubrik_cloudout.template
)

![Select Template](https://user-images.githubusercontent.com/8610203/39970416-9d6bd71a-56b0-11e8-8a58-7832875180a8.png)

CloudFormation Stack Interface
------------------

![CloudFormation Screenshot](https://user-images.githubusercontent.com/8610203/40571735-e047cbd6-6063-11e8-9f32-a2fad181862c.png)

Variables
------------------

**Storage Configuration**

| Variable  |  Default | Description  |
|---|---|---|
| CreateS3NewBucket | no | Create a new S3 Bucket to use as a Rubrik archival location.|
| S3BucketName | n/a |The name of the S3 Bucket used as a Rubrik archival location.|


**IAM Users and Roles**

| Variable  |  Default | Description  |
|---|---|---|
| CreateNewUser | yes | Create a new IAM user specific to Rubrik CloudOn. If 'no' is selected the S3 IAM policy will be attached to the provided IAMUserName which should already be created. |
| IAMUserName | rubrik-cloudon | The name of the IAM User to assign the new CloudOn specific policies to. |



**Optional**

Default names and descriptions for the various IAM Users, Policies, and Security Group created during the process.

| Variable  |  Default | Description  |
|---|---|---|
| UserPolicyName |rubrik-cloudon |S3 Security policy used for Rubrik CloudOn.|

Output
------------------

| Variable | Description |
|---|---|
| IAMUserAccessKey | Access Key for the new IAM User (if applicable).  |
| IAMUserSecretKey | Secret Key for the new IAM user (if applicable).  |

Author Information
------------------

<p></p>
<p align="center">
  <img src="https://user-images.githubusercontent.com/8610203/37415009-6f9cf416-2778-11e8-8b56-052a8e41c3c8.png" alt="Rubrik Ranger Logo"/>
</p>
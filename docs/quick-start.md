# Quick Start: AWS CloudFormation Template for Rubrik CloudOut

Walkthrough for commpleting the AWS configuration process required for the Rubrik CloudOut to S3.

The following tasks are completed during the workflow:

* A new IAM user is created* (Access and Secret Keys generated)
* A new inline IAM policy is created for the user
* S3 bucket is created*
* A new KMS key is created (optional)

_* The template can also consume a previously created IAM User or S3 Bucket_

![Template Design](/docs/img/rubrik_cloudout-designer.png)

## CloudFormation Stack

Navigate to **Services** > **CloudFormation** > **Stacks** and select **Create Stack**. 

![Create a Stack](/docs/img/image1.png)

Either select **Upload a template file** or, preferably, **Specify an Amazon S3 template URL**.

![Select Template](/docs/img/image2.png)

The template file can be downloaded [here](https://s3-us-west-1.amazonaws.com/cloudformation-templates-rubrik-prod/rubrik_cloudout.template). Copy the following URL:

`https://s3-us-west-1.amazonaws.com/cloudformation-templates-rubrik-prod/rubrik_cloudout.template`

On the **Specify stack details** page, enter the **Stack name** and the **S3BucketName**. 

![Specify Details](/docs/img/image3.png)

Press **Next** through the **Options** page.

Use the **Review** page to ensure all the information is correct. Press **Create** once reviewed.

Go to the Rubrik UI, select the configuration cog, and choose **Archival Locations**. Select the plus (**+**) sign to add a new archival location.

![Add Archival Location](/docs/img/image4.png)

Follow the Rubrik CDM User Guide to complete the setup. 

## Variables

This section provides information regarding the variables used in the template.

| WARNING: CloudFormation is not ideponment. If any of the provided variables are not unique the template will return an error message! |
| --- |

### Storage Configuration

| Variable          | Default | Description                                                                                                           |
|-------------------|---------|-----------------------------------------------------------------------------------------------------------------------|
| CreateS3NewBucket | yes     | Create a new S3 Bucket to use as a Rubrik archival location. Choose 'no' if you wish to use a bucket already created. |
| S3BucketName      | n/a     | The name of the S3 Bucket used as a Rubrik archival location.                                                         |

### IAM Users and Roles

| Variable      | Default        | Description                                                                                                                                                           |
|---------------|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CreateNewUser | yes            | Create a new IAM user specific to Rubrik CloudOn. If 'no' is selected, the IAM policy will be attached to the provided `IAMUserName` which should already be created. |
| IAMUserName   | rubrik-cloudon | The name of the IAM User to assign the new CloudOn specific policies to.                                                                                              |

### Optional

Default names and descriptions for the various IAM Users, Policies, and Security Group created during the process.

| Variable       | Default        | Description                                 |
|----------------|----------------|---------------------------------------------|
| UserPolicyName | rubrik-cloudon | S3 Security policy used for Rubrik CloudOn. |

## Output 

The following information can used when to add the archive location to the Rubrik cluster.

| Variable         | Description                                         |
|------------------|-----------------------------------------------------|
| IAMUserAccessKey | Access Key for the new IAM User (if applicable).    |
| IAMUserSecretKey | Secret Key for the new IAM user (if applicable).    |
| AWSBucketName    | The S3 Bucket name.                                 |
| KMSKeyId         | The KMS Key ID used for encryption. (if applicable) |
| Region           | The AWS Region where the configuration took place.  |


---
title : "Create an IAM Role"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

To perform cross-account data transfer with AWS DataSync, you need an IAM role in your source account that grants DataSync permission to write to the S3 bucket in your destination account.

### Creating the IAM Role for DataSync in Your Source Account
Normally, AWS DataSync can create a role automatically with the necessary permissions when you set up a transfer location for an S3 bucket through the console. However, for cross-account transfers, this role must be created manually.


#### To Create the IAM Role:
1. Log in to the AWS Management Console with your source account credentials.
2. Navigate to the IAM console at [https://console.aws.amazon.com/iam/](https://console.aws.amazon.com/iam/).
3. In the left navigation pane, under **Access management**, select **Roles**, then click **Create role**.
4. On the **Select trusted entity** page, set **Trusted entity type** to **AWS service**.
   ![iam-role](/images/1-Introduce/iam-1.jpg?featherlight=false&width=90pc)
5. For **Use case**, choose **DataSync** from the dropdown list, then click **Next**.
6. Skip the **Add permissions** step by clicking **Next**.
   ![iam-role](/images/1-Introduce/iam-2.jpg?featherlight=false&width=90pc)
7. Provide a name for your role and click **Create role**.
   ![iam-role](/images/1-Introduce/iam-3.jpg?featherlight=false&width=90pc)
   

For detailed instructions, refer to [Creating a role for an AWS service (console)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the IAM User Guide.

### Attaching a Custom Policy to the IAM Role
The IAM role needs a policy that permits DataSync to write to the destination S3 bucket.

#### To Attach a Custom Policy to Your IAM Role:
1. On the **Roles** page of the IAM console, find the role you just created and select its name.
2. On the role's detail page, go to the **Permissions** tab. Click **Add permissions** then **Create inline policy**.
   ![iam-role](/images/1-Introduce/iam-4.jpg?featherlight=false&width=90pc)
   
3. Go to the **JSON** tab and perform the following:
   - Paste the JSON policy below into the policy editor:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "s3:GetBucketLocation",
        "s3:ListBucket",
        "s3:ListBucketMultipartUploads"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:s3:::destination-bucket"
    },
    {
      "Action": [
        "s3:AbortMultipartUpload",
        "s3:DeleteObject",
        "s3:GetObject",
        "s3:ListMultipartUploadParts",
        "s3:PutObject",
        "s3:GetObjectTagging",
        "s3:PutObjectTagging"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:s3:::destination-bucket/*"
    }
  ]
}

```

**Note**: Replace destination-bucket with the actual name of the S3 bucket in your destination account.
**For example**:
   ![iam-role](/images/1-Introduce/iam-5.jpg?featherlight=false&width=90pc)


---
title : "Configure Destination S3 Bucket"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

Ensuring that your destination account has full ownership of the data is crucial when transferring to an S3 bucket. This is achieved by disabling the bucket's Access Control Lists (ACLs), which by default could grant access to other accounts.

### Disabling ACLs for Your S3 Bucket
Ownership control is vital for maintaining data security standards. Follow these steps in your destination account to disable ACLs:

1. Log in to the AWS Management Console of your destination account.
2. Access the Amazon S3 console at [https://console.aws.amazon.com/s3/](https://console.aws.amazon.com/s3/).
3. From the left sidebar, click on **Buckets**.
4. Select the target S3 bucket to which you're transferring data from the list.
5. Navigate to the **Permissions** tab on the bucket's detail page.
6. Under **Object Ownership**, click **Edit**.
7. If not already done, select the option for **ACLs disabled (recommended)**.
8. Confirm the change by clicking **Save changes**.

Disabling ACLs ensures that all transferred data is owned by the destination account, aligning with best practices for data security. For further details, visit the [Controlling ownership of objects and disabling ACLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/about-object-ownership.html) section in the Amazon S3 User Guide.

### Configure Your S3 Bucket Policy

It's time to adjust the S3 bucket policy in your destination account to recognize and accept the IAM role designed for DataSync operations from your source account.

By updating the bucket policy, you’ll grant the necessary permissions for two specific roles:

- The first role is the one assigned to AWS DataSync in your source account, permitting it to write data to the destination bucket.
- The second role covers the necessary permissions for any users in your source account who will interact with AWS DataSync.

Proceed with the following steps to ensure your destination S3 bucket has the correct permissions:

1. Within the Amazon S3 console of your destination account, navigate to the S3 bucket designated for data receipt.
2. Access the **Permissions** tab on your bucket's detail page.
3. Click on **Edit** next to **Bucket policy** and revise the policy as follows:

```json
{
  "Version": "2008-10-17",
  "Statement": [
    {
      "Sid": "DataSyncS3WriteAccess",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::<source-account-id>:role/<dataSync-role-in-source-account>"
      },
      "Action": [
        "s3:GetBucketLocation",
        "s3:ListBucket",
        "s3:ListBucketMultipartUploads",
        "s3:AbortMultipartUpload",
        "s3:DeleteObject",
        "s3:GetObject",
        "s3:ListMultipartUploadParts",
        "s3:PutObject",
        "s3:GetObjectTagging",
        "s3:PutObjectTagging"
      ],
      "Resource": [
        "arn:aws:s3:::<destination-bucket>",
        "arn:aws:s3:::<destination-bucket>/*"
      ]
    },
    {
      "Sid": "UserAccessForDataSyncLocation",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::<source-account-id>:role/<user-in-source-account>"
      },
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::<destination-bucket>"
    }
  ]
}
```

⚠️ Important: There is an essential correction to the AWS documentation here. Where the policy references the IAM role for user permissions, it should actually reference an IAM user as follows:
**"AWS": "arn:aws:iam::source-account-id:user/user-in-source-account"**.
This change is necessary for proper permissions delegation when using an IAM user to manage DataSync.



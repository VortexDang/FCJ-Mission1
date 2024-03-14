---
title : "Create Source Location"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

After setting up the destination location for your S3 bucket in the target account, the next step in our cross-account data migration process is to establish a source location in AWS DataSync. This source location will reference the S3 bucket in your source AWS account from which DataSync will read data.

### Creating a Source Location in DataSync

Creating a source location involves specifying the S3 bucket that serves as the data origin and assigning the necessary permissions for DataSync to access this bucket.

#### To Create a Source Location:

1. **Log Into AWS Management Console**: Ensure you are logged into the AWS Management Console under your source account.

2. **Navigate to AWS DataSync**: Open the AWS DataSync service by searching for it in the service search bar or by finding it under "Storage" in the Services menu.

3. **Start Creating a New Location**: Within the DataSync dashboard, click on **Create location** to begin the setup for a new source location.

4. **Select Your Source Storage Service**: Choose Amazon S3 as the location type. This indicates the source of your data for the migration task.

5. **Configure S3 Bucket Access**:
    - **S3 Bucket Name**: Enter the name of the S3 bucket in your source account that contains the data you wish to migrate.
    - **IAM Role**: Provide the ARN of the IAM role that DataSync will assume to access the source S3 bucket. This role must have permissions to read from the bucket and list its contents.

6. **Review and Create**: Once you have filled in the necessary information, review your settings to ensure everything is correct. Click **Create location** to finalize the creation of your source location.

   ![source-location](/images/1-Introduce/source-location.jpg?featherlight=false&width=90pc)

### Verification

After creating the source location, you will see it listed in the **Locations** section of the AWS DataSync console. Ensure that the location status is available, indicating that DataSync can access the S3 bucket and is ready to start transferring data.

By completing this step, you have successfully set up the source location for your cross-account S3 migration. The next step will involve creating a DataSync task that uses this source location and the destination location you set up previously to transfer data across AWS accounts.

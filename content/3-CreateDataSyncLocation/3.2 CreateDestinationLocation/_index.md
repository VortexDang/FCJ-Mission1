---
title : "Create Destination Location"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

Setting up a DataSync destination location for the S3 bucket in your destination account is a necessary step from your source account. The DataSync console itself doesn't permit creating locations for storage resources in another account directly. Nevertheless, AWS CloudShell comes to the rescue, offering a way to bypass this limitation.

### Using AWS CloudShell for DataSync Configuration
AWS CloudShell is a browser-based shell that is integrated into the AWS Management Console, providing a way to run AWS CLI commands without additional installations.

> **Note:** If opting to use a command line tool other than CloudShell, your AWS CLI profile must correspond to the `source-user-role` referenced in the bucket policy. Consult the [AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html) for more details.

#### Steps to Create a DataSync Destination Location:
1. Return to the AWS Management Console under your source account.
2. Access the [AWS DataSync console](https://console.aws.amazon.com/datasync/).
3. Launch CloudShell by:
   - Clicking on the CloudShell icon next to the search box on the console navigation bar.
   - Or searching for "CloudShell" in the console search box and selecting it from the results.
4. Prepare the following AWS CLI command by replacing the placeholders:

```shell
aws datasync create-location-s3 \
  --s3-bucket-arn arn:aws:s3:::<destination-bucket> \
  --s3-config '{
    "BucketAccessRoleArn":"arn:aws:iam::<source-account-id>:role/<DataSync-role-in-source-account>"
  }'
```

5. Change `<destination-bucket>` to the name of your destination S3 bucket.
6. Replace `<source-account-id>` with the ID of your source account.
7. Substitute   `<DataSync-role-in-source-account>` with the role you established for DataSync in the source account.
8. If the destination bucket is in a different region, include --region followed by the appropriate region code, such as --region us-east-2.
9. Execute the modified command in CloudShell.
     
    Upon successful execution, you will receive a DataSync location ARN, indicating that the destination location has been established:
```json
{
  "LocationArn": "arn:aws:datasync:<region>:<source-account-id>:location/loc-<unique-id>"
}
``` 
10. Verify the new location by going to the Data transfer section and clicking on Locations in the DataSync console. If the location is in a different region, remember to switch to the correct one from the console.

**For example**:
   ![destination-location](/images/1-Introduce/destination-location.jpg?featherlight=false&width=90pc)



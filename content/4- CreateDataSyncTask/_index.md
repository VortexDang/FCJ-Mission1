---
title : "Create & Start DataSync Task"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 3. </b> "
---

With the preparatory steps completed, including IAM role creation and configuring both source and destination S3 bucket locations, you're now ready to create and start the DataSync transfer task to move your data across AWS accounts.

### Creating and Starting the DataSync Transfer Task

1. **Navigate to DataSync in the Source Account**: In the AWS Management Console, ensure you're using the DataSync service within your source account.

2. **Initiate Task Creation**:
    - Expand **Data transfer** in the left navigation pane.
    - Choose **Tasks**, then **Create task**.

3. **Select the Task Region**:
    - If your destination bucket resides in a different AWS Region than your source bucket, select the appropriate Region for the destination bucket in the top navigation pane.
    - **Important**: The DataSync task must be created in the same Region as the destination location to avoid network connection errors.

4. **Configure Source Location**:
    - Choose **Choose an existing location**.
    - If applicable, select the correct Region where the source bucket resides from the **Region dropdown**.
    - Select your previously configured source location from **Existing locations**, then click **Next**.

5. **Configure Destination Location**:
    - Select **Choose an existing location**.
    - Choose the destination location for the S3 bucket you're transferring data to, then click **Next**.

6. **Configure Task Settings**:
    - Provide a name for your task.
    - Optionally, configure additional settings such as specifying an Amazon CloudWatch log group.
    - Proceed by selecting **Next**.

7. **Review and Create Task**:
    - Review your task settings for accuracy.
    - Click **Create task** to finalize the task setup.

8. **Start the Transfer Task**:
    - On the task's detail page, choose **Start**.
    - Decide on starting the task with defaults or customizing the start options:
        - **Start with defaults** for a standard transfer.
        - **Start with overriding options** if adjustments are needed before execution.

### Verifying the Data Transfer

After the task completes, verify the transfer by checking the destination S3 bucket in your destination account. The data from your source account's S3 bucket should now be present, signifying a successful cross-account migration.

---
title : "Cleanup Resource"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 5. </b> "
---

## Clean-Up Resources

Once you've completed the data transfer task and verified the successful migration of your data across AWS accounts, it's essential to perform clean-up actions to avoid unnecessary costs and resource usage. Follow these steps to clean up the resources used during the migration process:

1. **Stop DataSync Task**:
    - Navigate to the DataSync console in your source account.
    - Select the completed transfer task.
    - Choose **Stop** to halt the task execution.

2. **Delete DataSync Task**:
    - After stopping the task, select the task again.
    - Click **Delete** to remove the task from your account.

3. **Delete DataSync Locations**:
    - In the DataSync console, navigate to **Locations**.
    - Delete both the source and destination locations associated with the completed task.

4. **Remove IAM Roles**:
    - Access the IAM console in both your source and destination accounts.
    - Delete the IAM roles created for DataSync, ensuring no residual permissions remain.

5. **Revert S3 Bucket Policies**:
    - Review and modify the bucket policies of your S3 buckets if any changes were made during the setup.
    - Ensure policies are reverted to their original configurations or as required for ongoing operations.

6. **Review and Confirm**:
    - Double-check all steps to ensure you're deleting the correct resources.
    - Confirm deletion prompts to permanently remove resources from your AWS accounts.

Following these steps will help maintain a clean and organized AWS environment while preventing unnecessary charges and ensuring compliance with security best practices. Always verify the removal of resources to avoid unintentional deletions and potential data loss.

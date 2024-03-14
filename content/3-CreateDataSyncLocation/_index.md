---
title : "Create DataSync Location"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 3. </b> "
---

## Introduction to Creating DataSync Locations for Cross-Account S3 Migrations

In this segment of our workshop, we'll focus on a crucial aspect of migrating data between S3 buckets across different AWS accounts: creating AWS DataSync locations. A DataSync location acts as a pointer to either the source or destination of your data transfer. For cross-account S3 migrations, you'll define one location for the source bucket in your source account and another location for the destination bucket in your target account.

Creating these locations is essential, as it allows DataSync to understand where to pull data from and where to deliver it. This step involves specifying the S3 bucket details and ensuring DataSync has the necessary permissions, via an IAM role, to access these buckets.

This process is straightforward yet critical to the success of your data migration efforts, laying the groundwork for the efficient, secure, and reliable transfer of data between AWS accounts.


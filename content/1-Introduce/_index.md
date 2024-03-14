---
title : "Introduction"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

## Introduction to AWS DataSync

**AWS DataSync** is an online data movement and discovery service that simplifies data migration and helps you quickly, easily, and securely transfer your file or object data to, from, and between AWS storage services.

#### On-premises storage transfers
DataSync works with the following on-premises storage systems:
- Network File System (NFS)
- Server Message Block (SMB)
- Hadoop Distributed File Systems (HDFS)
- Object storage

#### AWS storage transfers
DataSync is compatible with the following AWS storage services:
- Amazon S3
- Amazon EFS
- Amazon FSx for Windows File Server
- Amazon FSx for Lustre
- Amazon FSx for OpenZFS
- Amazon FSx for NetApp ONTAP

#### Other cloud storage transfers
DataSync also facilitates transfers to other cloud storage services including:
- Google Cloud Storage
- Microsoft Azure Blob Storage
- Microsoft Azure Files
- Wasabi Cloud Storage
- DigitalOcean Spaces
- Oracle Cloud Infrastructure Object Storage
- Cloudflare R2 Storage
- Backblaze B2 Cloud Storage
- NAVER Cloud Object Storage
- Alibaba Cloud Object Storage Service
- IBM Cloud Object Storage
- Seagate Lyve Cloud

#### Edge storage transfers
Additionally, DataSync works with edge storage services and devices such as:
- Amazon S3 compatible storage on AWS Snowball Edge
- AWS Snowcone

#### Use cases
The main use cases for DataSync include:
- **Discover data:** Get visibility into your on-premises storage performance and utilization. AWS DataSync Discovery can also provide recommendations for migrating your data to AWS storage services.
- **Migrate data:** Move active datasets rapidly over the network into AWS storage services. DataSync includes automatic encryption and data integrity validation to help ensure that your data arrives securely, intact, and ready to use.
- **Archive cold data:** Move cold data stored in on-premises storage directly to durable and secure long-term storage classes such as S3 Glacier Flexible Retrieval or S3 Glacier Deep Archive.
- **Replicate data:** Copy data into any Amazon S3 storage class, choosing the most cost-effective storage class for your needs. You can also replicate data to Amazon EFS, FSx for Windows File Server, FSx for Lustre, or FSx for OpenZFS.
- **Move data for timely in-cloud processing:** Facilitate data movement in or out of AWS for processing, accelerating hybrid cloud workflows in various industries.

#### Benefits
Using DataSync, you can achieve the following benefits:
- **Simplify migration planning:** Minimize the time, effort, and costs associated with planning data migrations to AWS with automated data collection and recommendations from DataSync Discovery.
- **Automate data movement:** Easily move data over the network between storage systems and services with DataSync's automated process and infrastructure management.
- **Transfer data securely:** With end-to-end security, including encryption and integrity validation, DataSync ensures that your data is transferred securely and intact.
- **Move data faster:** DataSync's purpose-built network protocol and multi-threaded architecture accelerate data transfers, improving the speed of migrations and data-processing workflows.
- **Reduce operational costs:** DataSync's flat, per-gigabyte pricing allows for cost-effective data movement, eliminating the need for custom scripts or expensive transfer tools.
---
title: "Create DocumentDB Cluster (Multi-AZ)"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 5.3.2. </b> "
---

<div class="lms">

# Create the Amazon DocumentDB cluster (Multi-AZ)

Create a document database (MongoDB-compatible) placed in a private subnet.

**Find and open the Amazon DocumentDB service.**
![Navigate to Amazon DocumentDB](/images/Screenshot%202026-07-09%20225845.png)

**Create the Subnet group `lms-docdb-subnet-group` in VPC `LMS-VPC`.**
![Create the subnet group for DocumentDB](/images/Screenshot%202026-07-09%20225927.png)

**Add 2 private subnets (us-east-1a and us-east-1b) to the subnet group.**
![Add private subnets to the subnet group](/images/Screenshot%202026-07-09%20225932.png)

**The subnet group is created (Complete status).**
![Subnet group completed](/images/Screenshot%202026-07-09%20225936.png)

**Create the cluster: Instance-based type, engine version 5.0.0.**
![Create the DocumentDB cluster](/images/Screenshot%202026-07-09%20225950.png)

**Choose the instance class `db.t3.medium` and enable 1 replica for Multi-AZ.**
![Choose the instance class and replica](/images/Screenshot%202026-07-09%20230001.png)

**Set the administrator account (username `admin404`) and password.**
![Configure the login account](/images/Screenshot%202026-07-09%20230020.png)

**Configure networking: VPC `LMS-VPC`, subnet group `lms-docdb-subnet-group`, security group `DocumentDB-SG`.**
![Configure networking for the cluster](/images/Screenshot%202026-07-09%20230038.png)

**Keep port `27017`, enable encryption at rest using the default KMS key.**
![Configure the port and encryption](/images/Screenshot%202026-07-09%20230044.png)

**Enable Deletion protection, review the cost estimate, then Create cluster.**
![Review and create the cluster](/images/Screenshot%202026-07-09%20230052.png)

**The cluster is in the Available state; get the connection string (endpoint) for the application to use.**
![DocumentDB cluster ready and connection string](/images/Screenshot%202026-07-09%20230123.png)

</div>

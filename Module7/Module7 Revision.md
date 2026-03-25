# Module 7: Storage

## Module Overview

### Topics
- Amazon Elastic Block Store (Amazon EBS)
- Amazon Simple Storage Service (Amazon S3)
- Amazon Elastic File System (Amazon EFS)
- Amazon Simple Storage Service Glacier

### Demos
- Amazon EBS console
- Amazon S3 console
- Amazon EFS console
- Amazon S3 Glacier console

### Lab
- Working with Amazon EBS

### Activities
- Storage solution case study

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Identify the different types of storage
- Explain Amazon S3
- Identify the functionality in Amazon S3
- Explain Amazon EBS
- Identify the functionality in Amazon EBS
- Perform functions in Amazon EBS to build an Amazon EC2 storage solution
- Explain Amazon EFS
- Identify the functionality in Amazon EFS
- Explain Amazon S3 Glacier
- Identify the functionality in Amazon S3 Glacier
- Differentiate between Amazon EBS, Amazon S3, Amazon EFS, and Amazon S3 Glacier

---

# Storage Fundamentals

## Why Storage Matters in the Cloud

Cloud storage is typically:

- More reliable than traditional on-premises storage
- More scalable than traditional on-premises storage
- More secure than traditional on-premises storage

Storage is critical because applications depend on it. The module specifically notes that the following rely on data storage architecture:

- Big data analytics
- Data warehouses
- Internet of Things (IoT)
- Databases
- Backup applications
- Archive applications

---

## Main AWS Storage Types in This Module

The module introduces these broad storage categories:

- Instance store (ephemeral storage)
- Amazon EBS
- Amazon EFS
- Amazon S3
- Amazon S3 Glacier

### Instance Store
- Temporary storage attached to an Amazon EC2 instance
- Also called ephemeral storage

### Amazon EBS
- Persistent, mountable storage
- Mounted as a device to an EC2 instance
- Can be mounted only within the same Availability Zone
- Only one EC2 instance at a time can mount an EBS volume

### Amazon EFS
- Shared file system
- Multiple EC2 instances can mount it at the same time

### Amazon S3
- Persistent object storage
- Each file becomes an object
- Available through a URL
- Can be accessed from anywhere

### Amazon S3 Glacier
- Cold storage
- Designed for data that is not accessed frequently
- Good for long-term archival and compliance use cases

---

## Block Storage vs Object Storage

One of the most important storage concepts in the module is the difference between block storage and object storage.

### Block Storage
If you want to change one character in a 1-GB file:
- You change only the block that contains that character

### Object Storage
If you want to change one character in a 1-GB file:
- You must update and re-upload the entire file

### Why This Matters
This difference affects:
- Throughput
- Latency
- Cost

### Main Rule
- Block storage is usually faster and uses less bandwidth
- Object storage can be cheaper, but updates are less granular

---

# Section 1: Amazon Elastic Block Store (Amazon EBS)

## What Is Amazon EBS?

Amazon Elastic Block Store (Amazon EBS) provides persistent block storage volumes for use with Amazon EC2 instances.

### Persistent Storage Means
- Data remains after power is shut off
- Also called non-volatile storage

### Key Characteristics
- Block-level storage
- Durable
- Detachable
- Low latency
- Automatically replicated within the same Availability Zone
- Designed for high availability and durability
- Scales up or down within minutes
- You pay only for what you provision

---

## How Amazon EBS Works

Amazon EBS lets you:

- Create individual storage volumes
- Attach them to an EC2 instance
- Use them like virtual disks in the cloud

Because EBS volumes are directly attached to EC2 instances, they can provide low latency between compute and storage.

### Common Uses
- Boot volumes and storage for EC2 instances
- Data storage with a file system
- Database hosts
- Enterprise applications

### Important Limitation
An EBS volume is mounted to a single EC2 instance at a time.

---

## Backups and Snapshots

A backup of an Amazon EBS volume is called a **snapshot**.

### Snapshot Basics
- Snapshots are stored in Amazon S3
- The first snapshot is the **baseline snapshot**
- Later snapshots capture only what changed since the previous snapshot

### Why Snapshots Matter
They help with:
- Backup
- Recovery
- Disaster recovery
- Restoring a new volume at any time

### Additional Snapshot Capabilities
- Re-create a new volume from a snapshot
- Share snapshots
- Copy snapshots to different AWS Regions for greater disaster recovery protection

---

## Amazon EBS Volume Types

The module groups Amazon EBS volume types into:

## Solid State Drives (SSD)
- General Purpose SSD
- Provisioned IOPS SSD

## Hard Disk Drives (HDD)
- Throughput-Optimized HDD
- Cold HDD

### Maximum Sizes and Performance in the Module

#### General Purpose SSD
- Maximum size: 16 TiB
- Maximum IOPS per volume: 16,000
- Maximum throughput per volume: 250 MiB/s

#### Provisioned IOPS SSD
- Maximum size: 16 TiB
- Maximum IOPS per volume: 64,000
- Maximum throughput per volume: 1,000 MiB/s

#### Throughput-Optimized HDD
- Maximum size: 16 TiB
- Maximum IOPS per volume: 500
- Maximum throughput per volume: 500 MiB/s

#### Cold HDD
- Maximum size: 16 TiB
- Maximum IOPS per volume: 250
- Maximum throughput per volume: 250 MiB/s

---

## EBS Volume Type Use Cases

### General Purpose SSD
Recommended for most workloads, including:
- System boot volumes
- Virtual desktops
- Low-latency interactive applications
- Development and test environments

### Provisioned IOPS SSD
Best for:
- Critical business applications requiring sustained IOPS performance
- Large database workloads
- Data warehouses
- Workloads needing more than 16,000 IOPS or more than 250 MiB/s throughput per volume

### Throughput-Optimized HDD
Best for:
- Streaming workloads requiring consistent, fast throughput at a low price
- Big data
- Log processing

### Cold HDD
Best for:
- Throughput-oriented storage for large volumes of data that are infrequently accessed
- Scenarios where the lowest storage cost is important

### Important Rule
- Only SSDs can be used as boot volumes for EC2 instances
- HDD types cannot be used as boot volumes

---

## Amazon EBS Features

### 1. Snapshots
- Point-in-time snapshots
- Create a new volume at any time from a snapshot

### 2. Encryption
- Encrypted EBS volumes are supported
- No additional cost for encryption

### 3. Elasticity
- Increase volume capacity
- Change volume type
- Resize dynamically without stopping instances

---

## Amazon EBS Pricing

When estimating Amazon EBS cost, the module says to consider:

### 1. Volumes
- All volume types are charged by the amount provisioned per month

### 2. IOPS
- General Purpose SSD:
  - Charged mainly by provisioned storage size
- Magnetic:
  - Charged by the number of requests
- Provisioned IOPS SSD:
  - Charged by the amount of provisioned IOPS and the duration provisioned

### 3. Snapshots
- Snapshot storage adds cost per GB-month of stored data

### 4. Data Transfer
- Inbound data transfer is free
- Copying snapshots across Regions incurs outbound transfer charges
- Standard EBS snapshot storage charges then apply in the destination Region

### Main Pricing Idea
With Amazon EBS, you generally pay for:
- The size of the volume
- The type of volume
- Its performance characteristics
- Snapshots
- Cross-Region transfer when applicable

---

## Amazon EBS Recorded Demo

The module includes a recorded Amazon EBS demonstration showing how to:

- Create an Amazon General Purpose (SSD) EBS volume
- Attach the EBS volume to an EC2 instance
- Interact with the volume by using the AWS CLI
- Mount the EBS volume to the EC2 instance

---

## Lab: Working with Amazon EBS

### Lab Scenario
In this lab, you:
- Create an Amazon EBS volume
- Attach it to an Amazon EC2 instance
- Configure the instance to use the virtual disk
- Create a snapshot
- Restore from the snapshot

### Lab Final Product
- Amazon EC2 instance
- Amazon EBS volume
- Snapshot

### Lab Debrief Key Takeaways
In the lab, you:
- Created an Amazon EBS volume
- Attached the volume to an instance
- Configured the instance to use the virtual disk
- Created an Amazon EBS snapshot
- Restored the snapshot

---

## Section 1 Key Takeaways

Amazon EBS provides:

- Persistent and customizable block storage for Amazon EC2
- HDD and SSD volume types
- Replication within the same Availability Zone
- Easy and transparent encryption
- Elastic volumes
- Backup through snapshots

---

# Section 2: Amazon Simple Storage Service (Amazon S3)

## What Is Amazon S3?

Amazon S3 is object storage built to store and retrieve any amount of data from anywhere.

### Typical Sources of Data for S3
- Websites
- Mobile apps
- Corporate applications
- IoT sensors and devices

---

## Amazon S3 Basics

Amazon S3 is object-level storage.

### Important Meaning
If you want to change part of a file:
- You must update and re-upload the whole file

### Core Structure
- Data is stored as **objects**
- Objects are stored inside **buckets**

---

## Amazon S3 Overview

Amazon S3 is a managed cloud storage solution designed to scale seamlessly and provide **11 9s of durability**.

### Key Characteristics
- Data is stored as objects in buckets
- Virtually unlimited storage
- A single object can be up to **5 TB**
- Bucket names are universal and must be globally unique
- Data is stored redundantly across multiple facilities and devices in the selected Region
- You do not manage infrastructure yourself
- Amazon S3 can hold trillions of objects
- Amazon S3 can handle millions of requests per second
- Accessible over HTTP or HTTPS
- Can also be accessed privately through a VPC endpoint

### Security Controls
You can control access by using:
- IAM policies
- Bucket policies
- Per-object access control lists (ACLs)

### Default Access Behavior
- By default, your data is not shared publicly

### Encryption
- You can encrypt data in transit
- You can enable server-side encryption on objects

### Ways to Access Amazon S3
- AWS Management Console
- API
- SDKs
- Third-party tools using the API or SDKs

---

## Amazon S3 Event Notifications and Analytics

### Event Notifications
Amazon S3 can send notifications when events occur, such as:
- Object uploaded
- Object deleted

These notifications can:
- Alert you
- Trigger other processes such as AWS Lambda functions

### Storage Class Analysis
Storage class analysis helps you:
- Analyze storage access patterns
- Transition data to the right storage class
- Create better lifecycle policies
- View daily usage visualizations
- Export data for analysis by BI tools such as Amazon QuickSight

---

## Amazon S3 Storage Classes

The module lists these S3 storage classes:

- Amazon S3 Standard
- Amazon S3 Intelligent-Tiering
- Amazon S3 Standard-Infrequent Access (Amazon S3 Standard-IA)
- Amazon S3 One Zone-Infrequent Access (Amazon S3 One Zone-IA)
- Amazon S3 Glacier
- Amazon S3 Glacier Deep Archive

---

## S3 Storage Class Details

### Amazon S3 Standard
Best for frequently accessed data.

#### Characteristics
- High durability
- High availability
- High performance
- Low latency
- High throughput

#### Good For
- Cloud applications
- Dynamic websites
- Content distribution
- Mobile and gaming applications
- Big data analytics

---

### Amazon S3 Intelligent-Tiering
Designed to optimize costs automatically.

#### How It Works
- Monitors access patterns
- Moves data to the most cost-effective tier
- Moves objects not accessed for 30 consecutive days to the infrequent access tier
- Moves them back automatically if accessed again

#### Important Notes
- Small monthly monitoring and automation fee per object
- No retrieval fees
- No extra charge for moving between access tiers

#### Best For
- Long-lived data
- Unknown or unpredictable access patterns

---

### Amazon S3 Standard-IA
Used for data accessed less frequently but requiring rapid access.

#### Characteristics
- Same durability as S3 Standard
- Low per-GB storage price
- Retrieval fee applies
- Good balance between cost and performance

#### Good For
- Long-term storage
- Backups
- Disaster recovery files

---

### Amazon S3 One Zone-IA
Used for infrequently accessed data that still needs rapid access, but at lower cost.

#### Characteristics
- Stores data in a single Availability Zone
- Costs less than Standard-IA
- Lower availability and resilience than Standard and Standard-IA

#### Good For
- Secondary backup copies of on-premises data
- Easily re-creatable data
- Replicated data from another AWS Region

---

### Amazon S3 Glacier
Used for low-cost data archiving.

#### Characteristics
- Secure
- Durable
- Low cost
- Good for long-term archival
- Supports lifecycle transfer from active S3 storage classes

#### Retrieval Time
- A few minutes to hours depending on retrieval option

---

### Amazon S3 Glacier Deep Archive
Lowest-cost S3 storage class.

#### Good For
- Long-term retention
- Digital preservation
- Data accessed once or twice a year
- Regulatory compliance retention for 7–10 years or more
- Backup and disaster recovery

#### Important Characteristics
- Designed for 11 9s of durability
- Replicated across at least three geographically dispersed Availability Zones
- Restore time can be within 12 hours

---

## Buckets, Objects, and URLs

To use S3 effectively, you must understand:

### Bucket
- Logical container for objects
- Must be globally unique
- Associated with a specific AWS Region
- Can have its own permissions and access logs

### Object
- The actual file stored in a bucket
- Includes data plus metadata
- Uploaded into a bucket

### Upload Process
1. Create a bucket in an AWS Region
2. Upload almost any number of objects into the bucket

### Bucket URL Styles
The module shows two bucket URL styles:

#### Path-Style
`https://s3.ap-northeast-1.amazonaws.com/bucket-name`

#### Virtual Hosted-Style
`https://bucket-name.s3-ap-northeast-1.amazonaws.com`

### Important Rule
Bucket names must be:
- Globally unique
- DNS-compliant

---

## Data Durability and Regional Storage

When you create an S3 bucket:
- It belongs to a specific AWS Region
- Data is stored redundantly across multiple AWS facilities in that Region

Amazon S3 is designed to:
- Durably store your data
- Tolerate concurrent data loss in two AWS facilities

---

## S3 Scaling

Amazon S3 automatically manages storage growth.

### Key Points
- No need to provision storage capacity
- No need to provision throughput
- Storage grows with application needs
- Scales to a high volume of requests
- You are billed only for what you use

---

## Common Use Cases for Amazon S3

### General Use Cases
- Storing application assets
- Static web hosting
- Backup and disaster recovery
- Staging area for big data
- Many more

### Common Scenarios in the Module
- Backup and storage
- Application hosting
- Media hosting
- Software delivery

### What These Mean
- **Backup and storage**: Provide backup and storage services for others
- **Application hosting**: Deploy, install, and manage web applications
- **Media hosting**: Highly available hosting for video, photo, or music uploads and downloads
- **Software delivery**: Host software applications for customer download

---

## Amazon S3 Pricing

With Amazon S3, costs vary by:
- Region
- Specific request types
- Storage class
- Data transfer patterns

### You Pay For
- GBs per month
- Transfer OUT to other Regions
- PUT requests
- COPY requests
- POST requests
- LIST requests
- GET requests

### You Do Not Pay For
- Transfers IN to Amazon S3
- Transfers OUT from Amazon S3 to Amazon CloudFront or Amazon EC2 in the same Region

---

## Amazon S3 Cost Estimation Factors

### 1. Storage Class Type
The module specifically compares:

#### Standard Storage
- 11 9s of durability
- Four 9s of availability

#### S3 Standard-IA
- 11 9s of durability
- Three 9s of availability

### 2. Amount of Storage
- Number of objects
- Size of objects

### 3. Requests
Consider:
- Number of requests
- Type of requests

#### Examples
- GET = retrieve an object
- PUT = add an object
- COPY = copy an existing object

### 4. Data Transfer
- Data transfer in is free
- Data transfer out is charged

---

## Amazon S3 Recorded Demo

The module includes a recorded S3 demonstration showing how to:

- Create an Amazon S3 bucket
- Upload files and create folders
- Change bucket settings
- Review common S3 bucket settings

---

## Section 2 Key Takeaways

Amazon S3 is:

- A fully managed cloud storage service
- Capable of storing a virtually unlimited number of objects
- Priced on pay-for-what-you-use
- Accessible anytime from anywhere through a URL
- Rich in security controls

---

# Section 3: Amazon Elastic File System (Amazon EFS)

## What Is Amazon EFS?

Amazon EFS provides simple, scalable, elastic file storage for use with AWS services and on-premises resources.

### Main Idea
It is shared file storage over a network.

### Important Protocol
Amazon EFS uses:
- Network File System (NFS)
- Specifically NFS versions 4.0 and 4.1

---

## Amazon EFS Overview

Amazon EFS is designed to:

- Scale dynamically on demand
- Grow automatically as files are added
- Shrink automatically as files are removed
- Avoid disruption to applications

### Main Benefits
- Simple interface
- Quick creation and configuration
- Elastic capacity
- Shared storage
- Fully managed service
- No minimum fee
- No setup costs
- Pay only for what you use

---

## Amazon EFS Features

The module highlights these EFS features:

- File storage in the AWS Cloud
- Good for big data and analytics
- Good for media processing workflows
- Good for content management
- Good for web serving
- Good for home directories
- Petabyte-scale, low-latency file system
- Shared storage
- Elastic capacity
- Supports NFSv4
- Compatible with Linux-based Amazon EC2 AMIs

---

## Accessing Amazon EFS

With Amazon EFS, you can:

- Create a file system
- Mount it on an EC2 instance
- Read and write data over the network

### Important Access Pattern
- Multiple EC2 instances can access the same EFS file system concurrently
- EC2 instances can be in multiple Availability Zones within the same Region
- Many users and instances can share a common data source

---

## Amazon EFS Architecture

The module shows an EFS architecture with:

- A VPC
- Multiple Availability Zones
- Private subnets
- One mount target in each Availability Zone
- Network interfaces connected to the EFS file system

### Important Recommendation
Access the file system from a mount target in the same Availability Zone when possible.

### Important Rule
A mount target is created in one subnet per Availability Zone.

---

## Amazon EFS Implementation Steps

The module gives five steps for implementing EFS:

1. Create Amazon EC2 resources and launch an instance
2. Create the Amazon EFS file system
3. Create mount targets in the appropriate subnets
4. Connect the EC2 instance to the EFS file system
5. Verify resources and protect the AWS account

---

## Amazon EFS Resources

### Primary Resource: File System
Each file system has properties such as:
- ID
- Creation token
- Creation time
- File system size in bytes
- Number of mount targets
- File system state

### Mount Targets
To access an EFS file system, you must create mount targets in your VPC.

Each mount target has:
- Mount target ID
- Subnet ID
- File system ID
- IP address for mounting
- Mount target state

### Tags
- Key-value pairs
- Used to organize file systems

### Important Rules
- Create mount targets in VPC subnets
- One mount target per Availability Zone
- Mount targets must be in the same VPC as the file system

---

## Amazon EFS Recorded Demo

The module includes a recorded EFS demo showing how to:

- Create an EFS implementation in a VPC
- Attach the EFS
- Configure security and performance settings
- Get instructions to validate the EFS installation and connect it to EC2 instances

---

## Section 3 Key Takeaways

Amazon EFS:

- Provides file storage over a network
- Works well for big data and analytics, media processing workflows, content management, web serving, and home directories
- Is a fully managed service that removes storage administration tasks
- Is accessible from the console, API, or CLI
- Scales up or down as files are added or removed
- Charges only for what you use

---

# Section 4: Amazon S3 Glacier

## What Is Amazon S3 Glacier?

Amazon S3 Glacier is a secure, durable, and extremely low-cost cloud storage service for:

- Data archiving
- Long-term backup

### Main Design Goal
Store data very cheaply when immediate retrieval is not required.

---

## Key Glacier Concepts

The module highlights three Glacier terms you should know:

### 1. Archive
- Any object stored in Glacier
- Base unit of storage
- Has a unique ID
- Can also have a description

### 2. Vault
- Container for storing archives
- Created in a specific Region

### 3. Vault Access Policy
- Controls who can access data in the vault
- Controls what operations users can perform
- Each vault can have one vault access policy
- Each vault can also have one vault lock policy

### Vault Lock
Vault Lock helps enforce compliance and prevent a vault from being altered.

---

## Glacier Retrieval Options

Glacier provides three retrieval options with different times and costs:

### Expedited Retrieval
- Typically 1–5 minutes
- Highest cost

### Standard Retrieval
- Typically 3–5 hours
- Medium cost

### Bulk Retrieval
- Typically 5–12 hours
- Lowest cost

### Main Idea
You choose between speed and cost.

---

## Glacier Features

The module summarizes Glacier as:

- A data archiving service designed for security, durability, and extremely low cost
- Designed to provide 11 9s of durability for objects
- Supports encryption in transit and at rest using SSL or TLS
- Supports Vault Lock for compliance
- Very well suited for long-term archiving

---

## Lifecycle Archiving from S3 to Glacier

You can configure lifecycle archiving of Amazon S3 content to Amazon S3 Glacier.

### Example in the Module
- Archive after 30 days
- Delete after 5 years

This shows how Glacier is commonly used as the colder archive layer after data ages in S3.

---

## Amazon S3 Glacier Use Cases

The module lists these use cases:

- Media asset archiving
- Healthcare information archiving
- Regulatory and compliance archiving
- Scientific data archiving
- Digital preservation
- Magnetic tape replacement

### Why These Fit Glacier
These use cases often need:
- Long retention
- Low cost
- High durability
- Infrequent access

---

## Using Amazon S3 Glacier

You can use the AWS Management Console for some Glacier tasks, such as:

- Creating vaults
- Deleting vaults
- Creating and managing archive policies

For many other operations, the module says you generally use:

- Amazon S3 Glacier REST APIs
- AWS Java SDK
- AWS .NET SDK
- AWS CLI
- Amazon S3 lifecycle policies

---

## Lifecycle Policies

You should automate data lifecycle in Amazon S3.

### What Lifecycle Policies Do
- Move objects between storage classes based on age
- Delete objects automatically based on age
- Can be applied per object or per bucket

### Example Lifecycle Policy in the Module
- Store object in Amazon S3 Standard first
- Move to Amazon S3 Standard-IA after 30 days
- Move to Amazon S3 Glacier after 60 days
- Delete after 365 days

### Why Lifecycle Policies Matter
They reduce cost automatically as data becomes less important over time.

---

## Amazon S3 vs Amazon S3 Glacier

The module provides an important comparison.

### Similarity
Both are object storage solutions that can store a virtually unlimited amount of data.

### Key Differences

#### Average Latency
- Amazon S3: milliseconds
- Amazon S3 Glacier: minutes or hours

#### Maximum Item Size
- Amazon S3: 5 TB
- Amazon S3 Glacier: 40 TB

#### Cost per GB per Month
- Amazon S3: higher
- Amazon S3 Glacier: lower

#### Billed Requests
- Amazon S3: PUT, COPY, POST, LIST, GET
- Amazon S3 Glacier: UPLOAD and retrieval

#### Retrieval Pricing
- Amazon S3: lower
- Amazon S3 Glacier: higher per retrieval and per GB

### Main Rule
- Amazon S3 = frequent, low-latency access
- Amazon S3 Glacier = low-cost, long-term storage for infrequently accessed data

---

## Encryption and Security

### Data in Transit
With both Amazon S3 and Amazon S3 Glacier:
- Data can be transferred securely over HTTPS

### Data at Rest
#### Amazon S3 Glacier
- Data is encrypted by default

#### Amazon S3
Your application must enable server-side encryption

### Amazon S3 Server-Side Encryption Options Mentioned
- SSE-S3
- SSE-C
- SSE-KMS

### Glacier Security Model
By default:
- Only you can access your data

Access is controlled with:
- IAM

The module also notes:
- Glacier encrypts data with AES-256
- Glacier manages keys for you

---

## Amazon S3 Glacier Recorded Demo

The module includes a recorded Glacier demo showing how to:

- Create an Amazon Glacier vault
- Upload archived items to the vault using a third-party graphical interface tool

---

## Section 4 Key Takeaways

Amazon S3 Glacier is:

- A data archiving service designed for security, durability, and extremely low cost
- Priced based on Region
- Very good for long-term archiving
- Designed to provide 11 9s of durability for objects

---

# Activity: Storage Case Studies

The module includes an educator-led activity in which learners review case studies and recommend the best storage solution.

### Activity Instructions
- Break into groups of four or five
- Review the assigned case study
- Create a presentation describing the best storage solution
- Include:
  - Key factors considered
  - Any factors that might change the recommendation

---

## Case 1
A data analytics company for travel sites must store billions of customer events per day.

### Architecture Includes
- Amazon API Gateway
- Amazon Kinesis
- Amazon Kinesis Data Firehose
- AWS Lambda
- Amazon ECS
- Storage ???

---

## Case 2
A collaboration software company processes email for enterprise customers.

### Business Details
- More than 250 enterprise customers
- More than half a million users
- Must store petabytes of customer data

### Architecture Includes
- Corporate data center
- Elastic Load Balancing
- Amazon EC2 instances
- Storage ???

---

## Case 3
A data protection company must ingest and store large amounts of customer data and help customers meet compliance requirements.

### Architecture Includes
- Amazon EC2
- Amazon DynamoDB
- Clients
- Storage ???

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Identify the different types of storage
- Explain Amazon S3
- Identify the functionality in Amazon S3
- Explain Amazon EBS
- Identify the functionality in Amazon EBS
- Perform functions in Amazon EBS to build an Amazon EC2 storage solution
- Explain Amazon EFS
- Identify the functionality in Amazon EFS
- Explain Amazon S3 Glacier
- Identify the functionality in Amazon S3 Glacier
- Differentiate between Amazon EBS, Amazon S3, Amazon EFS, and Amazon S3 Glacier

---

## Knowledge Check
- Complete the knowledge check at the end of the module

---

## Sample Exam Question

### Question
A company wants to store data that is not frequently accessed. What is the best and cost-effective solution that should be considered?

### Choices
- A. AWS Storage Gateway
- B. Amazon Simple Storage Service Glacier
- C. Amazon Elastic Block Store (Amazon EBS)
- D. Amazon Simple Storage Service (Amazon S3)

### Correct Answer
**B. Amazon Simple Storage Service Glacier**

### Why
The important keywords are:
- not frequently accessed
- cost-effective solution

That points directly to Amazon S3 Glacier.

---

## Additional Resources Mentioned in the Module

- AWS Storage page
- Storage Overview whitepaper
- Recovering files from an Amazon EBS volume backup
- Confused by AWS Storage Options? S3, EFS, EBS Explained

---

# Exam-Focused Final Review

## Memorize These Points

### Storage Types
- Instance store = temporary
- EBS = persistent block storage for one EC2 instance at a time
- EFS = shared file storage for multiple EC2 instances
- S3 = object storage with URL-based access
- S3 Glacier = cold archive storage

### EBS
- Block storage
- Persistent
- Replicated in one Availability Zone
- Good for boot volumes, databases, and enterprise apps
- Supports snapshots
- Supports encryption
- Supports resizing and type changes

### S3
- Object storage
- Bucket names must be globally unique
- Single object size limit = 5 TB
- Designed for 11 9s of durability
- Good for static websites, backups, application assets, media hosting, and software delivery
- Pay for storage, requests, and transfer out
- Transfer in is free

### EFS
- File storage over a network
- Uses NFS
- Shared by multiple EC2 instances
- Good for analytics, media workflows, content management, web serving, and home directories
- Automatically scales up and down
- Pay only for what you use

### Glacier
- Best for infrequently accessed data
- Extremely low cost
- Retrieval is slower than S3
- Good for archives, compliance, preservation, and long-term backup
- Retrieval options:
  - Expedited
  - Standard
  - Bulk

### S3 vs Glacier
- S3 = fast access, higher storage cost
- Glacier = slower access, lower storage cost
- S3 single object max = 5 TB
- Glacier item max = 40 TB

### Pricing Ideas
- EBS = pay for provisioned storage, IOPS model, snapshots, and some transfer
- S3 = pay for storage class, object count and size, request type, and transfer out
- EFS = pay for storage used
- Glacier = low storage cost, slower retrieval, retrieval pricing depends on access type

---

# One-Line Summary

Module 7 explains the main AWS storage options, how block, file, object, and archive storage differ, when to use Amazon EBS, Amazon S3, Amazon EFS, and Amazon S3 Glacier, and how storage choice affects performance, durability, access pattern, and cost.
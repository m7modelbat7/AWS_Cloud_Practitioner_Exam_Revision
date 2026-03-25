# Module 8: Databases

## Module Overview

### Topics
- Amazon Relational Database Service (Amazon RDS)
- Amazon DynamoDB
- Amazon Redshift
- Amazon Aurora

### Demos
- Amazon RDS console
- Amazon DynamoDB console

### Lab
- Lab 5: Build Your DB Server and Interact with Your DB Using an App

### Activity
- Database case studies

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Explain Amazon Relational Database Service (Amazon RDS)
- Identify the functionality in Amazon RDS
- Explain Amazon DynamoDB
- Identify the functionality in Amazon DynamoDB
- Explain Amazon Redshift
- Explain Amazon Aurora
- Perform tasks in an RDS database, such as launching, configuring, and interacting

---

# Module Introduction

The business world is constantly changing and evolving. By accurately recording, updating, and tracking data on an efficient and regular basis, companies can use the immense potential from the insights that they obtain from their data.

Database management systems are the crucial link for managing this data.

Like other cloud services, cloud databases offer significant cost advantages over traditional database strategies.

### Core Ideas Introduced in This Module
- Different database services in the cloud
- Differences between unmanaged and managed database solutions
- Differences between SQL and NoSQL databases
- Availability differences between alternative database solutions

### Main Goal
The goal of this module is to help you understand the database resources that are available to power your solution and how different database choices affect things such as availability and scalability.

---

# Section 1: Amazon Relational Database Service (Amazon RDS)

## Managed Versus Unmanaged Services

AWS solutions typically fall into one of two categories:

### Unmanaged
- Scaling is managed by you
- Fault tolerance is managed by you
- Availability is managed by you
- Gives more fine-tuned control
- Requires more administration

### Managed
- You still configure the service
- Scaling is typically built in
- Fault tolerance is typically built in
- Availability is typically built in
- Requires less administration

### Example
- A web server on Amazon EC2 is an unmanaged solution unless you add extra scaling and recovery logic
- A static website on Amazon S3 benefits from built-in scaling, fault tolerance, and availability because S3 is managed

---

## Challenges of Running Relational Databases Yourself

When you run your own relational database, you are responsible for:

- Server maintenance and energy footprint
- Software installation and patches
- Database backups
- High availability
- Scalability planning
- Data security
- Operating system installation and patches

### Main Problem
These tasks consume time, expertise, and operational effort.

---

## What Is Amazon RDS?

Amazon RDS is a managed service that sets up and operates a relational database in the cloud.

### Main Benefits
- Cost-efficient
- Resizable capacity
- Automates time-consuming administrative tasks
- Lets you focus on your application and data
- Helps provide performance, high availability, security, and compatibility

---

## From On-Premises to Amazon RDS

### On-Premises Database
You manage everything, including:
- Hardware
- Networking
- Power
- Operating system
- Database software
- Backups
- High availability
- Scaling
- Application optimization

### Database on Amazon EC2
AWS provides:
- Underlying hardware
- Data center operations

You still manage:
- Operating system patching
- Database software
- Backups
- High availability
- Scaling
- Application optimization

### Database on Amazon RDS or Amazon Aurora
AWS manages:
- OS installation and patching
- Database software installation and patching
- Database backups
- High availability
- Scaling
- Server maintenance
- Power
- Racking and stacking servers

You manage:
- Application optimization

### Main Idea
Amazon RDS significantly reduces database administration work.

---

## Amazon RDS Responsibilities

### You Manage
- Application optimization

### AWS Manages
- Operating system installation and patches
- Database software installation and patches
- Database backups
- High availability
- Scaling
- Power and server infrastructure
- Server maintenance

---

## Amazon RDS DB Instances

The basic building block of Amazon RDS is the **DB instance**.

### A DB Instance Is
- An isolated database environment
- Able to contain multiple user-created databases
- Accessible using the same tools and applications you use with standalone databases

### DB Instance Class Determines
- CPU
- Memory
- Network performance

### DB Storage Options Mentioned
- Magnetic
- General Purpose SSD
- Provisioned IOPS

### Database Engines Mentioned Across the Module
- Amazon Aurora
- PostgreSQL
- MySQL
- MariaDB
- Oracle
- Microsoft SQL Server
- IBM DB2

### Main Idea
You can customize performance and cost by choosing the instance class, storage type, and engine.

---

## Amazon RDS in a VPC

Amazon RDS can run inside an Amazon VPC.

### Why This Matters
- You control the networking environment
- You choose IP ranges
- You create subnets
- You configure routes and ACLs

### Common Design Pattern
- Database is usually placed in a private subnet
- Application servers access the database
- The database is not usually exposed directly to the internet

### Important Detail
A subnet belongs to one Availability Zone, so the subnet selection also determines the database location.

---

## High Availability with Multi-AZ Deployment

One of the most powerful Amazon RDS features is **Multi-AZ deployment**.

### How It Works
- Amazon RDS creates a standby copy of the database in another Availability Zone
- Transactions are synchronously replicated to the standby
- If the primary fails, Amazon RDS automatically promotes the standby

### Benefits
- Enhanced availability during maintenance
- Protection against DB instance failure
- Protection against Availability Zone disruption
- Reduced chance of data loss

### Important Detail
Applications connect using the Amazon RDS DNS endpoint, so you usually do not need to change application code during failover.

---

## Amazon RDS Read Replicas

Amazon RDS supports **read replicas** for:
- MySQL
- MariaDB
- PostgreSQL
- Amazon Aurora

### Read Replica Characteristics
- Uses asynchronous replication
- Can be promoted to primary manually if needed
- Helps scale read-heavy workloads
- Can offload read queries from the primary database
- Can be placed in another AWS Region

### Main Uses
- Improve read performance
- Disaster recovery
- Lower read latency for users in other Regions

### Important Difference
- **Multi-AZ** is mainly for high availability
- **Read replicas** are mainly for read scaling

---

## Amazon RDS Use Cases

Amazon RDS works well for:

### Web and Mobile Applications
- High throughput
- Massive storage scalability
- High availability

### Ecommerce Applications
- Low-cost database
- Data security
- Fully managed solution

### Mobile and Online Games
- Rapid growth in capacity
- Automatic scaling
- Database monitoring

---

## When to Use Amazon RDS

Use Amazon RDS when your application requires:

- Complex transactions or complex queries
- A medium to high query or write rate
- Up to 30,000 IOPS
- No more than a single worker node or shard
- High durability

### Do Not Use Amazon RDS When Your Application Requires
- Massive read/write rates such as 150,000 writes per second
- Sharding because of very high data size or throughput demands
- Simple GET or PUT requests that a NoSQL database can handle better
- Heavy relational database customization

### Alternative Choices
If RDS is not the best fit, consider:
- Amazon DynamoDB
- A database running on Amazon EC2
- Other AWS purpose-built database services

---

## Amazon RDS Pricing Factors

When estimating Amazon RDS cost, consider:

### 1. Clock-Hour Billing
- You are charged while the instance is running

### 2. Database Characteristics
- Engine
- Size
- Memory class

### 3. DB Purchase Type
- On-Demand Instances
- Reserved Instances

### On-Demand
- Pay by the hour
- No long-term commitment

### Reserved Instances
- Low, one-time upfront payment
- Reserve for 1 year or 3 years
- Lower hourly usage cost

### 4. Number of DB Instances
- You may provision multiple DB instances to handle peak loads

### 5. Storage
- Backup storage up to 100% of provisioned database storage for an active DB instance has no extra charge
- Backup storage for terminated DB instances is charged by GB per month
- Additional backup storage beyond the provisioned amount is charged by GB per month

### 6. Requests
- Number of input and output requests affects cost

### 7. Deployment Type
- Single-AZ
- Multi-AZ

Storage and I/O charges vary depending on deployment type.

### 8. Data Transfer
- Inbound data transfer is free
- Outbound data transfer uses tiered pricing

---

## Amazon RDS Console Demo

The module includes a recorded demo that shows how to:
- Configure an Amazon RDS installation running MySQL
- Connect to the database by using a MySQL client

---

## Lab 5: Build Your DB Server and Interact with Your DB Using an App

## Lab Scenario
This lab shows how to use an AWS managed database instance to solve a relational database need.

### Lab Goals
- Launch an Amazon RDS DB instance with high availability
- Configure the DB instance to allow connections from a web server
- Open a web application and interact with the database

### Lab Tasks
- Create a VPC security group
- Create a DB subnet group
- Create an Amazon RDS DB instance
- Interact with the database

### Lab Final Product
- Web server
- VPC
- Private subnets
- DB subnet group
- Security groups
- RDS DB primary
- RDS DB secondary
- Multi-AZ high availability setup

### Lab Debrief
In the lab, you:
- Created a VPC security group
- Created a DB subnet group
- Created an Amazon RDS DB instance
- Interacted with the database

---

## Section 1 Key Takeaways

Amazon RDS:

- Lets you set up, operate, and scale relational databases in the cloud
- Is a managed service
- Is accessible by console, AWS CLI, and API calls
- Scales compute and storage
- Provides automated redundancy and backups
- Supports major relational database engines
- Works well when you need relational features without managing the full infrastructure yourself

---

# Section 2: Amazon DynamoDB

## Relational Versus Non-Relational Databases

### Relational (SQL)
- Data stored in rows and columns
- Fixed schema
- Uses SQL
- Scales vertically
- Good for structured data and strong relationships between tables

### Non-Relational (NoSQL)
- Data stored as key-value, document, or graph models
- Dynamic schema
- Often focuses on collections of documents or flexible data structures
- Scales horizontally
- Handles unstructured and semistructured data more easily

### Main Idea
DynamoDB represents the NoSQL side of AWS database services.

---

## What Is Amazon DynamoDB?

Amazon DynamoDB is a fast and flexible NoSQL database service for any scale.

### Main Features
- NoSQL database tables
- Virtually unlimited storage
- Items can have different attributes
- Low-latency queries
- Scalable read/write throughput

### Core Promise
It delivers consistent, single-digit millisecond latency at any scale.

---

## Why DynamoDB Is Powerful

### DynamoDB Provides
- Automatic partitioning as data grows
- Fault-tolerant architecture
- Storage on SSDs only
- Flexible schema
- High scale for both storage and throughput

### Storage Behavior
- There is no practical limit on the number of items in a table
- Some production tables contain billions of items

### Schema Flexibility
Items in the same table can have different attributes, which makes application evolution easier.

---

## DynamoDB Throughput and Scaling

As application usage grows, DynamoDB can scale with it.

### Throughput Options
- Manual provisioning of read/write throughput
- Automatic scaling based on observed load

### Main Benefit
DynamoDB can handle increasing read and write demand while keeping low latency.

---

## Additional DynamoDB Features

The module specifically mentions:
- Global Tables
- Encryption at rest
- Item Time-to-Live (TTL)

### Global Tables
- Automatically replicate tables across selected AWS Regions
- Help improve availability and business continuity

### TTL
- Allows automatic expiration of items

---

## DynamoDB Core Components

The core DynamoDB components are:

### Table
- A collection of data

### Item
- A uniquely identifiable group of attributes in a table

### Attribute
- A basic data element that does not need to be broken down further

---

## DynamoDB Primary Keys

DynamoDB supports two kinds of primary keys:

### 1. Partition Key
- Simple primary key
- One attribute

### 2. Partition Key and Sort Key
- Composite primary key
- Two attributes

### Why Keys Matter
Proper key design is essential for good query performance and efficient partitioning.

---

## Partitioning

As data grows, DynamoDB partitions and indexes the table by the primary key.

### Two Ways to Retrieve Data

#### Query
- Uses the primary key
- Efficient
- Takes advantage of partitioning

#### Scan
- Searches using non-key attributes
- More flexible
- Less efficient because it scans through all items

### Main Rule
Use **query** whenever possible for better performance.

---

## Items in a Table Must Have a Key

To fully benefit from DynamoDB, you should think carefully about how items are uniquely identified.

### Simple Key Example
- Product ID
- GUID
- Random identifier with uniform distribution

### Compound Key Example
- Author + title for books

### Why Compound Keys Help
They can improve how efficiently you retrieve grouped or sorted data.

---

## Where DynamoDB Works Well

DynamoDB works well for:

- Mobile applications
- Web applications
- Gaming
- Adtech
- Internet of Things (IoT) applications

### Why
- Predictable low latency
- Massive scale
- Flexible schema
- High throughput
- Global replication options

---

## DynamoDB Console Demo

The recorded demo shows how to:
- Create a DynamoDB table in the AWS Management Console
- Interact with the table using the AWS CLI
- Query the table
- Add data to the table

---

## Section 2 Key Takeaways

Amazon DynamoDB:

- Runs exclusively on SSDs
- Supports document and key-value store models
- Replicates tables automatically across chosen AWS Regions through Global Tables
- Is accessible through the console, AWS CLI, and API calls
- Provides consistent single-digit millisecond latency at any scale
- Has no practical limits on table size or throughput
- Is ideal for applications that need scale, low latency, and schema flexibility

---

# Section 3: Amazon Redshift

## What Is Amazon Redshift?

Amazon Redshift is a fast, fully managed data warehouse that makes it simple and cost-effective to analyze all your data by using standard SQL and your existing business intelligence tools.

### Main Use
It is designed for analytics and data warehousing.

---

## Why Redshift Exists

Traditional data warehouses are:
- Complex
- Expensive
- Slow to set up

Amazon Redshift is intended to be:
- Faster to set up
- Easier to scale
- More cost-effective
- Fully managed

---

## Core Redshift Capabilities

Amazon Redshift enables you to:
- Run complex analytic queries
- Analyze petabytes of structured data
- Use sophisticated query optimization
- Benefit from columnar storage
- Use massively parallel processing
- Get results in seconds for many workloads

---

## Parallel Processing Architecture

Amazon Redshift uses a leader node and compute nodes.

### Leader Node
- Manages communication with client programs
- Communicates with compute nodes
- Parses queries
- Builds execution plans
- Compiles code for query execution

### Compute Nodes
- Run compiled query code
- Return intermediate results to the leader node
- Enable parallel processing

### Main Benefit
This architecture improves analytic query performance at scale.

---

## Redshift Spectrum

Amazon Redshift Spectrum enables you to:
- Run queries against exabytes of data directly in Amazon S3

### Why It Matters
You can analyze data in S3 without loading all of it into Redshift storage first.

---

## Automation and Scaling

Amazon Redshift makes it straightforward to automate common tasks related to:

- Management
- Monitoring
- Scaling

### Main Benefits
- Easier administration
- Focus more on data and business needs
- Cluster can scale up and down with a few clicks

---

## Security

Security is built into Amazon Redshift.

### Security Features Mentioned
- Encryption at rest
- Encryption in transit

---

## Compatibility

Amazon Redshift supports:

- Standard SQL
- JDBC connectors
- ODBC connectors

### Why This Matters
You can keep using familiar SQL clients and business intelligence tools.

---

## Amazon Redshift Use Cases

### Enterprise Data Warehouse (EDW)
- Migrate at your own pace
- Experiment without large upfront cost
- Respond faster to business needs

### Big Data
- Useful for customers with large volumes of data
- Lower barrier to entry for smaller customers
- Managed service reduces operational burden

### Software as a Service (SaaS)
- Scale data warehouse capacity as demand grows
- Add analytics to applications
- Reduce hardware and software costs

---

## Pricing Notes Mentioned in the Module

The module notes that:
- You pay only for what you use
- You can get started for as little as 25 cents per hour
- At scale, Redshift can deliver storage and processing for about $1,000 per terabyte per year with 3-year Partial Upfront Reserved Instance pricing

---

## Section 3 Key Takeaways

Amazon Redshift:

- Is a fast, fully managed data warehouse service
- Scales easily with no downtime
- Uses columnar storage
- Uses parallel processing architecture
- Automatically monitors the cluster
- Includes built-in encryption
- Works well for analytics at scale

---

# Section 4: Amazon Aurora

## What Is Amazon Aurora?

Amazon Aurora is a MySQL- and PostgreSQL-compatible relational database built for the cloud.

### Main Idea
It combines:
- The performance and availability of high-end commercial databases
- The simplicity and cost-effectiveness of open-source databases

---

## Amazon Aurora Core Benefits

Amazon Aurora is:
- Enterprise-class
- Relational
- Compatible with MySQL and PostgreSQL
- Highly available
- Fully managed
- Designed for performance and reliability

### Aurora Automates
- Provisioning
- Patching
- Backup
- Recovery
- Failure detection
- Repair

---

## Service Benefits

The module highlights these advantages:

- Highly available
- Fast distributed storage subsystem
- Easy to set up
- Uses SQL queries
- Drop-in compatibility with MySQL and PostgreSQL in many cases
- Pay-as-you-go pricing

### Migration Support
Aurora integrates with:
- AWS Database Migration Service (AWS DMS)
- AWS Schema Conversion Tool

These help move datasets into Aurora.

---

## High Availability

Aurora is designed to be highly available.

### It Does This By
- Storing multiple copies of your data across multiple Availability Zones
- Continuously backing up data to Amazon S3
- Supporting up to 15 read replicas
- Providing fast crash recovery

### Main Benefit
It reduces the risk of downtime and data loss.

---

## Resilient Design

Aurora is designed for fast recovery after failures.

### Important Details
- It does not need to replay the redo log from the last checkpoint in the traditional way after a crash
- It performs this work on every read operation
- Restart time after a database crash is reduced to less than 60 seconds in most cases
- Buffer cache is moved out of the database process
- Cache is available immediately at restart
- This reduces the need to throttle access after restart

---

## Security

Aurora provides multiple levels of security, including:

- Network isolation with Amazon VPC
- Encryption at rest with AWS KMS keys
- Encryption in transit with SSL

---

## Section 4 Key Takeaways

Amazon Aurora features:

- High performance and scalability
- High availability and durability
- Multiple levels of security
- Compatibility with MySQL and PostgreSQL
- Fully managed operation

### Main Summary
Aurora is a highly available, performant, and cost-effective managed relational database.

---

# Choosing the Right Database Tool

The module gives a very important mapping of requirements to services.

## The Right Tool for the Right Job

### Enterprise-Class Relational Database
- Amazon RDS

### Fast and Flexible NoSQL Database for Any Scale
- Amazon DynamoDB

### Need Operating System Access or Features Not Supported by AWS Database Services
- Databases on Amazon EC2

### Specific Case-Driven Needs Such as Machine Learning, Data Warehousing, or Graphs
- AWS purpose-built database services

### Main Idea
Modern applications often need databases that are purpose-built for their specific workload, scale, and access patterns.

---

# Database Case Study Activity

The module includes three case studies.

## Case 1
A data protection and management company:
- Provides services to enterprises
- Must support over 55 petabytes of data
- Needs:
  - Relational database for configuration data
  - Unstructured metadata store for de-duplication support
- Stores data in Amazon S3 for quick retrieval
- Eventually moves it to Amazon S3 Glacier for long-term storage

## Case 2
A commercial shipping company:
- Uses an on-premises Oracle-based legacy data management system
- Must migrate to a serverless ecosystem
- Continues using the existing Oracle system during migration
- Is decomposing highly structured relational data into semistructured data

## Case 3
An online payment processing company:
- Processes over 1 million transactions per day
- Supports ecommerce customers with flash sales
- Demand can spike 30 times in a short period
- Uses IAM and AWS KMS to authenticate with financial institutions
- Needs high throughput during peak load
- Uses read replicas in the illustrated architecture

### Activity Goal
For each case, choose the best database technology and explain:
- Key factors used in the decision
- Any factors that could change the recommendation

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Explain Amazon Relational Database Service (Amazon RDS)
- Identify the functionality in Amazon RDS
- Explain Amazon DynamoDB
- Identify the functionality in Amazon DynamoDB
- Explain Amazon Redshift
- Explain Amazon Aurora
- Perform tasks in an RDS database, such as launching, configuring, and interacting

---

## Sample Exam Question

### Question
Which of the following is a fully managed NoSQL database service?

### Choices
- Amazon Relational Database Service (Amazon RDS)
- Amazon DynamoDB
- Amazon Aurora
- Amazon Redshift

### Correct Answer
**Amazon DynamoDB**

### Why
The keyword is **NoSQL database service**. DynamoDB is the fully managed NoSQL service among these options.

---

## Additional Resources

- AWS Database page:  
  https://aws.amazon.com/products/databases/

- Amazon RDS page:  
  https://aws.amazon.com/rds/

- Overview of Amazon database services:  
  https://docs.aws.amazon.com/whitepapers/latest/aws-overview/database.html

- Getting started with AWS databases:  
  https://aws.amazon.com/products/databases/learn/

---

# Exam-Focused Final Review

## Memorize These Points

### Amazon RDS
- Managed relational database service
- Good for complex transactions and queries
- Supports Multi-AZ for high availability
- Supports read replicas for read scaling
- Best when you want relational features without managing the full infrastructure
- Not ideal for extreme write scale or heavy customization needs

### Amazon DynamoDB
- Fully managed NoSQL database
- Key-value and document store
- Single-digit millisecond latency
- Scales horizontally
- Flexible schema
- Global Tables support cross-Region replication
- Best for massive scale, low latency, and variable data structures

### Amazon Redshift
- Fully managed data warehouse
- Designed for analytics
- Uses columnar storage
- Uses massively parallel processing
- Supports SQL, JDBC, and ODBC
- Redshift Spectrum lets you query data directly in Amazon S3

### Amazon Aurora
- Managed relational database
- Compatible with MySQL and PostgreSQL
- Highly available
- Highly performant
- Continuously backs up to Amazon S3
- Supports up to 15 read replicas
- Fast crash recovery

### SQL vs NoSQL
- SQL databases use structured tables and fixed schemas
- NoSQL databases use flexible schemas and scale horizontally

### Managed vs Unmanaged
- Managed = AWS handles more operations
- Unmanaged = you handle more operations

### Right Tool Mapping
- RDS = enterprise-class relational workloads
- DynamoDB = fast NoSQL at any scale
- EC2-hosted database = when you need OS access or unsupported features
- Purpose-built AWS databases = case-specific advanced workloads

---

# One-Line Summary

Module 8 explains the main AWS database options, shows when to use Amazon RDS, DynamoDB, Redshift, and Aurora, and helps you match relational, NoSQL, analytic, and high-availability database needs to the right AWS service.
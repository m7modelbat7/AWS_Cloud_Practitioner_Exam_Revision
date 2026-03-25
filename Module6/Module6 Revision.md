# Module 6: Compute

## Module Overview

### Topics
- Compute services overview
- Amazon EC2
- Amazon EC2 cost optimization
- Container services
- Introduction to AWS Lambda
- Introduction to AWS Elastic Beanstalk

### Activities
- Amazon EC2 versus Managed Service
- Hands-on with AWS Lambda
- Hands-on with AWS Elastic Beanstalk

### Demo
- Recorded demonstration of Amazon EC2

### Lab
- Introduction to Amazon EC2

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Provide an overview of different AWS compute services in the cloud
- Demonstrate why to use Amazon Elastic Compute Cloud (Amazon EC2)
- Identify the functionality in the EC2 console
- Perform basic functions in Amazon EC2 to build a virtual computing environment
- Identify Amazon EC2 cost optimization elements
- Demonstrate when to use AWS Elastic Beanstalk
- Demonstrate when to use AWS Lambda
- Identify how to run containerized applications in a cluster of managed servers

---

# Section 1: Compute Services Overview

## AWS Compute Services

AWS offers many compute services. The module introduces these services:

- Amazon Elastic Compute Cloud (Amazon EC2)
- Amazon EC2 Auto Scaling
- Amazon Elastic Container Registry (Amazon ECR)
- Amazon Elastic Container Service (Amazon ECS)
- VMware Cloud on AWS
- AWS Elastic Beanstalk
- AWS Lambda
- Amazon Elastic Kubernetes Service (Amazon EKS)
- Amazon Lightsail
- AWS Batch
- AWS Fargate
- AWS Outposts
- AWS Serverless Application Repository

### Important Note
This module mainly focuses on the highlighted services:
- Amazon EC2
- Container services
- AWS Lambda
- AWS Elastic Beanstalk

---

## Four Broad Categories of Compute

The module groups AWS compute services into four broad categories:

### 1. Virtual Machines / Infrastructure as a Service (IaaS)
- Main example: **Amazon EC2**
- You choose:
  - Operating system
  - Server size
  - Resource capabilities
- Gives flexibility
- Leaves more server management responsibility to you

### 2. Serverless
- Main example: **AWS Lambda**
- No server provisioning or server management
- Pay only for compute time consumed
- Good for cloud-native architectures
- Can scale massively at lower cost than running servers 24/7

### 3. Container-Based Computing
- Main examples:
  - Amazon ECS
  - Amazon EKS
  - AWS Fargate
  - Amazon ECR
- Lets you run multiple workloads on one operating system
- Containers start faster than virtual machines
- Gives quick responsiveness

### 4. Platform as a Service (PaaS)
- Main example: **AWS Elastic Beanstalk**
- AWS manages:
  - Operating system
  - Application server
  - Other infrastructure components
- You focus on developing application code

---

## Compute Services Comparison

### Amazon EC2
- IaaS
- Instance-based
- Virtual machines
- You manage the machines as you choose
- Familiar to many IT professionals

### AWS Lambda
- Serverless
- Function-based
- Low cost
- Code runs on schedule or in response to events
- Best used when architecting directly for the cloud

### Amazon ECS / Amazon EKS / AWS Fargate / Amazon ECR
- Container-based
- Faster startup than traditional virtual machines
- Good for containerized workloads
- AWS Fargate reduces administrative overhead

### AWS Elastic Beanstalk
- PaaS
- Best for web applications
- Lets you focus on application code
- Integrates easily with databases, DNS, and other services
- Fast and easy to start

---

## Choosing the Optimal Compute Service

The best compute service depends on your use case.

### Questions to Ask
- What is your application design?
- What are your usage patterns?
- Which configuration settings do you want to manage?

### Best Practices
- Evaluate available compute options
- Understand the available configuration choices
- Collect compute-related metrics
- Use resource elasticity
- Re-evaluate compute needs based on metrics

### Important Idea
Choosing the wrong compute solution can reduce performance efficiency.

---

# Section 2: Amazon EC2

## What Is Amazon EC2?

Amazon Elastic Compute Cloud (Amazon EC2) provides secure, resizable compute capacity in the cloud as virtual machines called **EC2 instances**.

### Why EC2 Exists
Traditional on-premises servers are expensive because organizations must:
- Procure hardware
- Build and maintain data centers
- Staff and manage infrastructure
- Provision enough hardware for traffic spikes
- Accept long periods of idle unused capacity

EC2 solves this by providing virtual servers on demand in the AWS Cloud.

---

## Common Uses of Amazon EC2

EC2 instances can be used for many workloads, including:

- Application servers
- Web servers
- Database servers
- Game servers
- Mail servers
- Media servers
- Catalog servers
- File servers
- Computing servers
- Proxy servers

---

## Meaning of EC2

### Elastic
- You can increase or decrease the number of servers easily
- You can also resize existing servers

### Compute
- Servers provide CPU and memory needed to host applications and process data

### Cloud
- The virtual machines run in the AWS Cloud

---

## EC2 Core Characteristics

Amazon EC2:

- Provides Windows and Linux virtual machines in the cloud
- Gives you full administrative control over the guest operating system
- Supports many operating systems, including:
  - Windows
  - Red Hat
  - SuSE
  - Ubuntu
  - Amazon Linux
- Lets you launch any number of instances
- Lets you launch them in any Availability Zone worldwide
- Uses Amazon Machine Images (AMIs) as launch templates
- Lets you control traffic by using security groups

---

## Launching an EC2 Instance

The AWS Management Console Launch Instance Wizard walks through **nine key decisions**.

### The 9 Key Decisions
1. AMI
2. Instance type
3. Network settings
4. IAM role
5. User data
6. Storage options
7. Tags
8. Security group
9. Key pair

---

## 1. Select an AMI

An **Amazon Machine Image (AMI)** is the template used to create an EC2 instance.

### An AMI Includes
- A template for the root volume
- Launch permissions
- Block device mapping for attached volumes

### AMI Choices
- **Quick Start**  
  AWS-provided Linux and Windows AMIs
- **My AMIs**  
  AMIs that you created
- **AWS Marketplace**  
  Third-party preconfigured templates
- **Community AMIs**  
  Shared by others, use carefully and avoid in production

### Important Note
Community AMIs are not checked by AWS.

---

## Creating a New AMI

You can create an AMI from an EC2 instance.

### Example Process
1. Start from an existing AMI or imported virtual machine
2. Launch an unmodified instance
3. Modify and configure it as needed
4. Capture it as a new AMI
5. Optionally copy the AMI to other Regions

### Important Detail
When creating an AMI:
- Amazon EC2 stops the instance
- Creates a snapshot of the root volume
- Registers the snapshot as an AMI

---

## 2. Select an Instance Type

Instance types are optimized for different use cases.

### What the Instance Type Determines
- Memory (RAM)
- Processing power (CPU)
- Disk space and disk type
- Network performance

### Main Categories
- General purpose
- Compute optimized
- Memory optimized
- Storage optimized
- Accelerated computing

---

## EC2 Instance Type Naming

Example: `t3.large`

### Meaning
- `t` = family
- `3` = generation
- `large` = size

### Important Rules
- Higher generations are usually more powerful and better value
- Size affects vCPU, memory, and network bandwidth

### Example Size Progression
- `t3.large`
- `t3.xlarge`
- `t3.2xlarge`

Each larger size gives more resources.

---

## Instance Type Use Cases

### T3
- Burstable general purpose
- Good for:
  - Websites
  - Web applications
  - Development environments
  - Build servers
  - Microservices
  - Test and staging environments

### C5
- Compute optimized
- Good for:
  - Scientific modeling
  - Batch processing
  - Ad serving
  - Video encoding
  - Multiplayer gaming

### R5
- Memory optimized
- Good for:
  - High-performance databases
  - Data mining
  - In-memory databases
  - Big data real-time processing
  - Hadoop and Spark clusters

---

## Networking Features of Instance Types

Network bandwidth varies by instance type.

### Important Points
- Larger instances often provide better bandwidth
- Network-heavy workloads may require larger instance sizes
- You can improve performance by:
  - Using cluster placement groups for interdependent instances
  - Enabling enhanced networking

### Enhanced Networking Types
- **Elastic Network Adapter (ENA)**  
  Supports up to 100 Gbps
- **Intel 82599 Virtual Function interface**  
  Supports up to 10 Gbps

---

## 3. Specify Network Settings

You must choose where the instance will be deployed.

### Network Choices
- VPC
- Optional subnet
- Public IP assignment

### Important Notes
- Region must be selected before starting the wizard
- In a default VPC, a public IP is assigned by default
- In a nondefault VPC, public IP assignment depends on subnet settings
- You can override the subnet default during launch

---

## 4. Attach an IAM Role

If software on the EC2 instance needs to call other AWS services, attach an IAM role.

### Best Practice
**Never store AWS credentials directly on an EC2 instance.**

### Instead
- Attach an IAM role
- The role grants permissions to the application on the instance

### Important Detail
- The role is kept in an **instance profile**
- You can attach the role at launch or later to an existing instance

### Example
An application on an EC2 instance might use an IAM role to access an Amazon S3 bucket.

---

## 5. User Data Script

You can optionally provide a **user data script** at launch.

### Purpose
Automate installation and configuration when the instance starts.

### Common Uses
- Update OS packages
- Install software
- Configure the runtime environment
- Fetch license keys

### Important Behavior
- By default, user data runs only the **first time** the instance boots

### Example Linux User Data
```bash
#!/bin/bash
yum update -y
yum install -y wget
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
```

### Important Idea
User data can reduce the number of custom AMIs you must build and maintain.

---

## 6. Specify Storage

When launching an instance, you define storage settings.

### You Can Configure
- Root volume size
- Additional attached volumes
- Volume type
- Whether the volume is deleted when the instance is terminated
- Whether encryption is enabled

---

## EC2 Storage Options

### Amazon EBS
- Durable block storage
- Data persists independently from the instance
- If the instance stops and starts again, data remains

### EC2 Instance Store
- Temporary block storage physically attached to the host
- Good for:
  - Buffers
  - Caches
  - Scratch data
  - Temporary content
- If the instance stops because of user action or failure, the data is lost

### Other Storage Options
- Amazon EFS
- Amazon S3

---

## Example: EBS vs Instance Store

### Instance 1
- Root volume on Amazon EBS
- Additional EBS volume
- Additional Instance Store volume

If the instance stops and starts again:
- OS remains
- EBS data remains
- Instance Store data is lost

### Instance 2
- Root volume on Instance Store

If the instance stops:
- The instance is terminated
- Root volume data is lost
- OS is lost
- You cannot restart it

### Important Rule
Do not rely on Instance Store for valuable long-term data.

---

## 7. Add Tags

A **tag** is a label attached to an AWS resource.

### Tag Structure
- Key
- Optional value

### Common Uses
- Purpose
- Owner
- Environment
- Filtering
- Automation
- Cost allocation
- Access control

### Important Note
Tag keys and values are case-sensitive.

### Best Practice
Use a consistent tagging strategy.

---

## 8. Security Group Settings

A security group acts as a virtual firewall for one or more EC2 instances.

### Security Group Characteristics
- Exists outside the guest operating system
- Controls inbound and outbound traffic
- Rules specify:
  - Port number
  - Protocol
  - Source or destination

### Example Rule
- SSH
- TCP
- Port 22
- Source: My IP

### Important Note
After launch, you can still change security groups for the instance.

---

## 9. Identify or Create a Key Pair

Amazon EC2 uses public-key cryptography for secure access.

### A Key Pair Consists Of
- Public key stored by AWS
- Private key file stored by you

### Windows Use
- Use the private key to retrieve the administrator password
- Connect by Remote Desktop Protocol (RDP)

### Linux Use
- Use the private key for SSH access

### Important Warning
If you create a new key pair during launch, download and save the private key immediately.  
That is your only chance to save it.

---

## EC2 Console View

After launch, the EC2 console shows details such as:
- Public IP address
- Private IP address
- DNS name
- Instance type
- Instance ID
- AMI ID
- VPC ID
- Subnet ID

Many of these items are links to related resources.

---

## Launching EC2 with the AWS CLI

You can also launch EC2 instances programmatically by using:
- AWS CLI
- AWS SDKs

### CLI Command Parameters Commonly Used
- `image-id`
- `count`
- `instance-type`
- `key-name`
- `security-groups`
- `region`

### The Command Works If
- Syntax is correct
- Required resources already exist
- You have permissions
- Your account has enough capacity

---

## EC2 Instance Metadata

Running EC2 instances can access metadata about themselves.

### Metadata Can Include
- Public IP address
- Private IP address
- Hostname
- Instance ID
- Security groups
- Region
- Availability Zone

### Important Use
Metadata can be used by scripts to configure applications or the operating system automatically.

---

## Amazon CloudWatch for Monitoring EC2

Use Amazon CloudWatch to monitor EC2 instances.

### CloudWatch Features
- Near-real-time metrics
- Graphs in the EC2 console
- 15 months of historical data

### Monitoring Types
- **Basic monitoring**
  - Default
  - No extra cost
  - Data every 5 minutes
- **Detailed monitoring**
  - Additional charge
  - Data every 1 minute

### Important Note
By default, CloudWatch does not collect RAM metrics for EC2 unless you configure it.

---

## Section 2 Key Takeaways

- Amazon EC2 enables you to run Windows and Linux virtual machines in the cloud
- You launch EC2 instances from an AMI template into a VPC in your account
- You can choose from many instance types. Each instance type offers different combinations of CPU, RAM, storage, and networking capabilities
- You can configure security groups to control access to instances
- User data enables you to specify a script to run the first time that an instance launches
- Only instances that are backed by Amazon EBS can be stopped
- You can use Amazon CloudWatch to capture and review metrics on EC2 instances

---

## Recorded Amazon EC2 Demonstration

The recorded demonstration shows how to:
- Use the AWS Management Console to launch an EC2 instance
- Connect to a Windows instance by using a Remote Desktop client
- Use the selected key pair to decrypt the Windows password
- Terminate the instance after it is no longer needed

---

## Lab 3: Introduction to Amazon EC2

### Lab Purpose
Use the AWS Management Console to launch and manage an EC2 instance.

### Lab Tasks
- Task 1 – Launch an instance and explore the EC2 console
- Task 2 – Connect to the EC2 instance
- Task 3 – View the system log
- Task 4 – Reconfigure the security group
- Task 5 – Explore EC2 limits
- Task 6 – Test termination protection

### Lab Final Product
By the end of the lab, you will have:
1. Launched an instance that is configured as a web server
2. Viewed the instance system log
3. Reconfigured a security group
4. Modified the instance type and root volume size

### Lab Architecture
- Amazon EC2 instance
- Security group
- VPC
- Amazon EBS root volume
- AMI

---

## Activity: Amazon EC2 Versus Managed Service

This activity compares running a database on:
- Amazon EC2
- Amazon RDS

### Main Tradeoff

#### Amazon RDS
- Easier management
- Built-in managed backup and restore
- Can reduce operational burden
- Can be less expensive when considering the full operational picture

#### Amazon EC2
- Gives total control
- Good if you have skilled DB administrators
- Good if you need very specific deployment control

### Important Insight
Even if EC2 seems cheaper at first, Amazon RDS can be less expensive overall when you include operational effort, automation, and managed recovery.

---

# Section 3: Amazon EC2 Cost Optimization

## EC2 Pricing Models

Amazon EC2 provides several pricing models.

### 1. On-Demand Instances
- Pay by the hour
- No long-term commitments
- Lowest upfront cost
- Eligible for AWS Free Tier
- Good for:
  - Short-term workloads
  - Spiky workloads
  - Unpredictable workloads
  - Development and testing

### 2. Dedicated Hosts
- Physical servers dedicated to your use
- Good for:
  - Existing per-socket, per-core, or per-VM licenses
  - Compliance and regulatory requirements

### 3. Dedicated Instances
- Run in a VPC on hardware dedicated to one customer
- Physically isolated from other customers at the host level

### 4. Reserved Instances
- Reserve capacity for 1-year or 3-year terms
- Lower hourly running costs
- Good for predictable and steady-state workloads
- Payment choices:
  - Full upfront
  - Partial upfront
  - No upfront

### 5. Scheduled Reserved Instances
- Capacity reservation on a recurring daily, weekly, or monthly schedule
- 1-year term
- You pay for scheduled time whether used or not

### 6. Spot Instances
- Use unused EC2 capacity
- Prices fluctuate based on supply and demand
- Can be interrupted with a 2-minute warning
- Interruption behavior can be:
  - Terminate
  - Stop
  - Hibernate
- Can be significantly cheaper than On-Demand
- Good when workloads can tolerate interruption

---

## Per-Second Billing

Per-second billing is available for:
- On-Demand Instances
- Reserved Instances
- Spot Instances

### Condition
Only for instances running:
- Amazon Linux
- Ubuntu

---

## Pricing Model Benefits by Use Case

### On-Demand Instances
Best for:
- Flexibility
- Short-term needs
- Spiky or unpredictable workloads

### Spot Instances
Best for:
- Time-insensitive workloads
- Fault-tolerant applications
- Web servers
- API backends
- Big data processing
- Workloads writing frequently to persistent storage such as S3

### Reserved Instances
Best for:
- Predictable
- Long-term
- Consistent usage patterns

### Dedicated Hosts
Best for:
- Licensing restrictions
- Compliance requirements
- Regulatory requirements

---

## Four Pillars of Cost Optimization

The module identifies four pillars:

### 1. Right Size
- Select the correct instance type and size
- Avoid overprovisioning
- Resize instances based on actual usage

### 2. Increase Elasticity
- Scale resources up and down as demand changes
- Avoid paying for idle capacity

### 3. Optimal Pricing Model
- Choose the right pricing option
- Match On-Demand, Reserved, Spot, or Dedicated models to workload patterns

### 4. Optimize Storage Choices
- Reduce storage cost while keeping needed performance and availability
- Resize EBS volumes
- Change EBS volume types
- Delete unnecessary EBS snapshots
- Choose the best destination for specific data
- Consider whether the instance must use EBS
- Use Amazon S3 lifecycle policies when appropriate

---

## Measure, Monitor, and Improve

Cost optimization is not a one-time task.

### Recommendations
- Define and enforce cost allocation tagging
- Define metrics and cost targets
- Review regularly
- Encourage teams to architect for cost
- Assign optimization responsibility to a person or team
- Use AWS Cost Explorer
- Use AWS Trusted Advisor for guidance

---

## Section 3 Key Takeaways

- EC2 pricing models include:
  - On-Demand Instances
  - Reserved Instances
  - Spot Instances
  - Dedicated Instances
  - Dedicated Hosts
- Spot Instances can be interrupted with a 2-minute notification
- The four pillars of cost optimization are:
  - Right size
  - Increase elasticity
  - Optimal pricing model
  - Optimize storage choices

---

# Section 4: Container Services

## Container Basics

Containers are a method of operating system virtualization.

### Containers Package
- Application code
- Dependencies
- Configurations
- Libraries
- System tools
- Runtime

### Main Benefits
- Repeatable environments
- Self-contained environments
- Consistent behavior across environments
- Faster launch and stop times than virtual machines
- Improved developer productivity
- Better version control
- Better resource efficiency

### Important Difference from Virtual Machines
- Containers do **not** contain a full operating system
- They share a virtualized operating system
- They are smaller than virtual machines
- They start in hundreds of milliseconds

---

## What Is Docker?

Docker is a software platform that packages software into containers.

### Docker Helps You
- Build applications quickly
- Test applications quickly
- Deploy applications quickly

### Docker Is Best When You Want To
- Standardize environments
- Reduce language stack conflicts
- Run microservices
- Use container-based deployment
- Require portability for data processing

---

## Containers Versus Virtual Machines

### Virtual Machines
- Each VM has its own guest operating system
- More overhead
- Larger footprint

### Containers
- Share the operating system
- Smaller footprint
- Faster startup
- Better portability

---

## Amazon Elastic Container Service (Amazon ECS)

Amazon ECS is a highly scalable, high-performance container management service that supports Docker containers.

### Main Benefits
- Orchestrates Docker containers
- Maintains and scales the fleet of nodes
- Removes complexity of managing infrastructure
- Integrates with familiar AWS services:
  - Elastic Load Balancing
  - Security groups
  - Amazon EBS
  - IAM roles

### ECS Capabilities
- Launch tens of thousands of containers in seconds
- Monitor deployment
- Manage cluster state
- Schedule containers using:
  - Built-in scheduler
  - Third-party schedulers

### Important Note
Amazon ECS clusters can use:
- Spot Instances
- Reserved Instances

---

## Amazon ECS Task Concepts

### Task Definition
A text file describing up to 10 containers that form an application.

It defines:
- Containers to use
- Ports to open
- Volumes to use

### Task
An actual running instance of a task definition inside a cluster.

### Scheduler
Places tasks within the cluster.

---

## Amazon Elastic Kubernetes Service (Amazon EKS)

Amazon EKS enables you to run Kubernetes on AWS.

### Important Notes
- Kubernetes is open-source container orchestration software
- EKS removes much of the complexity of running Kubernetes control infrastructure on AWS

---

## Amazon Elastic Container Registry (Amazon ECR)

Amazon ECR is a fully managed Docker container registry.

### It Helps You
- Store container images
- Manage container images
- Deploy container images

---

## AWS Fargate

AWS Fargate is a compute engine for containers.

### Main Benefit
It lets you run containers without managing:
- Servers
- Clusters

### Important Meaning
Fargate reduces the operational work required for container environments.

---

## Section 4 Key Takeaways

- Containers can hold everything an application needs to run
- Docker packages software into containers
- A single application can span multiple containers
- Amazon ECS orchestrates Docker containers
- Kubernetes is open-source container orchestration software
- Amazon EKS runs Kubernetes on AWS
- Amazon ECR stores, manages, and deploys Docker containers

---

# Section 5: Introduction to AWS Lambda

## What Is AWS Lambda?

AWS Lambda is an event-driven serverless compute service.

### Main Idea
You run code without provisioning or managing servers.

### How It Works
- You upload your code
- The code lives in a **Lambda function**
- The function runs only when triggered
- You pay only for the compute time consumed

---

## Serverless Computing

Serverless computing lets you build and run applications without managing servers.

### Key Benefits
- No server provisioning
- No server maintenance
- Automatic scaling
- Built-in fault tolerance
- Lower operational effort

---

## Benefits of Lambda

### 1. Supports Multiple Programming Languages
Includes:
- Java
- Go
- PowerShell
- Node.js
- C#
- Python
- Ruby

### 2. Completely Automated Administration
Lambda manages:
- Infrastructure
- Maintenance
- Security patches
- Deployment

### 3. Built-In Fault Tolerance
- Maintains compute across multiple Availability Zones
- Helps protect against machine or data center failures
- No maintenance windows or scheduled downtime

### 4. Supports Orchestration of Multiple Functions
- Works with AWS Step Functions
- Supports:
  - Sequential workflows
  - Parallel workflows
  - Branching
  - Error handling

### 5. Pay-Per-Use Pricing
- Pay only for requests served and compute time used
- Billing is measured in 100-millisecond increments

---

## Lambda Event Sources

An **event source** is an AWS service or developer-created application that triggers a Lambda function.

### Services That Can Trigger Lambda
- Amazon S3
- Amazon SNS
- Amazon CloudWatch Events
- Amazon SQS
- Amazon DynamoDB
- Amazon API Gateway
- Application Load Balancer
- Many more

### Direct Invocation Options
You can also invoke Lambda directly by using:
- Lambda console
- Lambda API
- AWS SDK
- AWS CLI
- AWS toolkits

---

## Lambda Monitoring and Logging

AWS Lambda automatically integrates with Amazon CloudWatch.

### CloudWatch Use
- Monitoring
- Logging
- Metrics
- Troubleshooting failures

### Important Note
Lambda logs requests handled by the function and stores generated logs in CloudWatch Logs.

---

## Lambda Function Configuration

When creating a Lambda function, you specify:

- Function name
- Runtime environment
- Execution role

### Then You Configure
- Trigger
- Function code
- Memory allocation
- Environment variables
- Description
- Timeout
- Optional VPC settings
- Tags
- Other settings

### Deployment Package
A Lambda deployment package is a ZIP archive containing:
- Function code
- Dependencies

---

## Lambda Quotas

### Soft Limits Per Region
- Concurrent executions = 1,000
- Function and layer storage = 75 GB

### Hard Limits Per Function
- Maximum memory allocation = 10,240 MB
- Timeout = 15 minutes
- Deployment package size = 250 MB unzipped, including layers
- Container image package size = 10 GB

### Layers
A layer is a ZIP archive containing:
- Libraries
- Custom runtime
- Other dependencies

### Benefit of Layers
- Share code across functions
- Reduce deployment package size

---

## Hands-On Activity: AWS Lambda Stopinator Function

In this activity, you create a basic Lambda function that stops an EC2 instance.

### Main Learning Goal
Understand how Lambda can automate operational tasks in AWS.

---

## Section 5 Key Takeaways

- Serverless computing lets you build and run applications without provisioning or managing servers
- AWS Lambda is a serverless compute service with built-in fault tolerance and automatic scaling
- An event source triggers a Lambda function to run
- Maximum memory allocation for one Lambda function is 10,240 MB
- Maximum run time for a Lambda function is 15 minutes

---

# Section 6: Introduction to AWS Elastic Beanstalk

## What Is AWS Elastic Beanstalk?

AWS Elastic Beanstalk is a Platform as a Service (PaaS) offering for quickly deploying, scaling, and managing web applications and services.

### Main Idea
You upload your code, and Elastic Beanstalk handles the deployment and most infrastructure operations.

---

## What Elastic Beanstalk Automatically Handles

- Infrastructure provisioning and configuration
- Deployment
- Load balancing
- Automatic scaling
- Health monitoring
- Analysis and debugging
- Logging

---

## What You Still Control

You still control things such as:
- Instance type
- Database choice
- Automatic scaling settings
- Application updates
- Server log access
- HTTPS on the load balancer
- Underlying AWS resources

### Important Idea
Elastic Beanstalk manages the platform, but you still retain resource-level control.

---

## Supported Platforms

Elastic Beanstalk supports:
- Docker
- Go
- Java
- .NET
- Node.js
- PHP
- Python
- Ruby

### Deployment Targets Mentioned
- Apache Tomcat
- Apache HTTP Server
- NGINX
- Passenger
- Puma
- Microsoft IIS

---

## Benefits of Elastic Beanstalk

### 1. Fast and Simple to Start
You can deploy using:
- AWS Management Console
- AWS CLI
- Git repository
- Eclipse
- Visual Studio

### 2. Improves Developer Productivity
You focus more on writing code and less on managing:
- Servers
- Databases
- Load balancers
- Firewalls
- Networks

### 3. Difficult to Outgrow
- Handles peaks in workload
- Automatically scales up or down
- Helps minimize costs

### 4. Complete Resource Control
- You can choose the AWS resources used
- You can take over management of some or all infrastructure pieces if needed

---

## Pricing of Elastic Beanstalk

### Important Rule
There is **no additional charge** for Elastic Beanstalk itself.

You pay only for the AWS resources that your application uses, such as:
- EC2 instances
- S3 buckets
- Load balancers
- Databases

### Important Idea
No minimum fees and no upfront commitments for Elastic Beanstalk itself.

---

## Hands-On Activity: AWS Elastic Beanstalk

This activity helps you understand why you might use Elastic Beanstalk to deploy a web application on AWS.

---

## Section 6 Key Takeaways

- AWS Elastic Beanstalk improves developer productivity
- It simplifies application deployment
- It reduces management complexity
- It supports Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker
- There is no charge for Elastic Beanstalk itself; you only pay for the AWS resources used

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Provide an overview of different AWS compute services in the cloud
- Demonstrate why to use Amazon Elastic Compute Cloud (Amazon EC2)
- Identify the functionality in the Amazon EC2 console
- Perform basic functions in Amazon EC2 to build a virtual computing environment
- Identify Amazon EC2 cost optimization elements
- Demonstrate when to use AWS Elastic Beanstalk
- Demonstrate when to use AWS Lambda
- Identify how to run containerized applications in a cluster of managed servers

---

## Knowledge Check
- Complete the knowledge check at the end of the module

---

## Sample Exam Question

### Question
Which AWS service helps developers quickly deploy resources which can make use of different programming languages, such as .NET and Java?

### Choices
- A. AWS CloudFormation
- B. AWS SQS
- C. AWS Elastic Beanstalk
- D. Amazon Elastic Compute Cloud (Amazon EC2)

### Correct Answer
**C. AWS Elastic Beanstalk**

### Why
The important keywords are:
- developers quickly deploy resources
- different programming languages

Elastic Beanstalk is designed to simplify rapid deployment of web applications across multiple supported platforms and languages.

---

## Additional Resources Mentioned in the Module

- Amazon EC2 Documentation
- Amazon EC2 Pricing
- Amazon ECS Workshop
- Running Containers on AWS
- Amazon EKS Workshop
- AWS Lambda Documentation
- AWS Elastic Beanstalk Documentation
- Cost Optimization Playbook

---

# Exam-Focused Final Review

## Memorize These Points

### Compute Categories
- EC2 = IaaS
- Lambda = serverless
- ECS / EKS / Fargate / ECR = container-based
- Elastic Beanstalk = PaaS

### EC2 Core Facts
- EC2 provides virtual machines in the cloud
- You control the guest operating system
- Instances launch from AMIs
- Security groups control traffic
- EBS-backed instances can be stopped and started again
- Instance Store is temporary

### 9 EC2 Launch Decisions
- AMI
- Instance type
- Network settings
- IAM role
- User data
- Storage options
- Tags
- Security group
- Key pair

### Instance Types
- General purpose
- Compute optimized
- Memory optimized
- Storage optimized
- Accelerated computing

### Pricing Models
- On-Demand
- Reserved Instances
- Scheduled Reserved Instances
- Spot Instances
- Dedicated Instances
- Dedicated Hosts

### Cost Optimization Pillars
- Right size
- Increase elasticity
- Optimal pricing model
- Optimize storage choices

### Containers
- Containers are lighter and faster than virtual machines
- Docker packages software into containers
- ECS orchestrates Docker containers
- EKS runs Kubernetes
- ECR stores container images
- Fargate removes server management for containers

### Lambda
- Serverless
- Event-driven
- Pay only when code runs
- Supports many languages
- Built-in fault tolerance
- Max memory = 10,240 MB
- Max timeout = 15 minutes

### Elastic Beanstalk
- PaaS for web apps
- Upload code and AWS handles deployment
- Supports multiple languages and platforms
- No additional charge for the service itself
- You pay only for underlying AWS resources

---

# One-Line Summary

Module 6 explains AWS compute options, shows how Amazon EC2 works in detail, covers EC2 cost optimization and pricing models, introduces container services, and explains when to use AWS Lambda or AWS Elastic Beanstalk for modern cloud applications.

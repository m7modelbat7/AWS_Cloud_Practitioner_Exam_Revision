# Module 3: AWS Global Infrastructure Overview

## Module Overview

### Topics
- AWS Global Infrastructure
- AWS service and service category overview

### Activities
- AWS Management Console clickthrough

### Demo
- AWS Global Infrastructure

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Identify the difference between AWS Regions, Availability Zones, and edge locations
- Identify AWS service and service categories

---

# Section 1: AWS Global Infrastructure

## AWS Global Infrastructure

The AWS Global Infrastructure is designed and built to deliver a:

- Flexible cloud computing environment
- Reliable cloud computing environment
- Scalable cloud computing environment
- Secure cloud computing environment
- High-quality global network performance

AWS continually updates its global infrastructure footprint.

### Current Infrastructure Information
The module refers to these resources for up-to-date infrastructure details:

- AWS Global Infrastructure Map
- Regions and Availability Zones page

These resources show current and planned AWS infrastructure.

---

## AWS Regions

### Definition
An **AWS Region** is a geographical area.

### Key Characteristics
- Data replication across Regions is controlled by you
- Communication between Regions uses AWS backbone network infrastructure
- Each Region provides full redundancy and connectivity to the network
- A Region typically consists of two or more Availability Zones

### Important Notes
- The AWS Cloud infrastructure is built around Regions
- A Region is a physical geographical location with one or more Availability Zones
- Availability Zones in turn consist of one or more data centers
- Regions are isolated from one another for fault tolerance and stability
- Resources in one Region are not automatically replicated to other Regions
- If data is stored in a specific Region, it is not automatically replicated outside that Region
- If business needs require replication across Regions, you must configure it

### Region Availability Notes
- Regions introduced before March 20, 2019 are enabled by default
- Regions introduced after March 20, 2019 are disabled by default
- You must enable newer Regions before using them
- You can enable or disable Regions through the AWS Management Console

### Restricted Access Examples
- AWS China accounts provide access only to the Beijing and Ningxia Regions
- AWS GovCloud (US) is designed for US government agencies and customers with specific regulatory and compliance needs

---

## Selecting a Region

When choosing the right AWS Region for your services, applications, and data, consider the following factors:

### 1. Data Governance and Legal Requirements
- Local laws might require data to stay within certain geographical boundaries
- Some laws restrict where content or services can be offered
- Compliance requirements can strongly affect Region selection

### 2. Proximity to Customers
- Hosting applications and data close to users reduces latency
- Lower latency improves the user experience

### 3. Services Available Within the Region
- Not all AWS services are available in every Region
- Before choosing a Region, verify that your required services are supported there

### 4. Costs
- AWS service pricing can vary by Region
- The same resource may cost more in one Region than another

### Key Idea
You should choose the optimal Region based on compliance, latency, service availability, and cost.

---

## Availability Zones

### Definition
Each AWS Region has multiple **Availability Zones**.

### Key Characteristics
- Each Availability Zone is a fully isolated partition of the AWS infrastructure
- Availability Zones consist of discrete data centers
- They are designed for fault isolation
- They are interconnected with other Availability Zones using high-speed private networking
- You choose your Availability Zones
- AWS recommends replicating data and resources across Availability Zones for resiliency

### Additional Details
- Each Availability Zone provides the ability to run applications and databases with higher availability, fault tolerance, and scalability than a single data center
- Each Availability Zone can include multiple data centers, typically three
- At full scale, an Availability Zone can include hundreds of thousands of servers
- Availability Zones are fully isolated partitions of the AWS Global Infrastructure
- Each Availability Zone has its own power infrastructure
- Availability Zones are physically separated by many kilometers
- All Availability Zones within a Region are generally within 100 km of each other

### Networking Between Availability Zones
- Availability Zones are interconnected with high-bandwidth, low-latency networking
- Networking is fully redundant
- Networking uses dedicated fiber
- This supports high throughput between Availability Zones
- This also enables synchronous replication between Availability Zones

### Why Availability Zones Matter
Availability Zones help build highly available applications.

If an application is distributed across multiple Availability Zones, it is better protected from issues such as:

- Lightning
- Tornadoes
- Earthquakes
- Other localized failures

### Responsibility
- You are responsible for choosing the Availability Zones where your systems will reside
- Systems can span multiple Availability Zones
- You should design systems to survive the temporary or prolonged failure of an Availability Zone

---

## AWS Data Centers

### Key Points
- AWS data centers are designed for security
- Data centers are where data resides and processing occurs
- Each data center has redundant power, networking, and connectivity
- Each data center is housed in a separate facility
- A data center typically has 50,000 to 80,000 physical servers

### Important Understanding
Customers do not directly select a specific data center for resource deployment.

The most granular level a customer typically selects is the **Availability Zone**, not the individual data center.

### Why Data Centers Matter
- The actual data physically resides in data centers
- Although failures are rare, they can affect availability in one location
- If all resources are hosted in a single affected location, they may become unavailable

### Data Center Security and Design Principles
- Each location is carefully evaluated to mitigate environmental risk
- Data centers use redundant design to tolerate failure while maintaining service levels
- Critical system components are backed up across multiple Availability Zones
- AWS continuously monitors service usage to deploy infrastructure that supports availability commitments
- Data center locations are not publicly disclosed
- Access to data centers is restricted
- In case of failure, automated processes reroute data traffic away from the affected area

### Additional Note
AWS uses custom network equipment sourced from multiple original device manufacturers (ODMs).

---

## Points of Presence

### Definition
AWS provides a global network of **Points of Presence** locations.

### Consists Of
- Edge locations
- A much smaller number of Regional edge caches

### Main Use
Points of Presence are used with **Amazon CloudFront**.

### Amazon CloudFront
Amazon CloudFront is a global **Content Delivery Network (CDN)** that delivers content to end users with reduced latency.

### Edge Locations
- Requests to services like CloudFront and Route 53 are automatically routed to the nearest edge location
- This helps lower latency
- Edge locations are located in many major cities worldwide

### Other Services That Use Points of Presence
- Amazon CloudFront
- Amazon Route 53
- AWS Shield
- AWS Web Application Firewall (AWS WAF)

### Regional Edge Caches
Regional edge caches are used by default with Amazon CloudFront.

They are useful when content:
- Is not accessed frequently enough to remain in an edge location
- Needs to be cached closer to users without going all the way back to the origin server every time

### Main Benefit
Points of Presence improve performance and help provide a better near real-time user experience.

---

## AWS Infrastructure Features

The AWS Global Infrastructure provides several major benefits.

### 1. Elasticity and Scalability
- Elastic infrastructure dynamically adapts to increases or decreases in capacity requirements
- Scalable infrastructure adjusts rapidly to accommodate growth

### 2. Fault Tolerance
- The infrastructure continues operating properly in the presence of failure
- It includes built-in redundancy of components

### 3. High Availability
- High operational performance
- Minimized downtime
- Little to no human intervention required

### Summary of Value
The AWS Global Infrastructure is designed to be:
- Elastic
- Scalable
- Fault tolerant
- Highly available

---

## Key Takeaways From Section 1

- The AWS Global Infrastructure consists of Regions and Availability Zones
- Your choice of a Region is typically based on compliance requirements or reducing latency
- Each Availability Zone is physically separate from other Availability Zones
- Each Availability Zone has redundant power, networking, and connectivity
- Edge locations and Regional edge caches improve performance by caching content closer to users

---

# Section 2: AWS Services and Service Category Overview

## AWS Foundational Services

AWS offers a broad set of global cloud-based products that can be used as building blocks for common cloud architectures.

### Infrastructure Layer
- Regions
- Availability Zones
- Edge locations

### Foundational Services Layer
- Compute
- Networking
- Storage

### Platform Services Layer
- Databases
- Analytics
- Application services
- Deployment and management
- Mobile services

### Applications Layer
- Virtual desktops
- Collaboration and sharing

### Important Idea
The AWS Global Infrastructure provides the platform on which AWS services are delivered as an on-demand utility with pay-as-you-go pricing.

---

## AWS Categories of Services

AWS offers a broad set of cloud-based services organized into service categories.

### Service Categories Listed in the Module
- Analytics
- Application Integration
- AR and VR
- Blockchain
- Business Applications
- Compute
- Cost Management
- Customer Engagement
- Database
- Developer Tools
- End User Computing
- Game Tech
- Internet of Things
- Machine Learning
- Management and Governance
- Media Services
- Migration and Transfer
- Mobile
- Networking and Content Delivery
- Robotics
- Satellite
- Security, Identity, and Compliance
- Storage

### Important Course Note
This course does not attempt to introduce every AWS service.

Instead, it focuses on:
- Services that are most widely used
- Services that best introduce the AWS Cloud
- Services likely to appear on the AWS Certified Cloud Practitioner exam

### Highlighted Categories in This Module
The module focuses especially on:

- Compute
- Cost Management
- Database
- Management and Governance
- Networking and Content Delivery
- Security, Identity, and Compliance
- Storage

---

# Storage Service Category

## AWS Storage Services Covered

- Amazon Simple Storage Service (Amazon S3)
- Amazon Elastic Block Store (Amazon EBS)
- Amazon Elastic File System (Amazon EFS)
- Amazon Simple Storage Service Glacier

---

## Amazon S3
Amazon Simple Storage Service (Amazon S3) is an **object storage service** that offers:

- Scalability
- Data availability
- Security
- Performance

### Common Uses
- Websites
- Mobile apps
- Backup and restore
- Archive
- Enterprise applications
- Internet of Things (IoT) devices
- Big data analytics

---

## Amazon EBS
Amazon Elastic Block Store (Amazon EBS) is **high-performance block storage** designed for use with Amazon EC2.

### Designed For
- Throughput-intensive workloads
- Transaction-intensive workloads

### Common Uses
- Relational databases
- Non-relational databases
- Enterprise applications
- Containerized applications
- Big data analytics engines
- File systems
- Media workflows

---

## Amazon EFS
Amazon Elastic File System (Amazon EFS) provides a **scalable, fully managed elastic Network File System (NFS)** for use with AWS Cloud services and on-premises resources.

### Key Characteristics
- Scales on demand to petabytes
- Grows automatically as files are added
- Shrinks automatically as files are removed
- Reduces the need to provision and manage capacity manually

---

## Amazon S3 Glacier
Amazon Simple Storage Service Glacier is a **secure, durable, and extremely low-cost Amazon S3 cloud storage class** for:

- Data archiving
- Long-term backup

### Key Characteristics
- Designed for 11 9s of durability
- Provides comprehensive security and compliance capabilities
- Suitable for stringent regulatory requirements

---

# Compute Service Category

## AWS Compute Services Covered

- Amazon EC2
- Amazon EC2 Auto Scaling
- Amazon Elastic Container Service (Amazon ECS)
- Amazon Elastic Container Registry (Amazon ECR)
- AWS Elastic Beanstalk
- AWS Lambda
- Amazon Elastic Kubernetes Service (Amazon EKS)
- AWS Fargate

---

## Amazon EC2
Amazon Elastic Compute Cloud (Amazon EC2) provides **resizable compute capacity as virtual machines in the cloud**.

---

## Amazon EC2 Auto Scaling
Amazon EC2 Auto Scaling enables you to **automatically add or remove EC2 instances** according to conditions that you define.

---

## Amazon ECS
Amazon Elastic Container Service (Amazon ECS) is a **highly scalable, high-performance container orchestration service** that supports Docker containers.

---

## Amazon ECR
Amazon Elastic Container Registry (Amazon ECR) is a **fully managed Docker container registry** that makes it easy to:

- Store Docker container images
- Manage Docker container images
- Deploy Docker container images

---

## AWS Elastic Beanstalk
AWS Elastic Beanstalk is a service for **deploying and scaling web applications and services** on familiar servers such as:

- Apache
- Microsoft Internet Information Services (IIS)

---

## AWS Lambda
AWS Lambda enables you to **run code without provisioning or managing servers**.

### Key Pricing Point
- You pay only for the compute time you consume
- There is no charge when your code is not running

---

## Amazon EKS
Amazon Elastic Kubernetes Service (Amazon EKS) makes it easy to **deploy, manage, and scale containerized applications that use Kubernetes on AWS**.

---

## AWS Fargate
AWS Fargate is a **compute engine for Amazon ECS** that lets you run containers **without managing servers or clusters**.

---

# Database Service Category

## AWS Database Services Covered

- Amazon Relational Database Service (Amazon RDS)
- Amazon Aurora
- Amazon Redshift
- Amazon DynamoDB

---

## Amazon RDS
Amazon Relational Database Service (Amazon RDS) makes it easy to:

- Set up a relational database in the cloud
- Operate a relational database in the cloud
- Scale a relational database in the cloud

### Key Benefits
- Resizable capacity
- Automates time-consuming administration tasks such as:
  - Hardware provisioning
  - Database setup
  - Patching
  - Backups

---

## Amazon Aurora
Amazon Aurora is a **MySQL- and PostgreSQL-compatible relational database**.

### Performance Notes
- Up to five times faster than standard MySQL databases
- Three times faster than standard PostgreSQL databases

---

## Amazon Redshift
Amazon Redshift enables you to run **analytic queries** against:

- Petabytes of data stored locally in Amazon Redshift
- Exabytes of data stored directly in Amazon S3

### Key Benefit
- Fast performance at any scale

---

## Amazon DynamoDB
Amazon DynamoDB is a **key-value and document database**.

### Key Characteristics
- Single-digit millisecond performance at any scale
- Built-in security
- Backup and restore
- In-memory caching

---

# Networking and Content Delivery Service Category

## AWS Networking and Content Delivery Services Covered

- Amazon VPC
- Elastic Load Balancing
- Amazon CloudFront
- AWS Transit Gateway
- Amazon Route 53
- AWS Direct Connect
- AWS VPN

---

## Amazon VPC
Amazon Virtual Private Cloud (Amazon VPC) enables you to **provision logically isolated sections of the AWS Cloud**.

---

## Elastic Load Balancing
Elastic Load Balancing automatically distributes incoming application traffic across multiple targets, such as:

- Amazon EC2 instances
- Containers
- IP addresses
- Lambda functions

---

## Amazon CloudFront
Amazon CloudFront is a **fast CDN service** that securely delivers:

- Data
- Videos
- Applications
- APIs

### Key Benefits
- Low latency
- High transfer speeds
- Global delivery

---

## AWS Transit Gateway
AWS Transit Gateway enables customers to connect:

- Their Amazon VPCs
- Their on-premises networks

to a **single gateway**.

---

## Amazon Route 53
Amazon Route 53 is a **scalable cloud DNS web service** designed to route end users to internet applications.

### Main Function
It translates names such as:

- `www.example.com`

into numeric IP addresses such as:

- `192.0.2.1`

that computers use to connect to each other.

---

## AWS Direct Connect
AWS Direct Connect provides a way to establish a **dedicated private network connection** from your data center or office to AWS.

### Benefits
- Can reduce network costs
- Can increase bandwidth throughput

---

## AWS VPN
AWS VPN provides a **secure private tunnel** from your network or device to the AWS global network.

---

# Security, Identity, and Compliance Service Category

## AWS Security, Identity, and Compliance Services Covered

- AWS Identity and Access Management (IAM)
- AWS Organizations
- Amazon Cognito
- AWS Artifact
- AWS Key Management Service (AWS KMS)
- AWS Shield

---

## AWS IAM
AWS Identity and Access Management (IAM) enables you to **manage access to AWS services and resources securely**.

### What You Can Do With IAM
- Create AWS users
- Create AWS groups
- Allow access using permissions
- Deny access using permissions

---

## AWS Organizations
AWS Organizations allows you to **restrict which services and actions are allowed in your accounts**.

---

## Amazon Cognito
Amazon Cognito lets you add:

- User sign-up
- User sign-in
- Access control

to your web and mobile applications.

---

## AWS Artifact
AWS Artifact provides **on-demand access** to:

- AWS security reports
- AWS compliance reports
- Select online agreements

---

## AWS KMS
AWS Key Management Service (AWS KMS) enables you to:

- Create keys
- Manage keys
- Control the use of encryption across many AWS services and applications

---

## AWS Shield
AWS Shield is a **managed Distributed Denial of Service (DDoS) protection service** that safeguards applications running on AWS.

---

# AWS Cost Management Service Category

## AWS Cost Management Services Covered

- AWS Cost and Usage Report
- AWS Budgets
- AWS Cost Explorer

---

## AWS Cost and Usage Report
The AWS Cost and Usage Report contains the **most comprehensive set of AWS cost and usage data available**.

### Includes
- Additional metadata about AWS services
- Pricing information
- Reservation information

---

## AWS Budgets
AWS Budgets enables you to **set custom budgets**.

### Alerts
It can alert you when:
- Your costs exceed your budget
- Your usage exceeds your budget
- Your costs are forecasted to exceed your budget
- Your usage is forecasted to exceed your budget

---

## AWS Cost Explorer
AWS Cost Explorer provides an **easy-to-use interface** to:

- Visualize AWS costs
- Understand AWS costs
- Manage AWS costs and usage over time

---

# Management and Governance Service Category

## AWS Management and Governance Services Covered

- AWS Management Console
- AWS Config
- Amazon CloudWatch
- AWS Auto Scaling
- AWS Command Line Interface
- AWS Trusted Advisor
- AWS Well-Architected Tool
- AWS CloudTrail

---

## AWS Management Console
The AWS Management Console provides a **web-based user interface** for accessing your AWS account.

---

## AWS Config
AWS Config helps you **track resource inventory and changes**.

---

## Amazon CloudWatch
Amazon CloudWatch allows you to **monitor resources and applications**.

---

## AWS Auto Scaling
AWS Auto Scaling provides features that allow you to **scale multiple resources to meet demand**.

---

## AWS Command Line Interface
AWS Command Line Interface provides a **unified tool to manage AWS services**.

---

## AWS Trusted Advisor
AWS Trusted Advisor helps you **optimize performance and security**.

---

## AWS Well-Architected Tool
AWS Well-Architected Tool helps you **review and improve workloads**.

---

## AWS CloudTrail
AWS CloudTrail tracks:

- User activity
- API usage

---

# Activity: AWS Management Console Clickthrough

## Purpose of the Activity
This educator-led activity is designed to help you:

- Log in to the AWS Management Console
- Navigate between AWS service consoles
- Identify service categories
- Understand whether services or resources are global or Regional

---

## Activity Steps

### 1. Launch the Sandbox
- Launch the Sandbox hands-on environment
- Connect to the AWS Management Console

### 2. Explore the AWS Management Console

#### A. Click the Services menu
- Notice how services are grouped into service categories
- Example: EC2 appears in the Compute category

#### Question 1
Under which service category does the IAM service appear?

#### Question 2
Under which service category does the Amazon VPC service appear?

#### B. Open the Amazon VPC service
- Notice the Region dropdown in the top-right corner
- It displays the current AWS Region

#### C. Change the Region
- Switch to a different Region, for example EU (London)

#### D. Open Subnets
- The Region contains three subnets
- Select a subnet
- The bottom half of the screen displays subnet details

#### Question 3
Does the selected subnet exist at the level of the Region or the level of the Availability Zone?

#### E. Open Your VPCs
- An existing VPC is already selected

#### Question 4
Does the VPC exist at the level of the Region or the level of the Availability Zone?

#### Question 5
Which of these services are global instead of Regional?

- Amazon EC2
- IAM
- Lambda
- Route 53

---

## Activity Answer Key

### Question 1
**Under which service category does the IAM service appear?**

**Answer:** Security, Identity, & Compliance

### Question 2
**Under which service category does the Amazon VPC service appear?**

**Answer:** Networking & Content Delivery

### Question 3
**Does the selected subnet exist at the level of the Region or the level of the Availability Zone?**

**Answer:** Subnets exist at the level of the Availability Zone

### Question 4
**Does the VPC exist at the level of the Region or the level of the Availability Zone?**

**Answer:** VPCs exist at the Region level

### Question 5
**Which of the following services are global instead of Regional?**

**Answer:** IAM and Route 53 are global. Amazon EC2 and Lambda are Regional.

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Identify the difference between AWS Regions, Availability Zones, and edge locations
- Identify AWS service and service categories

---

## Knowledge Check
- Complete the knowledge check at the end of the module

---

## Sample Exam Question

### Question
Which component of AWS global infrastructure does Amazon CloudFront use to ensure low-latency delivery?

### Choices
- A. AWS Regions
- B. AWS edge locations
- C. AWS Availability Zones
- D. Amazon Virtual Private Cloud (Amazon VPC)

### Correct Answer
**B. AWS edge locations**

### Why
The keywords are:
- Component of AWS global infrastructure
- CloudFront
- Low-latency

CloudFront uses **edge locations** to deliver content with low latency.

---

## Additional Resources

- AWS Global Infrastructure
- AWS Regional Services List
- AWS Cloud Products

---

# Exam-Focused Final Review

## Memorize These Points

### Global Infrastructure
- A Region is a geographical area
- A Region typically has two or more Availability Zones
- Regions are isolated from one another
- Cross-Region replication is controlled by you

### Availability Zones
- Each Region has multiple Availability Zones
- Availability Zones are isolated from each other
- They are connected by high-speed private networking
- AWS recommends replicating across Availability Zones for resiliency

### Data Centers
- Data centers are where data resides and processing occurs
- Customers select Availability Zones, not individual data centers
- Data centers have redundant power, networking, and connectivity

### Points of Presence
- Points of Presence include edge locations and Regional edge caches
- They are used to reduce latency
- CloudFront uses edge locations for low-latency delivery

### Region Selection
Choose a Region based on:
- Compliance and legal requirements
- Proximity to customers
- Service availability
- Cost

### Service Categories to Know
- Compute
- Storage
- Database
- Networking and Content Delivery
- Security, Identity, and Compliance
- Cost Management
- Management and Governance

### Global vs Regional
- IAM is global
- Route 53 is global
- Amazon EC2 is Regional
- Lambda is Regional

### Resource Scope
- A subnet exists at the Availability Zone level
- A VPC exists at the Region level

---

# One-Line Summary

Module 3 explains the AWS Global Infrastructure, the differences between Regions, Availability Zones, edge locations, and major AWS service categories, while also showing how to explore services and resource scope through the AWS Management Console.
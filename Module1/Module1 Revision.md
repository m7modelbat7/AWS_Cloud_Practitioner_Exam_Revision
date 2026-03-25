# Module 1: Cloud Concepts Overview

## Module 1 Objectives

By the end of Module 1, you should be able to:

- Define cloud computing
- Describe the different cloud service models
- Describe the different cloud deployment models
- Explain the benefits of cloud computing
- Identify the core AWS service categories
- Describe basic ways to interact with AWS
- Explain the AWS Cloud Adoption Framework (AWS CAF)

---

# 1. Introduction to Cloud Computing

## What is cloud computing?

Cloud computing is the **on-demand delivery of IT resources over the internet with pay-as-you-go pricing**.

These resources can include:

- Compute power
- Storage
- Databases
- Networking
- Applications
- Other IT services

Instead of buying and maintaining physical hardware, you use resources when needed and pay only for what you consume.

### Simple idea

Traditional IT says:

> Buy hardware first, then use it.

Cloud computing says:

> Use resources when needed, then pay for what you used.

---

## Infrastructure as software

One of the biggest mindset shifts in cloud computing is this:

- **Traditional infrastructure** is treated like **hardware**
- **Cloud infrastructure** is treated more like **software**

That means cloud resources are:

- Flexible
- Easy to provision
- Easy to terminate
- Scalable
- Temporary when needed
- Available on demand

---

## Traditional IT model

In a traditional environment, if you want to launch an application or website, you usually need to:

- Buy servers
- Install them in racks
- Secure the data center
- Plan electricity and cooling
- Hire staff for maintenance
- Estimate future capacity needs in advance

### Problems with this model

- If you buy too much capacity, you waste money
- If you buy too little capacity, performance suffers
- Procurement takes time
- Scaling later is difficult and expensive
- You spend time on maintenance instead of innovation

---

## Cloud computing model

With cloud computing:

- Resources can be created in minutes
- You do not need to buy hardware upfront
- You can scale up or down based on demand
- You avoid most of the undifferentiated heavy lifting
- You focus more on business value

Examples of undifferentiated heavy lifting:

- Racking servers
- Stacking servers
- Hardware procurement
- Data center maintenance
- Capacity planning

---

# 2. Cloud Service Models

Cloud service models differ mainly in **how much control and responsibility you have**.

## 2.1 Infrastructure as a Service (IaaS)

IaaS provides basic building blocks for cloud IT.

You typically get access to:

- Virtual servers
- Networking
- Storage

### Key point

IaaS gives you the **highest level of flexibility** and the **most management control** over your IT resources.

### Think of it as

You manage much of the environment, but the cloud provider owns the physical infrastructure.

---

## 2.2 Platform as a Service (PaaS)

PaaS removes the need to manage the underlying infrastructure.

You focus more on:

- Application deployment
- Application management
- Development workflows

The provider handles more of the lower-level environment such as:

- Hardware
- Operating systems
- Some runtime services

### Key point

PaaS helps developers focus more on building applications and less on infrastructure.

---

## 2.3 Software as a Service (SaaS)

SaaS provides a complete software product that is run and managed by the service provider.

### Example

- Web-based email

### Key point

With SaaS, you do not need to think about:

- Hardware
- Operating systems
- Maintenance
- Infrastructure management

You simply use the software.

---

## Easy comparison

- **IaaS** = most control
- **PaaS** = manage applications, not infrastructure
- **SaaS** = just use the software

---

# 3. Cloud Deployment Models

Deployment models describe **where and how applications are deployed**.

## 3.1 Cloud

In a cloud deployment model, all parts of the application run in the cloud.

The application can be:

- Designed in the cloud
- Migrated from on-premises to the cloud

### Key point

Everything runs in the cloud environment.

---

## 3.2 Hybrid

A hybrid model connects cloud resources with on-premises infrastructure.

This means some resources remain in traditional environments, while others run in the cloud.

### Key point

Hybrid is useful when an organization wants to:

- Extend existing infrastructure
- Connect cloud services to internal systems
- Move gradually to the cloud

---

## 3.3 On-premises (Private Cloud)

In this model, resources are deployed on-site using virtualization and resource management tools.

### Key point

It may use cloud-like methods, but it does not provide all the benefits of a public cloud environment.

It is often similar to a traditional IT setup.

---

## Easy comparison

- **Cloud** = everything runs in the cloud
- **Hybrid** = cloud + on-premises connected together
- **On-premises / private cloud** = local infrastructure

---

# 4. Similarities Between AWS and Traditional IT

Even though AWS is cloud-based, many concepts are familiar if you already know traditional IT.

## Examples of similarities

### Security

AWS services such as:

- Security groups
- Network ACLs
- IAM

Are conceptually similar to:

- Firewalls
- Access control lists
- Administrator permissions

### Networking

AWS services such as:

- Amazon VPC
- Elastic Load Balancing

Are similar to traditional networking components like:

- Routers
- Switches
- Network pipelines
- Load balancers

### Compute

AWS services such as:

- Amazon Machine Images (AMIs)
- Amazon EC2 instances

Are similar to:

- Traditional servers

### Storage and databases

AWS services such as:

- Amazon EBS
- Amazon EFS
- Amazon S3
- Amazon RDS

Relate to concepts like:

- DAS
- SAN
- NAS
- Relational databases

### Key takeaway

Most things you do in traditional IT can also be implemented in AWS, but in a more flexible cloud model.

---

# 5. Advantages of Cloud Computing

AWS highlights **six main advantages of cloud computing**.

These are very important for the exam.

## 5.1 Trade capital expense for variable expense

Instead of spending money upfront on data centers and servers, you pay only for what you use.

### Traditional model

- High upfront investment
- Capital expense (CapEx)

### Cloud model

- Usage-based payment
- Variable expense

### Benefit

- Lower upfront cost
- Better financial flexibility

---

## 5.2 Benefit from massive economies of scale

Because cloud providers serve many customers, they can achieve lower operational costs at scale.

These savings can be passed on to customers through lower pricing.

### Benefit

- Lower cost per unit of compute, storage, and other services

---

## 5.3 Stop guessing capacity

In traditional IT, you must estimate demand in advance.

That is risky because:

- Overestimation wastes money
- Underestimation causes performance issues

In the cloud, you can adjust capacity based on real demand.

### Benefit

- Better resource usage
- Less waste
- Better performance planning

---

## 5.4 Increase speed and agility

Cloud resources can be provisioned in minutes instead of waiting weeks or months for procurement and setup.

### Benefit

- Faster experimentation
- Faster development
- Faster innovation
- Faster deployment

---

## 5.5 Stop spending money running and maintaining data centers

You do not need to focus on tasks such as:

- Powering servers
- Cooling systems
- Racking hardware
- Stacking hardware
- Maintaining facilities

### Benefit

You focus on projects that bring business value instead of infrastructure maintenance.

---

## 5.6 Go global in minutes

You can deploy applications in multiple geographic regions quickly.

### Benefit

- Lower latency for users worldwide
- Better customer experience
- Fast international expansion

---

## Easy memory list for the six advantages

1. Trade CapEx for variable expense  
2. Benefit from economies of scale  
3. Stop guessing capacity  
4. Increase speed and agility  
5. Stop spending money on data centers  
6. Go global in minutes  

---

# 6. Introduction to AWS

## What are web services?

A web service is software that makes itself available over the internet or private networks.

It typically uses standard request and response formats such as:

- XML
- JSON

### Characteristics

- Platform independent
- Language independent
- Accessible over networks
- Used for API communication

---

## What is AWS?

Amazon Web Services (AWS) is a **secure cloud services platform**.

It offers a broad set of global cloud-based products such as:

- Compute
- Storage
- Databases
- Networking
- Security
- Analytics
- Management tools
- Application services

### Main idea

AWS gives organizations access to IT resources on demand, with flexible pricing and quick provisioning.

---

## AWS as building blocks

AWS services are designed to work together.

You can combine multiple services to create complete solutions.

### Example concept

A solution might use:

- **Amazon EC2** for compute
- **Amazon S3** for storage
- **Amazon DynamoDB** for indexing or fast access
- **Amazon VPC** for networking

### Key takeaway

AWS solutions are built by combining services from different categories.

---

# 7. AWS Service Categories

AWS services are grouped into categories.

Common categories include:

- Compute
- Storage
- Database
- Networking and Content Delivery
- Security, Identity, and Compliance
- Management and Governance
- Cost Management
- Analytics
- Machine Learning
- Migration and Transfer
- Developer Tools
- Internet of Things
- Mobile
- Media Services
- Business Applications
- End User Computing
- Application Integration
- Customer Engagement
- Blockchain
- Robotics
- AR and VR
- Game Tech

### Key point

You do not always use one service alone.  
You usually combine services from multiple categories to build a solution.

---

# 8. Choosing AWS Services

The AWS service you choose depends on:

- Your business goals
- Your technical requirements

## Compute examples from the module

### Amazon EC2

Use when you want:

- Full control over compute resources
- Virtual servers in the cloud

### AWS Lambda

Use when you want:

- To run code without managing servers

### AWS Elastic Beanstalk

Use when you want:

- Easy deployment and scaling for web applications

### Amazon Lightsail

Use when you want:

- A simple, lightweight web application environment

### AWS Batch

Use when you want:

- To run large-scale batch workloads

### AWS Outposts

Use when you want:

- AWS infrastructure inside your on-premises data center

### Amazon ECS / Amazon EKS / AWS Fargate

Use when you want:

- Container-based workloads
- Microservices

### VMware Cloud on AWS

Use when you want:

- To migrate or extend VMware-based on-premises environments into AWS

### Key lesson

There can be many AWS services in one category, and the right one depends on the use case.

---

# 9. Core AWS Services Mentioned in the Course

## Compute

- Amazon EC2
- AWS Lambda
- AWS Elastic Beanstalk
- Amazon EC2 Auto Scaling
- Amazon ECS
- Amazon EKS
- Amazon ECR
- AWS Fargate

## Security, Identity, and Compliance

- AWS IAM
- Amazon Cognito
- AWS Shield
- AWS Artifact
- AWS KMS

## Storage

- Amazon S3
- Amazon S3 Glacier
- Amazon EFS
- Amazon EBS

## Database

- Amazon RDS
- Amazon DynamoDB
- Amazon Redshift
- Amazon Aurora

## Networking and Content Delivery

- Amazon VPC
- Amazon Route 53
- Amazon CloudFront
- Elastic Load Balancing

## Management and Governance

- AWS Trusted Advisor
- Amazon CloudWatch
- AWS CloudTrail
- AWS Well-Architected Tool
- AWS Auto Scaling
- AWS CLI
- AWS Config
- AWS Management Console
- AWS Organizations

## Cost Management

- AWS Cost & Usage Report
- AWS Budgets
- AWS Cost Explorer

---

# 10. Three Ways to Interact with AWS

You can create and manage AWS resources in three main ways.

## 10.1 AWS Management Console

This is the graphical web interface.

### Best for

- Beginners
- Visual management
- Quick configuration

---

## 10.2 AWS Command Line Interface (AWS CLI)

This lets you manage AWS using commands in a terminal.

### Best for

- Automation
- Scripting
- Repetitive tasks

---

## 10.3 AWS Software Development Kits (SDKs)

SDKs allow you to interact with AWS services directly from code.

### Examples

- Python
- Java
- Other programming languages

### Best for

- Developers
- Application integration
- Programmatic control

---

## Easy comparison

- **Console** = graphical interface
- **CLI** = commands and scripts
- **SDKs** = code

---

# 11. Moving to the AWS Cloud

Cloud adoption is not just a technical change.

It also affects:

- People
- Processes
- Technology

Organizations usually do not move to the cloud instantly.

They need to understand:

- Their current state
- Their target state
- The transition plan between both

---

# 12. AWS Cloud Adoption Framework (AWS CAF)

AWS CAF helps organizations adopt the cloud successfully.

It provides:

- Guidance
- Best practices
- A structured approach
- Help in identifying skill and process gaps

### Key idea

Successful cloud adoption requires alignment across the organization.

AWS CAF organizes this using **six perspectives**.

---

## The 6 AWS CAF perspectives

The six perspectives are divided into two groups:

### Business-focused perspectives

- Business
- People
- Governance

### Technical-focused perspectives

- Platform
- Security
- Operations

---

# 13. Business Perspective

## Purpose

Ensures that IT aligns with business goals and that technology investments generate business value.

## Capabilities

- IT finance
- IT strategy
- Benefits realization
- Business risk management

## Typical stakeholders

- Business managers
- Finance managers
- Budget owners
- Strategy stakeholders

---

# 14. People Perspective

## Purpose

Supports training, staffing, and organizational changes needed to build an agile cloud-ready organization.

## Capabilities

- Resource management
- Incentive management
- Career management
- Training management
- Organizational change management

## Typical stakeholders

- Human resources
- Staffing managers
- People managers

---

# 15. Governance Perspective

## Purpose

Ensures IT goals stay aligned with business goals while maximizing value and minimizing risk.

## Capabilities

- Portfolio management
- Program and project management
- Business performance measurement
- License management

## Typical stakeholders

- CIO
- Program managers
- Enterprise architects
- Business analysts
- Portfolio managers

---

# 16. Platform Perspective

## Purpose

Helps understand current IT systems and design the target-state architecture.

## Capabilities

- Compute provisioning
- Network provisioning
- Storage provisioning
- Database provisioning
- Systems and solution architecture
- Application development

## Typical stakeholders

- CTO
- IT managers
- Solutions architects

---

# 17. Security Perspective

## Purpose

Helps the organization meet security objectives in the cloud.

## Capabilities

- Identity and access management
- Detective control
- Infrastructure security
- Data protection
- Incident response

## Typical stakeholders

- CISO
- IT security managers
- IT security analysts

---

# 18. Operations Perspective

## Purpose

Defines how daily, quarterly, and yearly IT operations are run and supported.

## Capabilities

- Service monitoring
- Application performance monitoring
- Resource inventory management
- Release and change management
- Reporting and analytics
- Business continuity and disaster recovery
- IT service catalog

## Typical stakeholders

- IT operations managers
- IT support managers

---

# 19. Module 1 Summary

By the end of Module 1, you should clearly understand:

- What cloud computing is
- The three cloud service models
- The three cloud deployment models
- The six advantages of cloud computing
- The purpose of AWS and its service categories
- The main ways to interact with AWS
- The role of AWS CAF in cloud adoption

---

# 20. Very Important Exam Memory Sheet

## Cloud computing

On-demand IT resources over the internet with pay-as-you-go pricing.

## Service models

- IaaS
- PaaS
- SaaS

## Deployment models

- Cloud
- Hybrid
- On-premises / private cloud

## Six advantages

1. Trade capital expense for variable expense  
2. Benefit from economies of scale  
3. Stop guessing capacity  
4. Increase speed and agility  
5. Stop spending money on running data centers  
6. Go global in minutes  

## AWS interaction methods

- Management Console
- CLI
- SDKs

## AWS CAF perspectives

- Business
- People
- Governance
- Platform
- Security
- Operations

---

# 21. Sample Exam Question

## Question

Why is AWS more economical than traditional data centers for applications with varying compute workloads?

### Options

- A. Amazon EC2 costs are billed monthly
- B. Customers retain full administrative access to their Amazon EC2 instances
- C. Amazon EC2 instances can be launched on demand when needed
- D. Customers can permanently run enough instances to handle peak workloads

## Correct answer

**C. Amazon EC2 instances can be launched on demand when needed**

## Explanation

When workloads vary, cloud computing is more economical because you do not need to keep expensive peak-capacity hardware running all the time.

You launch resources when needed and stop them when demand decreases.

---

# Final Note

For Module 1 exam preparation, focus especially on:

- Definitions of cloud computing
- IaaS vs PaaS vs SaaS
- Cloud vs Hybrid vs On-premises
- The six advantages of cloud computing
- AWS service categories
- Console vs CLI vs SDK
- The 6 AWS CAF perspectives
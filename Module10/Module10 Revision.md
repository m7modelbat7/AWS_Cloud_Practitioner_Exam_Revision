# Module 10: Auto Scaling and Monitoring

## Module Overview

### Topics
- Elastic Load Balancing
- Amazon CloudWatch
- Amazon EC2 Auto Scaling

### Activities
- Elastic Load Balancing activity
- Amazon CloudWatch activity

### Lab
- Scale and Load Balance Your Architecture

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Indicate how to distribute traffic across Amazon Elastic Compute Cloud (Amazon EC2) instances by using Elastic Load Balancing
- Identify how Amazon CloudWatch enables you to monitor AWS resources and applications in real time
- Explain how Amazon EC2 Auto Scaling launches and releases servers in response to workload changes
- Perform scaling and load balancing tasks to improve an architecture

---

# Section 1: Elastic Load Balancing

## Why Load Balancing Matters

Modern high-traffic applications can receive hundreds of thousands or even millions of concurrent requests.

If all requests go to one server:
- That server can become overloaded
- Performance can degrade
- Availability can suffer

This is why additional servers are usually needed, and why traffic must be distributed intelligently.

---

## What Is Elastic Load Balancing?

Elastic Load Balancing (ELB) is an AWS service that distributes incoming application or network traffic across multiple targets.

### Targets Can Include
- Amazon EC2 instances
- Containers
- IP addresses
- Lambda functions

### Key Capabilities
- Distributes traffic across one Availability Zone or multiple Availability Zones
- Scales the load balancer as traffic changes over time
- Automatically adapts to most workloads

### Main Idea
Elastic Load Balancing improves:
- Availability
- Scalability
- Fault tolerance
- Traffic distribution

---

## Types of Load Balancers

AWS provides **three types** of load balancers:

- Application Load Balancer
- Network Load Balancer
- Gateway Load Balancer

---

## 1. Application Load Balancer (ALB)

### Main Purpose
Best for **HTTP** and **HTTPS** traffic.

### Key Characteristics
- Operates at the **application layer** of the OSI model (**Layer 7**)
- Routes traffic based on the **content of the request**
- Supports advanced request routing
- Well suited for:
  - Modern applications
  - Microservices
  - Container-based applications
  - Lambda-backed HTTP(S) applications

### Security Benefit
Helps simplify application security by ensuring that modern SSL/TLS ciphers and protocols are used.

---

## 2. Network Load Balancer (NLB)

### Main Purpose
Best for **TCP**, **UDP**, and **TLS** traffic when very high performance is required.

### Key Characteristics
- Operates at the **transport layer** of the OSI model (**Layer 4**)
- Routes traffic based on **IP protocol data**
- Handles **millions of requests per second**
- Maintains **ultra-low latency**
- Optimized for:
  - Sudden traffic spikes
  - Volatile traffic patterns
  - Very high network performance needs

---

## 3. Gateway Load Balancer (GWLB)

### Main Purpose
Best for deploying and scaling **virtual appliances**.

### Key Characteristics
- Operates at the **network layer** of the OSI model (**Layer 3**)
- Routes traffic using **Gateway Load Balancer endpoints**
- Traffic to and from the endpoint is configured using **route tables**
- The Gateway Load Balancer endpoint and the application servers must be created in **different subnets**

### Common Use Cases
- Firewalls
- Intrusion detection systems
- Intrusion prevention systems
- Deep packet inspection systems

### Main Idea
It combines:
- A transparent network gateway
- Load balancing for virtual security appliances

---

## How Elastic Load Balancing Works

### Core Flow
1. A load balancer accepts incoming client traffic
2. One or more **listeners** check for connection requests
3. Traffic is routed to **target groups**
4. The load balancer sends traffic only to **healthy targets**

### Listener
A listener is a process that checks for connection requests.

It is configured with:
- A protocol
- A port for client-to-load-balancer traffic
- A protocol and port for load-balancer-to-target traffic

### Health Checks
Health checks monitor the health of registered targets.

If a target becomes unhealthy:
- The load balancer stops sending traffic to it

If the target becomes healthy again:
- The load balancer resumes routing traffic to it

### Main Idea
ELB helps ensure that traffic goes only to healthy backends.

---

## Elastic Load Balancing Use Cases

### 1. Highly Available and Fault-Tolerant Applications
- ELB balances traffic across healthy targets in multiple Availability Zones
- If targets fail in one Availability Zone, traffic is routed to healthy targets in other Availability Zones
- When failed targets recover, traffic resumes automatically

### 2. Containerized Applications
- Supports enhanced container integration
- Can balance traffic across multiple ports on the same EC2 instance
- Integrates with Amazon ECS
- Automatically manages registration and de-registration of containers
- Can dynamically detect ports and reconfigure itself

### 3. Elasticity and Scalability
- Works with Amazon CloudWatch and Amazon EC2 Auto Scaling
- CloudWatch alarms can trigger Auto Scaling
- New instances can be launched automatically
- ELB registers new instances and begins routing traffic to them

### 4. Use Inside a VPC
- Can create a public entry point into a VPC
- Can also route traffic internally between application tiers
- Supports security groups
- Existing network ACLs and route tables still apply
- Can be:
  - Public
  - Internal

### 5. Hybrid Environments
- Can distribute traffic across AWS and on-premises resources
- Can use one load balancer with a shared target group model
- Can also use DNS-based weighted load balancing with separate load balancers

### 6. Invoking Lambda Functions over HTTP(S)
- ALB supports Lambda functions as targets
- Users can access serverless apps from HTTP clients, including browsers
- Supports content-based routing to different Lambda functions
- Allows mixed architectures using:
  - EC2
  - Containers
  - On-premises servers
  - Lambda functions

---

## Activity: Elastic Load Balancing

### Scenario-to-Load-Balancer Mapping

#### You must support traffic to a containerized application
- **Answer:** Application Load Balancer

#### You have extremely spiky and unpredictable TCP traffic
- **Answer:** Network Load Balancer

#### You need to deploy virtual appliances for security inspection and network traffic analysis
- **Answer:** Gateway Load Balancer

#### You need to support a static or Elastic IP address, or an IP target outside a VPC
- **Answer:** Network Load Balancer

#### You need a load balancer that can handle millions of requests per second while maintaining low latencies
- **Answer:** Network Load Balancer

#### You must support HTTPS requests
- **Answer:** Application Load Balancer

---

## Load Balancer Monitoring

You can monitor load balancers by using:

### 1. Amazon CloudWatch Metrics
- ELB publishes metrics to CloudWatch
- Used to verify system performance
- Can trigger CloudWatch alarms if metrics leave an acceptable range

### 2. Access Logs
- Capture detailed request information
- Stored as log files in Amazon S3
- Useful for:
  - Analyzing traffic patterns
  - Troubleshooting backend issues

### 3. AWS CloudTrail Logs
- Capture API interaction details
- Can show:
  - Who made the call
  - What action was taken
  - When it happened
  - Source IP address
- Useful for:
  - Auditing
  - Security review
  - Operational troubleshooting

---

## Section 1 Key Takeaways

- Elastic Load Balancing distributes incoming application or network traffic across multiple targets in one or more Availability Zones
- Elastic Load Balancing supports three types of load balancers:
  - Application Load Balancer
  - Network Load Balancer
  - Gateway Load Balancer
- Elastic Load Balancing provides health checks, security support, and monitoring capabilities

---

# Section 2: Amazon CloudWatch

## Why Monitoring Matters

To use AWS efficiently, you need insight into your resources.

### Important Questions
- When should you launch more EC2 instances?
- Is application performance being affected by lack of capacity?
- How much of your infrastructure is actually being used?

### Main Idea
Without monitoring, you cannot make good scaling, performance, or availability decisions.

---

## What Is Amazon CloudWatch?

Amazon CloudWatch is a monitoring and observability service built for:

- DevOps engineers
- Developers
- Site reliability engineers (SREs)
- IT managers

### CloudWatch Monitors
- AWS resources
- Applications running on AWS

### CloudWatch Collects and Tracks
- Standard metrics
- Custom metrics

### CloudWatch Can Also
- Create alarms
- Send notifications
- Trigger EC2 Auto Scaling actions
- Trigger EC2 actions
- Match events and route them to targets for processing

### Main Idea
CloudWatch gives you system-wide visibility into:
- Resource utilization
- Application performance
- Operational health

---

## CloudWatch Metrics

A metric is a measurable variable for a resource or application.

### Example Metrics Mentioned in the Module
- EC2 CPU utilization
- ELB request latency
- DynamoDB table throughput
- Amazon SQS queue length
- AWS bill charges

### Metric Types
- Standard AWS metrics
- Custom application or infrastructure metrics

---

## CloudWatch Alarms

You can create an alarm to monitor a metric and automatically take action.

### Alarm Actions Can Include
- Sending a notification to an Amazon SNS topic
- Performing an Amazon EC2 Auto Scaling action
- Performing an Amazon EC2 action

### Alarm Types
You can create alarms based on:
- Static threshold
- Anomaly detection
- Metric math expression

---

## Static Threshold Alarm Configuration

When you create a static threshold alarm, you must specify:

### 1. Namespace
Example:
- `AWS/EC2`

### 2. Metric
Example:
- `CPUUtilization`

### 3. Statistic
Can be:
- Average
- Sum
- Minimum
- Maximum
- Sample count
- Predefined percentile
- Custom percentile

### 4. Period
- The evaluation period
- Each period becomes one data point during alarm evaluation

### 5. Conditions
Threshold comparisons can be:
- Greater than
- Greater than or equal to
- Lower than
- Lower than or equal to

### 6. Additional Configuration
Includes:
- Number of breached data points required
- How to treat missing data

### 7. Actions
- Send SNS notification
- Perform EC2 Auto Scaling action
- Perform EC2 action

### Main Idea
CloudWatch alarms let you turn monitoring into automated response.

---

## CloudWatch Events

CloudWatch can define rules that match changes in your AWS environment and route those events to targets.

### Possible Targets Mentioned
- Amazon EC2 instances
- AWS Lambda functions
- Kinesis streams
- Amazon ECS tasks
- Step Functions state machines
- Amazon SNS topics
- Amazon SQS queues
- Built-in targets

### Main Idea
CloudWatch Events helps react automatically to operational changes.

---

## CloudWatch Pricing Note

CloudWatch has:
- No upfront commitment
- No minimum fee

### Billing Model
- You pay only for what you use
- Charges are applied at the end of the month

---

## Activity: Amazon CloudWatch

### Determine Which Alarm Examples Are Correct

#### Amazon EC2
**If average CPU utilization is > 60% for 5 minutes**
- **Correct**

#### Amazon RDS
**If the number of simultaneous connections is > 10 for 1 minute**
- **Correct**

#### Amazon S3
**If the maximum bucket size in bytes is around 3 for 1 day**
- **Incorrect**
- Reason: **"around"** is not a valid threshold option
- Valid threshold operators must be:
  - `>`
  - `>=`
  - `<=`
  - `<`

#### Elastic Load Balancing
**If the number of healthy hosts is < 5 for 10 minutes**
- **Correct**

#### Amazon Elastic Block Store
**If the volume of read operations is > 1,000 for 10 seconds**
- **Incorrect**
- Reason: you must specify a **statistic**, such as average volume

---

## Section 2 Key Takeaways

- Amazon CloudWatch helps you monitor your AWS resources and applications in real time
- CloudWatch lets you:
  - Collect and track standard and custom metrics
  - Create alarms
  - Send notifications to SNS topics
  - Perform Amazon EC2 Auto Scaling or Amazon EC2 actions
  - Define rules that match AWS environment changes and route them to processing targets

---

# Section 3: Amazon EC2 Auto Scaling

## Why Scaling Is Important

Scaling is the ability to increase or decrease the compute capacity of your application.

### The Problem with Fixed Capacity
If you provision for peak demand:
- Many resources stay idle most of the time
- Cost is not optimized

If you provision too little:
- Application performance suffers
- Availability can be affected
- Users may experience outages or slowdowns

### Main Idea
Scaling helps you balance:
- Performance
- Availability
- Cost efficiency

---

## Amazon EC2 Auto Scaling

Amazon EC2 Auto Scaling is an AWS service that:

- Helps maintain application availability
- Automatically adds or removes EC2 instances based on conditions you define
- Detects impaired EC2 instances and unhealthy applications
- Replaces bad instances automatically

### Scaling Options Mentioned
- Manual
- Scheduled
- Dynamic or on-demand
- Predictive

### Main Idea
Because compute in the cloud is programmable, capacity can adjust automatically as demand changes.

---

## Why Auto Scaling Is Useful

### Predictable Workloads
Useful when traffic follows known patterns, such as weekly cycles.

### Dynamic On-Demand Workloads
Also useful for changing demand patterns, such as seasonal spikes.

### Example in the Module
Amazon.com traffic in November experiences major peaks during Black Friday and Cyber Monday.

If capacity were fixed for those peaks:
- **76 percent** of resources would be idle for most of the year
- Only **24 percent** would be actively needed most of the time

### Main Lesson
Auto scaling avoids:
- Too much idle capacity
- Under-capacity during spikes

---

## Auto Scaling Groups

An **Auto Scaling group** is a collection of EC2 instances treated as a logical group for automatic scaling and management.

### Important Settings
- **Minimum size**
- **Desired capacity**
- **Maximum size**

### What They Mean
- Minimum size: the group should not go below this number
- Desired capacity: the number of instances the group tries to maintain
- Maximum size: the group should not exceed this number

### Example from the Module
- Minimum size = 1
- Desired capacity = 2
- Maximum size = 4

### Main Idea
Scaling policies adjust the number of instances within the minimum and maximum limits.

---

## Scaling Out vs Scaling In

### Scaling Out
- Launching additional instances

### Scaling In
- Terminating instances

### Main Idea
Auto Scaling can both add and remove servers as needed.

---

## How Amazon EC2 Auto Scaling Works

The module organizes Auto Scaling around three questions:

### 1. What Are You Scaling?
You define a **launch configuration**, which is the instance configuration template.

It can include:
- AMI
- Instance type
- IAM role
- Security groups
- EBS volumes
- Additional storage

### 2. Where Are You Scaling?
You launch the Auto Scaling group into:
- A VPC
- One or more subnets

You can also attach:
- One or more load balancers

When a load balancer is attached:
- New instances are registered automatically
- Incoming traffic is distributed across the instances

### 3. When Are You Scaling?
Scaling can happen through:
- Health checks
- Manual changes
- Scheduled actions
- Scaling policies
- AWS Auto Scaling predictive scaling

---

## Auto Scaling Modes

### 1. Maintain Current Instance Levels
- Keeps a specified number of instances running at all times
- Performs health checks
- Replaces unhealthy instances automatically

### 2. Manual Scaling
- You manually change:
  - Minimum size
  - Maximum size
  - Desired capacity

### 3. Scheduled Scaling
- Scaling happens automatically at specific dates and times
- Good for predictable workloads
- Example: weekly traffic increases on Wednesday and Thursday, then decreases on Friday

### 4. Dynamic Scaling
- Responds to changing conditions you do not know in advance
- Example:
  - Keep average CPU utilization close to 50 percent
- Avoids keeping too many idle resources
- Uses policies triggered by CloudWatch alarms

### 5. Predictive Scaling
- Uses Amazon EC2 Auto Scaling with AWS Auto Scaling
- Capacity scales based on predicted demand
- Uses machine learning
- Needs at least **1 day** of historical data to start making predictions
- Re-evaluates every **24 hours**
- Creates a forecast for the next **48 hours**

### Main Idea
Different workloads need different scaling strategies.

---

## Implementing Dynamic Scaling

A common dynamic scaling setup combines:

- Amazon CloudWatch
- Amazon EC2 Auto Scaling
- Elastic Load Balancing

### Example Flow from the Module
1. CloudWatch monitors average CPU utilization across the fleet
2. If average CPU utilization is **> 60% for 5 minutes**, the alarm is triggered
3. EC2 Auto Scaling launches a new instance using the launch configuration
4. EC2 Auto Scaling registers the new instance with Elastic Load Balancing
5. ELB performs health checks
6. ELB begins distributing traffic to the new instance

### Main Idea
These three services are useful individually, but together they create a much more powerful and flexible architecture.

---

## AWS Auto Scaling

AWS Auto Scaling is a **separate service** from Amazon EC2 Auto Scaling.

### What It Does
- Monitors your applications
- Automatically adjusts capacity
- Tries to maintain steady, predictable performance
- Works toward the lowest possible cost

### Resources It Can Scale
- Amazon EC2 instances and Spot Fleets
- Amazon ECS tasks
- Amazon DynamoDB tables and indexes
- Amazon Aurora Replicas

### Main Idea
If you already use EC2 Auto Scaling for EC2 instances, AWS Auto Scaling can extend scaling to other AWS services too.

---

## Section 3 Key Takeaways

- Scaling helps you respond quickly to changes in resource needs
- Amazon EC2 Auto Scaling maintains application availability by automatically adding or removing EC2 instances
- An Auto Scaling group is a collection of EC2 instances
- A launch configuration is an instance configuration template
- Dynamic scaling commonly uses:
  - Amazon EC2 Auto Scaling
  - Amazon CloudWatch
  - Elastic Load Balancing
- AWS Auto Scaling is a separate service from Amazon EC2 Auto Scaling

---

# Lab 6: Scale and Load Balance Your Architecture

## Lab Scenario

You start with an architecture that includes:

- VPC: `10.0.0.0/16`
- Two Availability Zones
- Public subnet 1: `10.0.0.0/24`
- Public subnet 2: `10.0.2.0/24`
- Private subnet 1: `10.0.1.0/24`
- Private subnet 2: `10.0.3.0/24`
- Internet gateway
- NAT gateway
- Web server
- RDS DB primary
- RDS DB secondary
- Security groups

### Main Goal
Use Elastic Load Balancing and Amazon EC2 Auto Scaling to create a more scalable and balanced architecture.

---

## Lab Tasks

In this lab, you complete the following tasks:

- Create an Amazon Machine Image (AMI) from a running instance
- Create an Application Load Balancer
- Create a launch configuration and an Auto Scaling group
- Automatically scale new instances within a private subnet
- Create Amazon CloudWatch alarms and monitor performance of your infrastructure

---

## Lab Final Product

After the lab, the architecture includes:

- VPC: `10.0.0.0/16`
- Two Availability Zones
- Public subnets
- Private subnets
- Internet gateway
- NAT gateway
- Application Load Balancer
- Auto Scaling group
- Web instances
- RDS DB primary
- RDS DB secondary
- Security groups

### Main Improvement
The architecture becomes:
- Load balanced
- Automatically scalable
- Monitored with CloudWatch
- More resilient than the starting design

---

## Lab Debrief: Key Takeaways

In the lab, you:

- Created an Amazon Machine Image (AMI) from a running instance
- Created a load balancer
- Created a launch configuration and an Auto Scaling group
- Automatically scaled new instances within a private subnet
- Created Amazon CloudWatch alarms and monitored performance of your infrastructure

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Indicate how to distribute traffic across Amazon EC2 instances using Elastic Load Balancing
- Identify how Amazon CloudWatch enables you to monitor AWS resources and applications in real time
- Explain how Amazon EC2 Auto Scaling launches and releases servers in response to workload changes
- Perform scaling and load balancing tasks to improve an architecture

---

## Knowledge Check
- Complete the knowledge check for this module.

---

## Sample Exam Question

### Question
Which service would you use to send alerts based on Amazon CloudWatch alarms?

### Choices
- A. Amazon Simple Notification Service
- B. AWS CloudTrail
- C. AWS Trusted Advisor
- D. Amazon Route 53

### Correct Answer
**A. Amazon Simple Notification Service**

### Why
The keywords are:
- **send alerts**
- **Amazon CloudWatch alarms**

CloudWatch alarms can send notifications to an **Amazon SNS topic**, so the correct answer is **Amazon Simple Notification Service**.

---

# Exam-Focused Final Review

## Memorize These Points

### Elastic Load Balancing
- ELB distributes incoming traffic across multiple targets
- It can work across one or more Availability Zones
- It supports:
  - Application Load Balancer
  - Network Load Balancer
  - Gateway Load Balancer

### Load Balancer Types
- **ALB** = Layer 7, HTTP/HTTPS, content-based routing, microservices, containers, Lambda over HTTP(S)
- **NLB** = Layer 4, TCP/UDP/TLS, ultra-low latency, millions of requests per second, spiky traffic
- **GWLB** = Layer 3, security appliances, firewalls, inspection systems

### ELB Concepts
- Listener checks for connections
- Target groups hold registered targets
- Health checks ensure traffic goes only to healthy targets

### ELB Monitoring
- CloudWatch metrics
- Access logs
- CloudTrail logs

### Amazon CloudWatch
- Monitors AWS resources and applications in real time
- Tracks standard and custom metrics
- Supports alarms
- Supports event-based automation
- Can send notifications to SNS
- Can trigger EC2 Auto Scaling or EC2 actions

### CloudWatch Alarm Inputs
- Namespace
- Metric
- Statistic
- Period
- Conditions
- Additional configuration
- Actions

### Amazon EC2 Auto Scaling
- Automatically adds or removes EC2 instances
- Replaces unhealthy instances
- Helps maintain application availability
- Supports:
  - Manual scaling
  - Scheduled scaling
  - Dynamic scaling
  - Predictive scaling

### Auto Scaling Group
- A logical group of EC2 instances
- Defined by:
  - Minimum size
  - Desired capacity
  - Maximum size

### Key Auto Scaling Terms
- **Scale out** = launch instances
- **Scale in** = terminate instances
- **Launch configuration** = template for the instances being scaled

### Dynamic Scaling Flow
- CloudWatch alarm detects threshold breach
- EC2 Auto Scaling launches or removes instances
- ELB registers healthy instances and routes traffic

### AWS Auto Scaling
- Separate from EC2 Auto Scaling
- Can scale:
  - EC2 instances and Spot Fleets
  - ECS tasks
  - DynamoDB tables and indexes
  - Aurora Replicas

---

# One-Line Summary

Module 10 explains how Elastic Load Balancing distributes traffic, how Amazon CloudWatch monitors resources and triggers automated responses, and how Amazon EC2 Auto Scaling and AWS Auto Scaling help architectures stay available, efficient, and responsive to changing demand.
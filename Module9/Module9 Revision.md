# Module 9: Cloud Architecture

## Module Overview

### Topics
- AWS Well-Architected Framework
- Reliability and high availability
- AWS Trusted Advisor

### Activities
- AWS Well-Architected Framework design principles activity
- Interpret AWS Trusted Advisor recommendations

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Describe the AWS Well-Architected Framework, including the six pillars
- Identify the design principles of the AWS Well-Architected Framework
- Explain the importance of reliability and high availability
- Identify how AWS Trusted Advisor helps customers
- Interpret AWS Trusted Advisor recommendations

---

# Section 1: AWS Well-Architected Framework

## Architecture: Designing and Building

Architecture is the art and science of designing and building large structures.

### In a Cloud Context, Architects:
- Engage with decision makers to identify business goals and needed capabilities
- Ensure alignment between technical deliverables and business goals
- Work with delivery teams to ensure the chosen technical features are appropriate

### Main Idea
Having well-architected systems greatly increases the likelihood of business success.

---

## What Is the AWS Well-Architected Framework?

The AWS Well-Architected Framework is:

- A guide for designing infrastructures that are:
  - Secure
  - High-performing
  - Resilient
  - Efficient
- A consistent approach to evaluating and implementing cloud architectures
- A way to provide best practices developed from lessons learned by reviewing customer architectures

### Main Purpose
It helps you build the most secure, high-performing, resilient, and efficient infrastructure possible for your cloud applications and workloads.

### Important Detail
AWS developed the framework after reviewing thousands of customer architectures on AWS.

---

## Pillars of the AWS Well-Architected Framework

The AWS Well-Architected Framework is organized into **six pillars**:

- Operational Excellence
- Security
- Reliability
- Performance Efficiency
- Cost Optimization
- Sustainability

### Important Note
The first five pillars have been part of the framework since 2015.  
The **Sustainability** pillar was added in 2021 to help organizations minimize the environmental impact of cloud workloads.

### Important Course Note
The remainder of this module focuses mainly on the first five pillars:

- Operational Excellence
- Security
- Reliability
- Performance Efficiency
- Cost Optimization

---

## Pillar Organization

Each pillar includes:

- Best practice areas
- Questions to ask during architecture review
- Context for the question
- Recommended best practices

### Example Shown in the Module
A security best practice area asks how you manage credentials and authentication, and includes best practices such as:

- Define identity and access requirements
- Secure the AWS account root user
- Enforce MFA
- Automate access control enforcement
- Integrate with centralized federation
- Enforce password requirements
- Rotate credentials regularly
- Audit credentials periodically

### Main Idea
The framework is not just theory. It is organized into reviewable questions and practical best practices.

---

## Activity Context: Reviewing AnyCompany

The module uses a fictional company called **AnyCompany Corporation** to practice architecture review.

### AnyCompany Background
- Slogan: **Cityscapes you can stand over**
- Founded in 2008 by John Doe
- Sells 3D-printed cityscapes
- Preparing for investment and due diligence review
- Cloud native

### Important Background Detail
John created the AWS account in 2008 and originally launched his first Amazon EC2 instance himself. Over time, the company grew, but he shared the AWS account root user credentials with the rest of his team to manage the environment.

### Why This Matters
This detail becomes important when reviewing the architecture under the security pillar.

---

## AnyCompany Organizational Structure

AnyCompany has three main departments:

- **Fly and Snap** - image acquisition, preprocessing, and storage
- **Show and Sell** - promoting, selling, and working with customers
- **Make and Ship** - manufacturing of products and delivery

The high-level platform design mirrors the company’s organizational structure.

---

## AnyCompany Architecture: Fly and Snap

The **Fly and Snap** department handles image acquisition and preprocessing.

### Workflow
- Multiple devices, such as cameras and video cameras, are mounted on lightweight aircraft
- They capture imagery of major cities on a scheduled basis
- Each imagery asset is timestamped
- Assets are streamed to an onboard **Capture machine** with an external storage array
- The Capture machine also collects navigation data such as:
  - GPS
  - Compass readings
  - Elevation

### After Returning to Base
- The storage array is disconnected and moved to an ingest bay
- It is connected to an **Ingest machine**
- The Ingest machine creates a compressed archive
- It uses **FTP** to send the archive to an EC2 **Preprocessor machine**
- After processing, the archive is written to tape for backup
- Tapes are stored offsite by a third-party backup provider

### Preprocessor Machine
- Periodically processes new datasets
- Extracts imagery assets
- Stores them in an Amazon S3 bucket
- Notifies the Imagery service and provides flight information

### Imagery Service
- Computes 3D orientation and location for every moment of the flight
- Correlates this data to imagery file timestamps
- Stores the information in an **RDBMS hosted on Amazon EC2**
- Stores links to imagery assets in Amazon S3

---

## AnyCompany Architecture: Show and Sell

The **Show and Sell** department handles the website and customer ordering flow.

### Website Architecture
- Uses **Elastic Load Balancing** with HTTPS
- Uses an **Auto Scaling group of EC2 instances**
- Runs a content management system
- Stores static website assets in an S3 bucket

### Customer Experience
Customers can:
- View product images and videos
- Select a location on a map
- See a video preview of their cityscape
- Choose physical size
- Choose color scheme:
  - White
  - Monochrome
  - Full color
- Choose optional LED holes for illuminated maps

### Mapping and Ordering
- The Mapping service checks imagery availability for the selected location
- If customers proceed, they place an order
- Credit card orders are processed by a third-party PCI-compliant provider
- AnyCompany does **not** process or store credit card information

### Order Processing
- After payment confirmation, the website tells the Order service to push the order to production
- Orders and customer details are stored in the **Show and Sell database**
- This database is an **RDBMS hosted on Amazon EC2**

### Queues and Status Flow
- The Order service places messages on the **Production queue**
- The Render service uses this queue to know when to generate previews
- The Order service also reads from the **Order status queue**
- Customers can track order status during manufacturing and dispatch
- Dispatch is handled by a third-party broker service

---

## AnyCompany Architecture: Make and Ship

The **Make and Ship** department handles rendering, printing, and shipment.

### Render Service
- Uses a fleet of **g2.2xlarge** instances
- Takes orders from the **Production queue**
- Generates 3D models
- Stores 3D models in an S3 bucket
- Generates flyby videos for customer previews
- Stores preview videos in a separate S3 bucket

### Data Retention
- Old preview videos are deleted once a year
- 3D models are kept in case they are needed for future projects

### Printing Workflow
- After order placement, a message is placed in the **Print queue**
- The message contains a link to the 3D model
- Order status updates are posted to the **Order status queue**
- The website consumes this queue and shows order history

### On-Premises Printing
- The company has four 3D printers
- An on-premises **Print conductor** machine reads from the Print queue
- It sends jobs to the next available printer
- It sends updates to the Order status queue
- It sends a final update when the order is complete, passes quality assurance, and is ready for dispatch

---

## Activity: AWS Well-Architected Framework Design Principles

The activity asks learners to review the AnyCompany architecture pillar by pillar.

### For Each Question, You Must Answer
- What is the **current state** of the architecture?
- What should the **future state** be?
- What is the **top improvement** AnyCompany should make?

### Important Note
The module explicitly says there are **no right or wrong answers**.  
The framework questions are intended to prompt discussion.

---

# Operational Excellence Pillar

## Focus
Run and monitor systems to deliver business value and continually improve supporting processes and procedures.

## Key Topics
- Automating changes
- Responding to events
- Defining standards to manage daily operations

## Design Principles
- Perform operations as code
- Make frequent, small, reversible changes
- Refine operations procedures frequently
- Anticipate failure
- Learn from all operational events and failures

## Best Practice Areas and Questions

### Organization
- How do you determine what your priorities are?
- How do you structure your organization to support your business outcomes?
- How does your organizational culture support your business outcomes?

### Prepare
- How do you design your workload so that you can understand its state?
- How do you reduce defects, ease remediation, and improve flow into production?
- How do you mitigate deployment risks?
- How do you know that you are ready to support a workload?

### Operate
- How do you understand the health of your workload?
- How do you understand the health of your operations?
- How do you manage workload and operations events?

### Evolve
- How do you evolve operations?

## Activity Breakout Questions
The module specifically asks learners to review:

- **OPS 4**: How do you design your workload so that you can understand its state?
- **OPS 6**: How do you mitigate deployment risk?
- **OPS 7**: How do you know that you are ready to support a workload?

---

# Security Pillar

## Focus
Protect information, systems, and assets while delivering business value through risk assessments and mitigation strategies.

## Key Topics
- Protecting confidentiality and integrity of data
- Identifying and managing who can do what
- Protecting systems
- Establishing controls to detect security events

## Design Principles
- Implement a strong identity foundation
- Enable traceability
- Apply security at all layers
- Automate security best practices
- Protect data in transit and at rest
- Keep people away from data
- Prepare for security events

## Best Practice Areas and Questions

### Security
- How do you securely operate your workload?

### Identity and Access Management
- How do you manage identities for people and machines?
- How do you manage permissions for people and machines?

### Detection
- How do you detect and investigate security events?

### Infrastructure Protection
- How do you protect your network resources?
- How do you protect your compute resources?

### Data Protection
- How do you classify your data?
- How do you protect your data at rest?
- How do you protect your data in transit?

### Incident Response
- How do you anticipate, respond to, and recover from incidents?

## Activity Breakout Questions
The module specifically asks learners to review:

- **SEC 1**: How do you securely operate your workload?
- **SEC 4**: How do you detect and investigate security events?
- **SEC 6**: How do you protect your compute resources?

---

# Reliability Pillar

## Focus
Ensure a workload performs its intended function correctly and consistently when it is expected to.

## Key Topics
- Designing distributed systems
- Recovery planning
- Handling change

## Design Principles
- Automatically recover from failure
- Test recovery procedures
- Scale horizontally to increase aggregate workload availability
- Stop guessing capacity
- Manage change in automation

## Best Practice Areas and Questions

### Foundations
- How do you manage service quotas and constraints?
- How do you plan your network topology?

### Workload Architecture
- How do you design your workload service architecture?
- How do you design interactions in a distributed system to prevent failure?
- How do you design interactions in a distributed system to mitigate or withstand failures?

### Change Management
- How do you monitor workload resources?
- How do you design your workload to adapt to changes in demand?
- How do you implement change?

### Failure Management
- How do you back up data?
- How do you use fault isolation to protect your workload?
- How do you design your workload to withstand component failures?
- How do you test reliability?
- How do you plan for disaster recovery?

## Activity Breakout Questions
The module specifically asks learners to review:

- **REL 2**: How do you plan your network topology?
- **REL 7**: How do you design your system to adapt to changes in demand?
- **REL 9**: How do you back up data?

---

# Performance Efficiency Pillar

## Focus
Use IT and computing resources efficiently to meet system requirements and maintain that efficiency as demand changes and technologies evolve.

## Key Topics
- Selecting the right resource types and sizes based on workload requirements
- Monitoring performance
- Making informed decisions as business needs evolve

## Design Principles
- Democratize advanced technologies
- Go global in minutes
- Use serverless architectures
- Experiment more often
- Consider mechanical sympathy

## Best Practice Areas and Questions

### Selection
- How do you select the best performing architecture?
- How do you select your compute solution?
- How do you select your storage solution?
- How do you select your database solution?
- How do you configure your networking solution?

### Review
- How do you evolve your workload to take advantage of new releases?

### Monitoring
- How do you monitor your resources to ensure they are performing?

### Tradeoffs
- How do you use tradeoffs to improve performance?

## Activity Breakout Questions
The module specifically asks learners to review:

- **PERF 1**: How do you select the best performing architecture?
- **PERF 2**: How do you select your compute solution?
- **PERF 4**: How do you select your database solution?

---

# Cost Optimization Pillar

## Focus
Avoid unnecessary costs.

## Key Topics
- Understanding and controlling where money is being spent
- Selecting the most appropriate and right number of resource types
- Analyzing spend over time
- Scaling to meet business needs without overspending

## Design Principles
- Implement Cloud Financial Management
- Adopt a consumption model
- Measure overall efficiency
- Stop spending money on undifferentiated heavy lifting
- Analyze and attribute expenditure

## Best Practice Areas and Questions

### Practice Cloud Financial Management
- How do you implement cloud financial management?

### Expenditure and Usage Awareness
- How do you govern usage?
- How do you monitor usage and cost?
- How do you decommission resources?

### Cost-Effective Resources
- How do you evaluate cost when you select services?
- How do you meet cost targets when you select resource type, size, and number?
- How do you use pricing models to reduce cost?
- How do you plan for data transfer charges?

### Manage Demand and Supply Resources
- How do you manage demand and supply resources?

### Optimize Over Time
- How do you evaluate new services?

## Activity Breakout Questions
The module specifically asks learners to review:

- **COST 2**: How do you govern usage?
- **COST 6**: How do you meet cost targets when you select resource type, size, and number?
- **COST 7**: How do you use pricing models to reduce cost?

---

## The AWS Well-Architected Tool

The module explains that the AWS Well-Architected Tool is similar to the review process used in the activity.

### What the Tool Does
- Helps you review the state of your workloads
- Compares workloads to the latest AWS architectural best practices
- Gives you access to AWS architectural knowledge and best practices
- Delivers an action plan with step-by-step guidance
- Provides a consistent process to review and measure cloud architectures

### How It Works
You define a workload and answer questions across areas such as:

- Operational excellence
- Security
- Reliability
- Performance efficiency
- Cost optimization

Then the tool provides:
- Findings
- Recommendations
- Improvement guidance

### Why It Matters
You can use it to:
- Identify next steps for improvement
- Drive architectural decisions
- Bring architecture considerations into governance processes

---

## Section 1 Key Takeaways

- The AWS Well-Architected Framework provides a consistent approach to evaluate cloud architectures
- It helps implement designs using cloud best practices
- It is organized into six pillars
- Each pillar includes its own design principles and best practices

---

# Section 2: Reliability and Availability

## Core Principle

A key mindset in cloud architecture is:

> "Everything fails, all the time."  
> - Werner Vogels, CTO, Amazon.com

### Main Idea
Because failure is inevitable, you should architect workloads to withstand failure.

Two major concepts matter here:

- Reliability
- Availability

---

## Reliability

Reliability is a measure of a system’s ability to provide functionality when desired by the user.

### Important Notes
- The system includes all components:
  - Hardware
  - Firmware
  - Software
- Reliability is the probability that the entire system functions as intended for a specified period

### Example Used in the Module
A car is a system.  
Components such as ignition, brakes, and cooling must all work together.  
If a component repeatedly fails, the system is not reliable.

### Reliability Metric
**Mean Time Between Failures (MTBF)**

#### Formula
`MTBF = total time in service / number of failures`

---

## Understanding Reliability Metrics

The module explains three related metrics:

### Mean Time to Failure (MTTF)
The average amount of time the system operates before failing.

### Mean Time to Repair (MTTR)
The average amount of time needed to diagnose and fix the system after failure.

### Mean Time Between Failures (MTBF)
The average total cycle time between failures.

#### Formula
`MTBF = MTTF + MTTR`

### Example from the Module
- System runs from Monday noon to Friday noon = **96 hours**
- Repair time from Friday noon to Monday noon = **72 hours**
- Therefore:
  - `MTTF = 96 hours`
  - `MTTR = 72 hours`
  - `MTBF = 168 hours`

---

## Availability

Availability is the percentage of time a system is operating normally or correctly performing the expected operations.

### Formula
`Availability = normal operation time / total time`

### Another Way to Express It
Availability is commonly described as a percentage of uptime over a period such as one year.

### Number of 9s
A common shorthand for availability is the number of nines.

Example:
- **Five 9s** = **99.999% availability**

---

## High Availability

A highly available system can withstand some measure of degradation while still remaining available.

### Characteristics
- Downtime is minimized
- Minimal human intervention is required
- Essential services are restored quickly
- Recovery is often measured in less than one minute

### Main Idea
High availability is about keeping services online even when components fail.

---

## Availability Tiers

The module includes a table that shows common availability targets and the maximum yearly disruption they allow.

| Availability | Max Disruption per Year | Application Category |
|---|---:|---|
| 99% | 3 days 15 hours | Batch processing, data extraction, transfer, and load jobs |
| 99.9% | 8 hours 45 minutes | Internal tools like knowledge management, project tracking |
| 99.95% | 4 hours 22 minutes | Online commerce, point of sale |
| 99.99% | 52 minutes | Video delivery, broadcast systems |
| 99.999% | 5 minutes | ATM transactions, telecommunications systems |

### Main Idea
Different workloads need different availability targets. Higher availability usually costs more.

---

## Factors That Influence Availability

The module identifies three factors that influence overall application availability.

### 1. Fault Tolerance
- Built-in redundancy of application components
- Ability to remain operational even if some components fail

### 2. Scalability
- Ability to accommodate increased capacity needs
- Helps maintain performance and availability under growing demand

### 3. Recoverability
- Ability to restore service after a catastrophic event
- Includes processes, policies, and procedures for restoration

### Important Tradeoff
Improving availability usually increases cost.

---

## Section 2 Key Takeaways

- Reliability measures a system’s ability to provide functionality when desired
- Reliability can be measured using MTBF
- Availability is the percentage of time a system operates normally
- Availability is influenced by:
  - Fault tolerance
  - Scalability
  - Recoverability
- Highly available systems reduce downtime, but there is a cost tradeoff

---

# Section 3: AWS Trusted Advisor

## What Is AWS Trusted Advisor?

AWS Trusted Advisor is an online tool that provides real-time guidance to help you provision resources according to AWS best practices.

### What It Does
- Reviews your entire AWS environment
- Gives real-time recommendations
- Helps improve your environment as soon as you begin implementing architectures

---

## Trusted Advisor Recommendation Categories

AWS Trusted Advisor gives recommendations in **five categories**:

- Cost Optimization
- Performance
- Security
- Fault Tolerance
- Service Limits

### Cost Optimization
Helps reduce cost by:
- Identifying unused resources
- Identifying idle resources
- Suggesting reserved capacity opportunities

### Performance
Helps improve performance by:
- Checking service limits
- Identifying overutilized instances
- Ensuring provisioned throughput is used appropriately

### Security
Helps improve security by:
- Closing security gaps
- Enabling security features
- Reviewing permissions

### Fault Tolerance
Helps increase redundancy and availability by encouraging:
- Auto Scaling
- Health checks
- Multi-AZ deployments
- Backups

### Service Limits
Warns when service usage exceeds about **80%** of the current service limit.

### Important Note
Service limit data is based on a snapshot and can take up to 24 hours to reflect changes.

---

## Activity: Interpreting AWS Trusted Advisor Recommendations

The module includes an activity where you help interpret a friend's Trusted Advisor dashboard.

### Scenario
The dashboard looks acceptable in:
- Cost Optimization
- Service Limits

But it shows issues in:
- Security
- Performance
- Fault Tolerance

You are asked to interpret specific recommendations.

---

## Recommendation #1: MFA on Root Account

### Description
Checks the root account and warns if MFA is not enabled.

### Alert Criteria
- MFA is not enabled on the root account

### Best Practice
Protect the root account by using MFA.

### Recommended Action
- Log in to the root account
- Activate an MFA device

### Questions Asked in the Activity
- What is the status?
- What is the problem?
- What specific environment details are given?
- What is the best practice?
- What is the recommended action?

---

## Recommendation #2: IAM Password Policy

### Description
Checks whether a password policy exists and whether password content requirements are enabled.

### Alert Criteria
- A password policy exists, but at least one content requirement is not enabled

### Best Practice
Enforce strong password requirements.

### Recommended Action
- Enable missing content requirements
- If no password policy exists, create and configure one

### Important Note
Changes apply immediately to new users but do not force existing users to change their passwords.

### Questions Asked in the Activity
- What is the status?
- What is the problem?
- What specific environment details are given?
- What is the best practice?
- What is the recommended action?

---

## Recommendation #3: Security Groups - Unrestricted Access

### Description
Checks security groups for rules that allow unrestricted access to a resource.

### Alert Criteria
- A security group rule has a source IP address with a `/0` suffix for ports other than 25, 80, or 443

### Why This Is a Problem
Unrestricted access increases opportunities for:
- Hacking
- Denial-of-service attacks
- Data loss

### Best Practice
Restrict access to only those IP addresses that require it.

### Recommended Action
- Restrict the rule to required IP addresses only
- For one exact IP, use `/32`
- Delete overly permissive rules after adding tighter ones

### Example
- `192.0.2.10/32`

### Questions Asked in the Activity
- What is the status?
- What is the problem?
- What specific environment details are given?
- What is the best practice?
- What is the recommended action?

---

## Recommendation #4: Amazon EBS Snapshots

### Description
Checks the age of snapshots for Amazon EBS volumes.

### Why This Matters
Even though EBS volumes are replicated, failures can still occur. Snapshots are persisted to Amazon S3 for durable storage and point-in-time recovery.

### Alert Criteria
- **Yellow**: Most recent snapshot is between 7 and 30 days old
- **Red**: Most recent snapshot is more than 30 days old
- **Red**: The volume has no snapshot

### Best Practice
Create regular snapshots.

### Recommended Action
- Create weekly or monthly snapshots of volumes

### Questions Asked in the Activity
- What is the status?
- What is the problem?
- What specific environment details are given?
- What is the best practice?
- What is the recommended action?

---

## Recommendation #5: Amazon S3 Bucket Logging

### Description
Checks the logging configuration of Amazon S3 buckets.

### Why Logging Matters
When server access logging is enabled:
- Detailed access logs are delivered hourly
- You can perform security audits
- You can learn more about users and usage patterns

### Alert Criteria
- **Yellow**: Bucket does not have server access logging enabled
- **Yellow**: Target bucket permissions do not include the owner account, so Trusted Advisor cannot verify logging status

### Best Practice
Enable logging for most buckets.

### Recommended Action
- Enable bucket logging
- If needed, add the owner account as a grantee on the target bucket so Trusted Advisor can evaluate logging correctly

### Questions Asked in the Activity
- What is the status?
- What is the problem?
- What specific environment details are given?
- What is the best practice?
- What is the recommended action?

---

## Section 3 Key Takeaways

- AWS Trusted Advisor is an online tool that provides real-time guidance
- It evaluates your AWS environment using best-practice checks
- It gives recommendations in five categories:
  - Cost Optimization
  - Performance
  - Security
  - Fault Tolerance
  - Service Limits
- You can use it early to improve your environment as you implement architecture

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Describe the AWS Well-Architected Framework, including the six pillars
- Identify the design principles of the AWS Well-Architected Framework
- Explain the importance of reliability and high availability
- Identify how AWS Trusted Advisor helps customers
- Interpret AWS Trusted Advisor recommendations

---

## Knowledge Check
- Complete the knowledge check at the end of the module

---

## Sample Exam Question

### Question
A SysOps engineer working at a company wants to protect their data in transit and at rest. What services could they use to protect their data?

### Choices
- A. Elastic Load Balancing
- B. Amazon Elastic Block Storage (Amazon EBS)
- C. Amazon Simple Storage Service (Amazon S3)
- D. All of the above

### Correct Answer
**D. All of the above**

### Why
The keyword is:

- **protect their data in transit and at rest**

The module states that the correct answer is **All of the above**.

---

## Additional Resources

- AWS Well-Architected website:  
  https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc

- AWS Well-Architected Labs:  
  https://wellarchitectedlabs.com/

- AWS Trusted Advisor Best Practice Checks:  
  https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor-check-reference.html

---

# Exam-Focused Final Review

## Memorize These Points

### AWS Well-Architected Framework
- A consistent way to review cloud architectures
- Built from AWS best practices and lessons learned
- Organized into six pillars:
  - Operational Excellence
  - Security
  - Reliability
  - Performance Efficiency
  - Cost Optimization
  - Sustainability

### Operational Excellence
- Perform operations as code
- Make frequent, small, reversible changes
- Anticipate failure
- Learn from operational failures

### Security
- Implement strong identity controls
- Enable traceability
- Apply security at all layers
- Protect data in transit and at rest
- Prepare for security events

### Reliability
- Automatically recover from failure
- Test recovery procedures
- Scale horizontally
- Stop guessing capacity
- Manage change in automation

### Performance Efficiency
- Choose the right resource types
- Use serverless when appropriate
- Experiment often
- Review new services over time

### Cost Optimization
- Use a consumption model
- Measure efficiency
- Analyze and attribute expenditure
- Avoid paying for undifferentiated heavy lifting

### Reliability Metrics
- `MTTF` = Mean Time to Failure
- `MTTR` = Mean Time to Repair
- `MTBF = MTTF + MTTR`

### Availability
- Availability = normal operation time / total time
- Five 9s = 99.999% availability
- Higher availability usually means higher cost

### Factors That Influence Availability
- Fault tolerance
- Scalability
- Recoverability

### AWS Trusted Advisor
- Real-time recommendations
- Reviews the whole AWS environment
- Five categories:
  - Cost Optimization
  - Performance
  - Security
  - Fault Tolerance
  - Service Limits

### Common Trusted Advisor Best Practices
- Enable MFA on the root account
- Enforce a strong IAM password policy
- Avoid unrestricted security group access
- Create regular EBS snapshots
- Enable S3 bucket logging

---

# One-Line Summary

Module 9 explains how to evaluate cloud workloads with the AWS Well-Architected Framework, understand reliability and availability concepts, and use AWS Trusted Advisor to detect issues and improve security, performance, fault tolerance, cost posture, and operational health.
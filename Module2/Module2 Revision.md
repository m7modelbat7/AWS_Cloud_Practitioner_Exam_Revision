# Module 2: Cloud Economics and Billing

## Module Overview

### Topics
- Fundamentals of pricing
- Total Cost of Ownership (TCO)
- AWS Organizations
- AWS Billing and Cost Management
- Technical Support

### Demo
- Overview of the Billing Dashboard

### Activities
- AWS Pricing Calculator
- Support plans scavenger hunt

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Explain the AWS pricing philosophy
- Recognize fundamental pricing characteristics
- Indicate the elements of total cost of ownership
- Discuss the results of the AWS Pricing Calculator
- Identify how to set up an organizational structure that simplifies billing and account visibility to review cost data
- Identify the functionality in the AWS Billing Dashboard
- Describe how to use AWS Bills, AWS Cost Explorer, AWS Budgets, and AWS Cost and Usage Reports
- Identify the various AWS technical support plans and features

---

# Section 1: Fundamentals of Pricing

## AWS Pricing Model

There are **three fundamental drivers of cost** with AWS:

### 1. Compute
- Charged per hour or per second, depending on the service and pricing model
- Cost varies by instance type

### 2. Storage
- Typically charged per GB

### 3. Data Transfer
- Outbound data transfer is aggregated and charged
- Inbound data transfer usually has no charge, with some exceptions
- Typically charged per GB

### Important Notes
- In most cases, there is no charge for inbound data transfer
- In most cases, there is also no charge for data transfer between AWS services within the same AWS Region
- Outbound data transfer is aggregated across services and appears on the monthly statement as **AWS Data Transfer Out**

---

## How You Pay for AWS

AWS pricing follows a utility-style philosophy:

- Pay for what you use
- Pay less when you reserve
- Pay less when you use more
- Pay even less as AWS grows

### Core Idea
At the end of each month, you pay only for what you use. You can start or stop using a product at any time. No long-term contracts are required.

---

## Pay for What You Use

### Main Idea
- Pay only for the services you consume
- No large upfront expenses
- No need to purchase servers, software licenses, or lease facilities in advance
- Quickly adapt to changing business needs
- AWS services are on demand
- No long-term contracts
- No complex licensing dependencies

### Why It Matters
This reduces variable costs and allows businesses to focus on innovation instead of infrastructure ownership.

---

## Pay Less When You Reserve

For some AWS services, such as:

- Amazon EC2
- Amazon RDS

you can invest in **Reserved Instances (RIs)**.

### Benefits
- Save up to **75%** over equivalent On-Demand capacity

### RI Payment Options
- **AURI**: All Upfront Reserved Instance
  - Largest discount
- **PURI**: Partial Upfront Reserved Instance
  - Lower discount than AURI
- **NURI**: No Upfront Payments Reserved Instance
  - Smallest discount

### Key Rule
The larger the upfront payment, the larger the discount.

---

## Pay Less by Using More

AWS offers **volume-based discounts**.

### Examples
- Amazon S3
- Amazon EBS
- Amazon EFS

### Main Idea
- Pricing can be tiered
- The more you use, the less you pay per GB
- Multiple storage services help lower storage costs based on your needs

### Also Remember
- Data transfer **in** is always free in this context as presented by the module
- As usage increases, economies of scale help keep costs under control

---

## Pay Even Less as AWS Grows

AWS continuously lowers its cost of doing business and passes savings to customers.

### Key Points
- AWS focuses on reducing hardware, power, and operational costs
- Customers benefit from economies of scale
- Since 2006, AWS had reduced pricing **75 times** as of September 2019
- Higher-performing future resources may replace current resources at no extra charge

---

## Custom Pricing

AWS can offer **custom pricing** for:

- High-volume projects
- Unique requirements
- Cases where standard pricing models do not fit the project needs

---

## AWS Free Tier

The **AWS Free Tier** helps new customers gain hands-on experience with AWS.

### Key Points
- Free for up to **1 year** for new customers
- Applies only to certain services and options
- Lets users experiment with AWS at no cost within the allowed limits

### Example Mentioned in the Module
A new AWS customer can run a free Amazon EC2 T2 micro instance for a year while also using free usage tiers for some other AWS services.

---

## Services With No Additional Charge

AWS offers several services for no additional charge, including:

- Amazon VPC
- Elastic Beanstalk
- Auto Scaling
- AWS CloudFormation
- IAM

### Important Warning
These services themselves might be free, but the resources used with them might not be free.

### Example
- Auto Scaling has no extra charge
- But the EC2 instances launched by Auto Scaling are billed

---

## Consolidated Billing

Consolidated Billing is a feature of AWS Organizations.

### Benefits
- One bill for multiple accounts
- Easier tracking of each account’s charges
- Opportunity to reduce charges through aggregated volume discounts
- Centralized billing across multiple AWS accounts

### Note
The module also mentions AISPL accounts for India and explains that the seller of record can differ depending on account location.

---

## Key Takeaways From Section 1

- There is generally no charge for inbound data transfer
- There is generally no charge for data transfer between services in the same AWS Region
- Pay for what you use
- Start and stop anytime
- No long-term contracts are required
- Some AWS services are free, but the resources they provision may not be free

---

# Section 2: Total Cost of Ownership (TCO)

## On-Premises Versus Cloud

### On-Premises Infrastructure
- Installed locally on company-owned servers and systems
- Includes fixed costs or capital expenses
- Costs may include:
  - Facilities
  - Hardware
  - Licenses
  - Maintenance staff
- Scaling up can be expensive and time-consuming
- Scaling down does not reduce fixed costs

### Cloud Infrastructure
- Purchased from a cloud provider
- Provider manages facilities, hardware, and maintenance
- Customer pays only for what is used
- Scaling up or down is simpler
- Costs are easier to estimate because they depend on service usage

---

## What Is TCO?

**Total Cost of Ownership (TCO)** is a financial estimate used to identify the direct and indirect costs of a system.

### Why Use TCO?
- To compare the costs of running infrastructure or workloads on-premises versus on AWS
- To budget effectively
- To build the business case for moving to the cloud

### Important Idea
TCO includes not only the cost of the service itself, but also all associated ownership costs.

---

## TCO Considerations

When evaluating TCO, consider these cost categories:

### 1. Server Costs
- Hardware:
  - Servers
  - Rack chassis
  - PDUs
  - Top-of-rack switches
- Software:
  - Operating systems
  - Virtualization licenses
- Facilities:
  - Space
  - Power
  - Cooling

### 2. Storage Costs
- Storage disks
- SAN or Fibre Channel switches
- Storage administration
- Facilities:
  - Space
  - Power
  - Cooling

### 3. Network Costs
- LAN switches
- Load balancer bandwidth costs
- Network administration
- Facilities:
  - Space
  - Power
  - Cooling

### 4. IT Labor Costs
- Server administration
- Storage administration
- Network administration
- Security administration
- Application administration

### Important Note
The diagram in the module is conceptual and does not include every possible cost item.

---

## On-Premises Versus All-In Cloud Example

The module gives a sample 3-year cost comparison.

### On-Premises Example
- 1 virtual machine
- 4 CPUs
- 16 GB RAM
- Linux operating system
- Average utilization: 100%
- Optimized by RAM

### Comparable AWS Example
- 1 `m4.xlarge` instance
- 4 CPUs
- 16 GB RAM
- 3-year Partial Upfront Reserved Instance
- AWS cost includes business-level support

### Example Result
- On-premises 3-year total cost: **$167,422**
- AWS 3-year total cost: **$7,509**
- 3-year total savings: **$159,913**
- Savings can be up to **96%** in this example

### Key Lesson
AWS resources can be commissioned when needed and decommissioned when not in use, reducing overall costs.

---

## AWS Pricing Calculator

AWS provides the **AWS Pricing Calculator** to estimate monthly AWS costs.

### You Can Use It To
- Estimate monthly costs
- Identify opportunities to reduce monthly costs
- Model solutions before building them
- Explore price points and calculations behind your estimate
- Find available instance types and contract terms that meet your needs
- Name your estimate
- Create and name groups of services

### Why Groups Matter
Groups help organize estimates by:
- Cost center
- Department
- Product architecture
- Any logical grouping you choose

---

## Reading an Estimate

An AWS Pricing Calculator estimate is broken into:

- **First 12 months total**
- **Total upfront**
- **Total monthly**

### Meaning of Each
- **First 12 months total**: Upfront cost plus monthly cost for the first year
- **Total upfront**: How much is paid when setting up the AWS stack
- **Total monthly**: Estimated monthly running cost

### Example From the Module
- First 12 months total: **$886.92**
- Total upfront: **$0**
- Total monthly: **$73.91**

### Additional Point
You can create different groups to compare multiple architecture options.

---

## AWS Pricing Calculator Activity

The module includes a group activity where learners:
- Break into groups of four or five
- Use the AWS Pricing Calculator and provided specifications
- Develop a cost estimate
- Report findings back to the class

---

## Additional Benefit Considerations

TCO is useful, but a full business case should also consider broader benefits.

## Hard Benefits
- Reduced spending on compute, storage, networking, and security
- Reduced hardware and software purchases
- Reduced operational costs, backup, and disaster recovery costs
- Reduced operations personnel needs

## Soft Benefits
- Reuse of services and applications
- Increased developer productivity
- Improved customer satisfaction
- Agile business processes
- Increased global reach

### Important Idea
A TCO analysis shows cost differences, but an **ROI analysis** helps measure overall business value.

---

## Case Study: Delaware North

The module presents a TCO case study about **Delaware North**.

### Background
- Growing global company
- More than 200 locations
- 500 million customers
- $3 billion annual revenue

### Challenge
- Needed to rapidly deploy new solutions
- Needed to constantly upgrade aging equipment
- On-premises data center was too expensive and inefficient

### Criteria
Delaware North wanted a solution that could:
- Handle all workloads
- Improve efficiency and lower costs
- Eliminate repetitive work like patching
- Achieve a positive ROI

### Solution
- Moved its on-premises data center to AWS
- Eliminated **205 servers**, about **90%**
- Moved nearly all applications to AWS
- Used **3-year Amazon EC2 Reserved Instances**

### Financial Result
- Estimated **$3.5 million** savings based on a 5-year run rate

### Operational Results
- Better security compliance
- Enhanced disaster recovery
- Increased computing capacity
- New businesses could be provisioned in **one day**
- Services could be pushed out in **minutes instead of weeks**
- Continuous cost optimization and reduction

### Main Lesson From the Case Study
Cloud value is not only about lower cost. It also improves agility, speed to market, resilience, and operational efficiency.

---

# Section 3: AWS Organizations

## Introduction to AWS Organizations

**AWS Organizations** is a free account management service that lets you consolidate multiple AWS accounts into an organization that you centrally manage.

### Main Benefits
- Centrally managed access policies across accounts
- Controlled access to AWS services
- Automated AWS account creation and management
- Consolidated billing across multiple AWS accounts

### Why It Matters
AWS Organizations helps meet budgetary, security, and compliance needs more effectively.

---

## AWS Organizations Terminology

### Root
The top of the organization structure.

### Organizational Units (OUs)
- Containers for accounts within the organization
- Can also contain other OUs
- Create a hierarchy like a tree

### Accounts
- Standard AWS accounts containing AWS resources
- Each account can belong to exactly one OU
- An OU can have only one parent

### Policy Inheritance
When a policy is attached to a node in the hierarchy, it flows downward to child OUs and accounts.

---

## Key Features and Benefits

AWS Organizations enables you to:

- Create **Service Control Policies (SCPs)** to centrally control AWS services across multiple accounts
- Create groups of accounts and attach policies to them
- Automate account creation and management with APIs
- Use consolidated billing to simplify payments and benefit from aggregated usage discounts

---

## Security With AWS Organizations

AWS Organizations does **not** replace IAM.

### IAM Policies
- Applied to users, groups, and roles within an AWS account
- Can allow or deny access to AWS services, resources, or API actions
- Cannot restrict the AWS account root user

### Service Control Policies (SCPs)
- Applied at the organization, OU, or account level
- Can allow or deny access to AWS services for accounts or groups of accounts
- Affect all IAM users, groups, and roles in an account
- Also affect the AWS account root user

### Main Difference
- **IAM** controls permissions inside an account
- **SCPs** define permission guardrails across accounts in an organization

---

## Organizations Setup

The module shows these setup steps:

### Step 1
Create the organization.

### Step 2
Create organizational units.

### Step 3
Create service control policies.

### Step 4
Test restrictions.

### Notes
- This setup assumes access to two AWS accounts
- You must be able to sign in as an administrator
- The IAM Policy Simulator can help test and troubleshoot IAM and resource-based policies

---

## Limits of AWS Organizations

### Naming Rules
- Names for accounts, OUs, roots, and policies must use Unicode characters
- Names must not exceed **250 characters**

### Example Limits Mentioned
- Number of roots: **1**
- Number of OUs: **1,000**
- Number of policies: **1,000**
- Maximum size of control policy document: **5,120 bytes**
- Maximum OU nesting: **5 levels under a root**
- Invitations sent per day: **20**
- Member accounts created concurrently: **5**
- Policy attachment targets: **unlimited**

---

## Accessing AWS Organizations

You can manage AWS Organizations through:

- AWS Management Console
- AWS CLI
- SDKs
- HTTPS Query API

### Quick Comparison
- **Console**: browser-based management
- **CLI**: fast command-line operations
- **SDKs**: programming-language libraries for automation
- **HTTPS Query API**: direct programmatic access using signed HTTPS requests

---

# Section 4: AWS Billing and Cost Management

## Introduction

AWS Billing and Cost Management is the service you use to:

- Pay your AWS bill
- Monitor usage
- Budget your costs
- Forecast future usage and costs
- Plan ahead using trends and reporting

### Additional Features
- Custom time periods
- Monthly or daily granularity
- Filtering and grouping
- Trend analysis
- Optimization opportunities through cost and usage insights

---

## AWS Billing Dashboard

The Billing Dashboard helps you:

- View month-to-date AWS expenditure
- Identify the services driving most of your cost
- Understand cost trends at a high level

### Important Dashboard Views

#### Spend Summary
Shows:
- Last month’s spend
- Estimated cost month-to-date
- Forecast for the current month

#### Month-to-Date Spend by Service
Shows:
- Top AWS services by spend
- Proportion of total cost by service

---

## Cost Management Tools

From the billing dashboard, you can access:

- AWS Bills
- AWS Cost Explorer
- AWS Budgets
- AWS Cost and Usage Report

---

## AWS Bills

The **AWS Bills** page shows:

- Costs incurred over the past month for each AWS service
- Breakdown by AWS Region
- Breakdown by linked account
- The most up-to-date cost and usage information

### Main Use
Best for reviewing the detailed monthly bill.

---

## AWS Cost Explorer

**AWS Cost Explorer** is a free graphical tool for viewing AWS cost data.

### It Helps You
- Visualize costs and usage over time
- Understand spending patterns
- Manage cost trends
- Identify problem areas

### Features
- View charts of your costs
- View the past **13 months** of cost data
- Forecast the next **3 months**
- Discover cost patterns over time
- Identify the services you use most
- View metrics such as:
  - which Availability Zones have the most traffic
  - which linked AWS account is used the most

### Default Report Mentioned
- A monthly running costs report
- Overview of the past 3 months
- Forecast for the coming month with a confidence interval

---

## AWS Budgets

**AWS Budgets** uses Cost Explorer data to track budgets and forecast spending.

### You Can Use It To
- View the status of budgets
- Forecast estimated costs
- Create notifications when:
  - actual spending exceeds budget
  - forecasted spending exceeds budget

### Tracking Periods
- Monthly
- Quarterly
- Yearly

### Alert Delivery Methods
- Email
- Amazon SNS

---

## AWS Cost and Usage Report

The **AWS Cost and Usage Report** is the most comprehensive source for AWS billing and usage data.

### It Includes
- Usage for each service category
- Hourly or daily line items
- Tax allocation details if enabled

### Publishing Option
- Reports can be published to an S3 bucket
- Reports can be updated once per day

---

## Billing Dashboard Demo

The module includes a recorded demo of the **Amazon Billing Dashboard**.

---

# Section 5: Technical Support

## AWS Support

AWS Support provides a combination of tools and expertise for customers using AWS in different ways.

### Support Is Provided For
- Experimenting with AWS
- Production use of AWS
- Business-critical use of AWS

### Main Idea
AWS offers different support levels depending on customer needs, goals, and workload importance.

---

## AWS Support Resources

### Technical Account Manager (TAM)
Used for proactive guidance.

A TAM can provide:
- Architectural review
- Guidance
- Ongoing communication
- Planning, deployment, and optimization support

### AWS Trusted Advisor
Used for best practices.

Trusted Advisor:
- Acts like a customized cloud expert
- Checks for opportunities to reduce monthly expenditures
- Helps increase productivity
- Provides optimization recommendations

### AWS Support Concierge
Used for account assistance.

The Support Concierge:
- Helps with billing and account issues
- Handles non-technical inquiries
- Provides quick analysis of billing and account concerns

---

## Support Plans

AWS Support offers four support plans:

- Basic
- Developer
- Business
- Enterprise

---

## Basic Support

Includes:
- Resource Center access
- Service Health Dashboard
- Product FAQs
- Discussion forums
- Support for health checks
- 24/7 access to customer service
- Documentation
- Whitepapers
- Access to six core Trusted Advisor checks
- Access to Personal Health Dashboard

### Important Note
The Basic plan does **not** include case support.

---

## Developer Support

Best for:
- Early development on AWS
- Customers who are testing AWS
- Non-production workloads
- Customers who want technical guidance and support

---

## Business Support

Best for customers who:
- Run production workloads
- Have one or more production applications
- Use multiple AWS services
- Depend on availability, scalability, and security

---

## Enterprise Support

Best for customers who:
- Run business-critical or mission-critical workloads
- Need proactive management
- Want to increase efficiency and availability
- Want support for launches and migrations
- Need a TAM as the primary point of contact

### Key Advantage
Enterprise Support provides access to a TAM with deep technical expertise and ongoing guidance.

---

## Case Severity and Response Times

Case severity affects the response you receive.

### Severity Levels
- **Critical**: Business is at risk; critical application functions are unavailable
- **Urgent**: Business is significantly impacted; important functions are unavailable
- **High**: Important functions are impaired or degraded
- **Normal**: Non-critical functions behave abnormally, or you have a time-sensitive development question
- **Low**: General development question or feature request

### Important Note
There is no case support with the Basic Support Plan.

---

## Support Plan Scavenger Hunt Activity

The module includes a group activity where learners:

- Break into groups of four or five
- Review a business case
- Recommend the best AWS support plan
- Explain the criteria used for the recommendation

---

# Module Wrap-Up

## Module Summary

In this module, you:

- Explored the fundamentals of AWS pricing
- Reviewed TCO concepts
- Reviewed an AWS Pricing Calculator estimate
- Reviewed the Billing Dashboard
- Reviewed Technical Support options and costs

### Key Reminder
AWS Billing and Cost Management helps you:
- Access cost and usage data
- Understand spending
- Allocate costs
- Control costs
- Optimize costs

These tools help identify the main AWS cost drivers and improve planning.

---

## Sample Exam Question

### Question
Which AWS service provides infrastructure security optimization recommendations?

### Choices
- AWS Price List API
- Reserved Instances
- AWS Trusted Advisor
- Amazon EC2 Spot Fleet

### Correct Answer
**AWS Trusted Advisor**

### Why
The keyword is **recommendations**. Trusted Advisor provides best-practice recommendations for optimization, including areas related to security.

---

## Additional Resources Mentioned in the Module

- AWS Economics Center
- AWS Pricing Calculator
- Case studies and research
- Additional pricing exercises

---

# Exam-Focused Final Review

## Memorize These Points

### Pricing
- AWS cost is mainly driven by compute, storage, and data transfer
- Inbound transfer is generally free
- Outbound transfer is generally charged
- Same-Region service-to-service transfer is generally free
- Pay for what you use
- No long-term contracts are required

### Reserved Pricing
- Reserved Instances can save up to 75%
- AURI gives the largest discount
- PURI gives a smaller discount than AURI
- NURI gives the smallest discount

### TCO
- TCO includes direct and indirect costs
- On-premises includes facilities, hardware, licenses, and labor
- Cloud is usage-based and easier to scale

### AWS Pricing Calculator
- Helps estimate monthly cost
- Helps compare architecture choices
- Estimate view includes:
  - First 12 months total
  - Total upfront
  - Total monthly

### AWS Organizations
- Used to centrally manage multiple AWS accounts
- Supports OUs, SCPs, and consolidated billing
- IAM policies do not restrict the root user
- SCPs do affect the root user

### Billing Tools
- **AWS Bills**: detailed bill breakdown
- **Cost Explorer**: charts and forecasting
- **Budgets**: threshold tracking and alerts
- **Cost and Usage Report**: most detailed cost and usage data

### Support
- Four support plans: Basic, Developer, Business, Enterprise
- Trusted Advisor gives recommendations
- TAM provides proactive guidance
- Concierge handles billing and account help
- Basic support does not include case support

---

# One-Line Summary

Module 2 teaches how AWS pricing works, how to compare cloud versus on-premises costs using TCO, how to manage multiple AWS accounts with AWS Organizations, how to monitor and control spending with billing tools, and how to choose the right AWS support plan.
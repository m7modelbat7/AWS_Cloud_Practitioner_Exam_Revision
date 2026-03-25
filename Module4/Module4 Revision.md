# Module 4: AWS Cloud Security

## Module Overview

### Topics
- AWS shared responsibility model
- AWS Identity and Access Management (IAM)
- Securing a new AWS account
- Securing accounts
- Securing data on AWS
- Working to ensure compliance
- Additional security services and resources

### Activities
- AWS shared responsibility model activity

### Demo
- Recorded demonstration of IAM

### Lab
- Introduction to AWS IAM

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Recognize the shared responsibility model
- Identify the responsibility of the customer and AWS
- Recognize IAM users, groups, and roles
- Describe different types of security credentials in IAM
- Identify the steps to securing a new AWS account
- Explore IAM users and groups
- Recognize how to secure AWS data
- Recognize AWS compliance programs

---

# Section 1: AWS Shared Responsibility Model

## AWS Shared Responsibility Model

Security and compliance are a shared responsibility between AWS and the customer.

### Core Idea
The model is commonly explained as:

- **Security of the cloud** = AWS responsibility
- **Security in the cloud** = Customer responsibility

AWS manages and controls the components from the virtualization layer down to the physical facilities where AWS services operate.

The customer is responsible for what they deploy and configure in AWS.

---

## AWS Responsibility: Security of the Cloud

AWS is responsible for protecting the infrastructure that runs AWS Cloud services.

### AWS Responsibilities Include
- Physical security of data centers
- Controlled, need-based access
- Hardware infrastructure
- Software infrastructure
- Network infrastructure
- Intrusion detection
- Virtualization infrastructure
- Instance isolation
- AWS Global Infrastructure components

### Global Infrastructure Covered by AWS
- Regions
- Availability Zones
- Edge locations

### Important Meaning
AWS protects:
- The facilities
- The servers
- The storage devices
- The network devices
- The hypervisor and virtualization layer
- The foundational cloud platform itself

### Physical Protection Examples
AWS data centers include:
- Restricted access
- Security guards
- Two-factor authentication
- Access logging and review
- Video surveillance
- Disk degaussing and destruction

---

## Customer Responsibility: Security in the Cloud

Customers are responsible for the security of what they run, configure, and store in AWS.

### Customer Responsibilities Include
- EC2 instance operating systems
- OS patching and maintenance
- Applications installed on resources
- Passwords and role-based access
- Security group configuration
- Host-based firewalls
- Intrusion detection or prevention systems on customer-managed systems
- Network configuration
- Account management
- Login and permission settings for each user
- Encryption of data at rest
- Encryption of data in transit

### Customer Control Over Content
Customers control:
- What content is stored on AWS
- Which AWS services are used with that content
- In which country the content is stored
- Whether the data is masked, anonymized, or encrypted
- Who has access to the content
- How those permissions are granted, managed, and revoked

---

## Service Characteristics and Security Responsibility

The amount of customer responsibility changes depending on the AWS service model.

---

## Infrastructure as a Service (IaaS)

### Main Idea
With IaaS, the customer has more flexibility and more responsibility.

### Characteristics
- Customer configures networking and storage settings
- Customer manages more security aspects
- Customer configures access controls

### Example IaaS Services
- Amazon EC2
- Amazon EBS
- Amazon VPC

### What the Customer Handles
For example, with Amazon EC2, the customer is responsible for:
- Guest operating system updates
- Security patches
- Installed software
- Security groups

---

## Platform as a Service (PaaS)

### Main Idea
With PaaS, AWS manages more of the underlying infrastructure.

### Characteristics
- Customer does not manage the underlying hardware
- AWS handles the operating system
- AWS handles database patching
- AWS handles firewall configuration
- AWS handles disaster recovery
- Customer focuses more on code and data

### Example PaaS Services
- Amazon RDS
- AWS Elastic Beanstalk
- AWS Lambda

### Important Note
Even with PaaS, customers still manage:
- Their data
- Asset classification
- Permissions

---

## Software as a Service (SaaS)

### Main Idea
With SaaS, the software is centrally hosted and customers do not manage the supporting infrastructure.

### Characteristics
- Centrally hosted software
- Usually subscription or pay-as-you-go
- Accessed through web browser, mobile app, or API
- Customer does not manage the infrastructure underneath

### SaaS Examples in the Module
- AWS Trusted Advisor
- AWS Shield
- Amazon Chime

---

## Activity: AWS Shared Responsibility Model

The module includes an educator-led activity with two scenarios.

### Scenario 1 Answer Key

For the following items, responsibility is:

1. Upgrades and patches to the operating system on the EC2 instance  
   **Answer: The customer**

2. Physical security of the data center  
   **Answer: AWS**

3. Virtualization infrastructure  
   **Answer: AWS**

4. EC2 security group settings  
   **Answer: The customer**

5. Configuration of applications that run on the EC2 instance  
   **Answer: The customer**

6. Oracle upgrades or patches if Oracle runs as an Amazon RDS instance  
   **Answer: AWS**

7. Oracle upgrades or patches if Oracle runs on an EC2 instance  
   **Answer: The customer**

8. S3 bucket access configuration  
   **Answer: The customer**

---

### Scenario 2 Answer Key

1. Ensuring that the AWS Management Console is not hacked  
   **Answer: AWS**

2. Configuring the subnet  
   **Answer: The customer**

3. Configuring the VPC  
   **Answer: The customer**

4. Protecting against network outages in AWS Regions  
   **Answer: AWS**

5. Securing the SSH keys  
   **Answer: The customer**

6. Ensuring network isolation between AWS customers' data  
   **Answer: AWS**

7. Ensuring low-latency network connection between the web server and the S3 bucket  
   **Answer: AWS**

8. Enforcing multi-factor authentication for all user logins  
   **Answer: The customer**

---

## Section 1 Key Takeaways

- AWS and the customer share security responsibilities
- AWS is responsible for security **of** the cloud
- The customer is responsible for security **in** the cloud
- AWS protects the infrastructure, including hardware, software, networking, and facilities
- For IaaS services, customers must handle necessary security configuration and management
- Examples of customer duties include guest OS updates, patching, and firewall/security group configuration

---

# Section 2: AWS Identity and Access Management (IAM)

## What Is IAM?

AWS Identity and Access Management (IAM) is used to manage access to AWS resources.

### IAM Lets You Control
- Who can access a resource
- Which resources can be accessed
- What actions can be performed on those resources
- How resources can be accessed

### Example
You can use IAM to control who can terminate Amazon EC2 instances.

### Important Note
IAM is a **no-cost AWS account feature**.

---

## IAM Essential Components

### 1. IAM User
A person or application that can authenticate with an AWS account.

### 2. IAM Group
A collection of IAM users that are granted identical permissions.

### 3. IAM Policy
A document that defines:
- Which resources can be accessed
- What level of access is allowed

### 4. IAM Role
A mechanism for granting a set of permissions, usually temporary, for making AWS service requests.

---

## Authentication as an IAM User

When you create an IAM user, you choose the type of access they can use.

### Programmatic Access
Used for:
- AWS CLI
- AWS SDKs
- Other development tools

Authenticated with:
- Access key ID
- Secret access key

### AWS Management Console Access
Authenticated with:
- 12-digit account ID or alias
- IAM user name
- IAM password
- MFA code, if MFA is enabled

---

## IAM MFA

### What MFA Does
Multi-factor authentication increases security.

Instead of using only:
- Username
- Password

The user must also provide:
- A unique authentication code

### MFA Token Options
- Virtual MFA apps such as Google Authenticator or Authy
- U2F security key devices
- Hardware MFA devices

---

## Authorization in IAM

After authentication, authorization determines what actions are permitted.

### Key Authorization Rules
- IAM users have **no permissions by default**
- You assign permissions by creating IAM policies
- Policies are written in **JSON**
- Everything is implicitly denied unless explicitly allowed
- Anything explicitly denied is never allowed

### Best Practice
Follow the **principle of least privilege**.

### Important Scope Note
IAM service configuration is **global**, not Regional.  
IAM settings apply across all AWS Regions.

---

## Types of IAM Policies

### Identity-Based Policies
Attached to:
- IAM users
- IAM groups
- IAM roles

### Resource-Based Policies
Attached directly to a resource.

### Resource-Based Policy Characteristics
- Specify who can access the resource
- Specify what actions they can perform
- Defined inline on the resource
- Supported only by some AWS services

### Example
An Amazon S3 bucket policy is a resource-based policy.

### Important Rule
An explicit deny in a resource-based policy takes precedence over an allow statement.

---

## Lab 1: Introduction to IAM

### Lab Tasks
- Task 1: Explore the Users and Groups
- Task 2: Add Users to Groups
- Task 3: Sign-In and Test Users

### What You Practice in the Lab
- Explore pre-created IAM users and groups
- Inspect IAM policies
- Add users to groups with specific permissions
- Find and use the IAM sign-in URL
- Test how IAM policies affect access to AWS resources

### Lab Final Product
The lab ends with:
- Users: `user-1`, `user-2`, `user-3`
- Groups:
  - `EC2-Admin`
  - `EC2-Support`
  - `S3-Support`

### Example Permissions in the Lab
- S3 read-only access
- Amazon EC2 read-only access
- Amazon EC2 view, start, and stop access

---

# Section 3: Securing a New AWS Account

## Best Practices for a New AWS Account

The module recommends several steps for securing a new AWS account.

---

## Step 1: Stop Using the Root User for Daily Tasks

### Recommended Process
1. While logged in as the root user, create an IAM user for yourself with AWS Management Console access
2. Create an IAM group and give it full administrator permissions
3. Add your IAM user to the group
4. Disable and remove root user access keys, if they exist
5. Enable a password policy for users
6. Sign in with your new IAM user credentials
7. Store your root user credentials in a secure place

### Main Idea
Use the root user only when absolutely necessary.

---

## Step 2: Enable Multi-Factor Authentication (MFA)

### Recommendation
Require MFA for:
- The root user
- All IAM users

### MFA Can Also Help Control
- Programmatic access to AWS service APIs

### Token Options Mentioned
- Google Authenticator
- Authy
- U2F security keys such as YubiKey
- Hardware MFA devices

---

## Step 3: Use AWS CloudTrail

### What AWS CloudTrail Does
AWS CloudTrail tracks user activity in your account by logging API requests.

### Key Facts
- Basic CloudTrail event history is enabled by default
- It is free
- It stores the most recent **90 days** of management event history

### You Can Use It To
- View account activity
- Filter events
- Search events
- Audit API operations

### To Keep Logs Beyond 90 Days
Create a **trail**.

### Trail Setup Highlights
- Name the trail
- Apply it to all Regions
- Create an S3 bucket for log storage
- Restrict access to the log bucket

---

## Step 4: Enable Billing Reports

### Example Report
- AWS Cost and Usage Report

### Benefits
- Shows how AWS resources are used
- Shows estimated costs
- Delivered to a specified S3 bucket
- Updated at least once per day

### Cost and Usage Report
Tracks usage and estimated charges:
- By the hour
- Or by the day

---

## Section 3 Key Takeaways

Best practices to secure an AWS account include:

- Secure logins with MFA
- Delete root user access keys
- Create individual IAM users
- Grant permissions based on least privilege
- Use groups to assign permissions
- Configure a strong password policy
- Delegate using roles instead of sharing credentials
- Monitor account activity using AWS CloudTrail

---

# Section 4: Securing Accounts

## AWS Organizations

AWS Organizations helps you centrally manage multiple AWS accounts.

### Security Features
- Group accounts into organizational units (OUs)
- Attach different access policies to each OU
- Integrate with IAM
- Use service control policies (SCPs)

### Permissions Model
A user’s effective permissions are the **intersection** of:
- What AWS Organizations allows
- What IAM grants in that account

That means the user can access only what is allowed by **both**.

---

## Service Control Policies (SCPs)

### What SCPs Do
SCPs provide centralized control over the **maximum permissions** available to accounts in an organization.

### Important Facts
- SCPs are similar to IAM policies in syntax
- SCPs **never grant permissions**
- SCPs set the maximum permissions that can exist
- IAM is still required to actually grant permissions to users, groups, or roles

### Main Benefit
They help ensure that accounts follow organizational access control guidelines.

---

## AWS Shield

AWS Shield is a managed DDoS protection service.

### AWS Shield Features
- Protects applications running on AWS
- Always-on detection
- Automatic inline mitigations
- Helps minimize downtime and latency

### Versions
- **AWS Shield Standard**: enabled at no additional cost
- **AWS Shield Advanced**: optional paid service with stronger protections

### Shield Advanced Can Protect Services Such As
- Amazon EC2
- Elastic Load Balancing
- Amazon CloudFront
- AWS Global Accelerator
- Amazon Route 53

---

# Section 5: Securing Data on AWS

## Encryption of Data at Rest

### What It Means
Data at rest is data stored physically:
- On disk
- On tape

Encryption makes the data unreadable without the secret key.

### Key Points
- AWS supports encryption of data at rest
- AWS KMS can manage your encryption keys
- Encryption helps protect data even if unauthorized access occurs

### Services Mentioned as Supporting AWS KMS Encryption
- Amazon S3
- Amazon EBS
- Amazon EFS
- Amazon RDS managed databases

---

## AWS Key Management Service (AWS KMS)

AWS KMS is used to create and manage encryption keys.

### AWS KMS Features
- Create and manage encryption keys
- Control the use of encryption across AWS services and applications
- Integrates with AWS CloudTrail to log key usage
- Uses FIPS 140-2 validated hardware security modules (HSMs)

### Key Idea
You control who can access keys and how those keys are used.

---

## Encryption of Data in Transit

### What It Means
Data in transit is data moving across a network.

### Technology Used
- Transport Layer Security (TLS)
- Formerly called SSL
- Secure HTTP (HTTPS) uses TLS/SSL

### Main Benefit
Protects data against:
- Eavesdropping
- Man-in-the-middle attacks

### AWS Certificate Manager
AWS Certificate Manager helps you:
- Provision certificates
- Manage certificates
- Deploy certificates
- Renew TLS/SSL certificates

### Examples Mentioned
- Traffic between Amazon EC2 and Amazon EFS can be encrypted with TLS/SSL
- Traffic between AWS Storage Gateway and Amazon S3 can be encrypted in transit

---

## Securing Amazon S3 Buckets and Objects

### Default Behavior
Newly created S3 buckets and objects are:
- Private
- Protected by default

### When Sharing Is Required
You must carefully manage access to S3 data.

### Best Practices
- Follow least privilege
- Consider using encryption

### Access Control Options for S3
- Amazon S3 Block Public Access
- IAM policies
- Bucket policies
- Access control lists (ACLs)
- AWS Trusted Advisor bucket permission check

### Important Notes
- S3 Block Public Access is a simple and strong protection
- Bucket policies are powerful but must be written carefully
- ACLs are a legacy mechanism
- An explicit deny in a bucket policy overrides granted permissions elsewhere

---

# Section 6: Working to Ensure Compliance

## AWS Security Compliance Programs

AWS provides security compliance programs that give information about:
- AWS policies
- AWS processes
- AWS controls

### Examples Mentioned in the Module
- ISO/IEC 27001:2013
- HIPAA
- GDPR

### Main Idea
AWS provides documentation and assurance information to help customers with compliance goals.

---

## AWS Config

AWS Config is used to assess, audit, and evaluate AWS resource configurations.

### What AWS Config Does
- Continuously monitors configurations
- Records resource configurations
- Evaluates configurations against desired settings
- Reviews configuration changes
- Shows detailed configuration histories
- Simplifies compliance auditing and security analysis

### Important Note
AWS Config is a **Regional** service.

To track resources across Regions:
- Enable it in every Region you use

### Extra Capability
AWS Config has an **aggregator** feature to view data across:
- Multiple Regions
- Multiple accounts

---

## AWS Artifact

AWS Artifact is a resource for compliance-related information.

### AWS Artifact Provides
- Security reports
- Compliance reports
- Select online agreements

### Example Documents
- AWS ISO certifications
- PCI reports
- SOC reports

### Additional Capability
You can:
- Review agreements
- Accept agreements
- Track agreement status

### Example
A Business Associate Agreement (BAA) for HIPAA-related needs.

### Important Note
AWS Artifact provides documents about **AWS only**.  
Customers are still responsible for their own organization’s compliance documentation.

---

## Section 6 Key Takeaways

- AWS security compliance programs provide information about the policies, processes, and controls established and operated by AWS
- AWS Config is used to assess, audit, and evaluate AWS resource configurations
- AWS Artifact provides access to security and compliance reports

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Recognize the shared responsibility model
- Identify the responsibility of the customer and AWS
- Recognize IAM users, groups, and roles
- Describe different types of security credentials in IAM
- Identify the steps to securing a new AWS account
- Explore IAM users and groups
- Recognize how to secure AWS data
- Recognize AWS compliance programs

---

## Knowledge Check
- Complete the knowledge check at the end of the module

---

## Sample Exam Question

### Question
Which of the following is AWS's responsibility under the AWS shared responsibility model?

### Choices
- A. Configuring third-party applications
- B. Maintaining physical hardware
- C. Securing application access and data
- D. Managing custom Amazon Machine Images (AMIs)

### Correct Answer
**B. Maintaining physical hardware**

### Why
The keywords are:
- AWS's responsibility
- Shared responsibility model

Physical hardware is part of the infrastructure that AWS protects, so it is AWS’s responsibility.

---

## Additional Resources

- AWS Cloud Security
- AWS Security Resources
- AWS Security Blog
- Security Bulletins
- Vulnerability and Penetration Testing
- AWS Well-Architected Framework – Security Pillar
- IAM Best Practices documentation

---

# Exam-Focused Final Review

## Memorize These Points

### Shared Responsibility Model
- AWS = security **of** the cloud
- Customer = security **in** the cloud

### AWS Responsibility
- Data center physical security
- Hardware
- Software infrastructure
- Networking infrastructure
- Virtualization layer
- Global infrastructure

### Customer Responsibility
- OS patching on EC2
- Application configuration
- Security groups
- Firewall settings
- IAM setup
- Password and login management
- Data encryption choices
- Bucket access settings

### IAM Core Components
- User
- Group
- Policy
- Role

### IAM Rules
- No permissions by default
- Explicit allow is needed
- Explicit deny always wins
- Least privilege is best practice
- IAM is global

### New Account Security Best Practices
- Use MFA
- Avoid daily use of root
- Delete root access keys
- Create IAM users
- Use IAM groups
- Configure password policy
- Use CloudTrail
- Enable billing reports

### AWS Organizations
- Central account management
- OUs organize accounts
- SCPs define maximum permissions
- SCPs do not grant permissions
- IAM and Organizations work together

### Data Protection
- Encrypt data at rest
- Encrypt data in transit
- Use AWS KMS for key management
- Use HTTPS/TLS for secure network traffic

### S3 Security
- Buckets are private by default
- Use Block Public Access when possible
- Use IAM policies and bucket policies carefully
- ACLs are legacy
- Explicit deny overrides allow

### Compliance Tools
- AWS Config = assess, audit, evaluate configurations
- AWS Artifact = compliance and security reports

---

# One-Line Summary

Module 4 explains how AWS and the customer share security responsibilities, how IAM controls access, how to secure AWS accounts and data, and how AWS services such as CloudTrail, Organizations, KMS, Config, and Artifact help build a secure and compliant cloud environment.
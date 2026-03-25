# Module 5: Networking and Content Delivery

## Module Overview

### Topics
- Networking basics
- Amazon VPC
- VPC networking
- VPC security
- Amazon Route 53
- Amazon CloudFront

### Activities
- Label a network diagram
- Design a basic VPC architecture

### Demo
- VPC demonstration

### Lab
- Build your VPC and launch a web server

### Knowledge Check
- A knowledge check is included at the end of the module.

---

## Module Objectives

After completing this module, you should be able to:

- Recognize the basics of networking
- Describe virtual networking in the cloud with Amazon VPC
- Label a network diagram
- Design a basic VPC architecture
- Indicate the steps to build a VPC
- Identify security groups
- Create your own VPC and add additional components to it to produce a customized network
- Identify the fundamentals of Amazon Route 53
- Recognize the benefits of Amazon CloudFront

---

# Section 1: Networking Basics

## What Is a Network?

A computer network is two or more client machines that are connected together to share resources.

### Important Points
- A network can be logically partitioned into subnets
- Networking requires a device such as a router or switch
- These devices connect clients and enable communication between them

---

## IP Addresses

Each machine in a network has a unique Internet Protocol (IP) address.

### Key Points
- An IP address is a numerical label
- Machines convert the decimal IP address into binary format
- In IPv4, the address has four dot-separated numbers
- Each part represents 8 bits
- Each part can range from 0 to 255
- Total size of IPv4 is 32 bits

### Example
- `192.0.2.0`

---

## IPv4 and IPv6

### IPv4
- 32-bit address
- Example: `192.0.2.0`

### IPv6
- 128-bit address
- Example: `2600:1f18:22ba:8c00:ba86:a05e:a5ba:00FF`

### IPv6 Characteristics
- Uses eight groups
- Each group has four hexadecimal characters
- Groups are separated by colons
- Each group represents 16 bits
- Total size is 128 bits

### Why IPv6 Exists
- It supports far more devices than IPv4

---

## Classless Inter-Domain Routing (CIDR)

CIDR is a common method for describing a network.

### CIDR Format
A CIDR address contains:
- An IP address
- A slash `/`
- A number that tells how many bits are fixed for the network portion

### Example
- `192.0.2.0/24`

### Meaning of `/24`
- First 24 bits are fixed
- Last 8 bits can change
- Total available addresses: `2^8 = 256`
- Range: `192.0.2.0` to `192.0.2.255`

### Another Example
- `192.0.2.0/16`
- First 16 bits are fixed
- Last 16 bits can change
- Total available addresses: `2^16 = 65,536`
- Range: `192.0.0.0` to `192.0.255.255`

### Special Cases
- `192.0.2.0/32` = one single fixed IP address
- `0.0.0.0/0` = the entire internet

### Why CIDR Matters
CIDR is used heavily when designing VPCs and subnets.

---

## OSI Model

The Open Systems Interconnection (OSI) model is a conceptual way to understand how data travels across a network.

## OSI Layers

### Layer 7: Application
- Lets applications access the network
- Example protocols: HTTP(S), FTP, DHCP, LDAP

### Layer 6: Presentation
- Ensures the application layer can read the data
- Handles formatting and encryption
- Example: ASCII, ICA

### Layer 5: Session
- Enables orderly exchange of data
- Example: NetBIOS, RPC

### Layer 4: Transport
- Supports host-to-host communication
- Example: TCP, UDP

### Layer 3: Network
- Handles routing and packet forwarding
- Routers work here
- Example: IP

### Layer 2: Data Link
- Transfers data inside the same LAN
- Bridges and switches work here
- Example: MAC

### Layer 1: Physical
- Handles raw bit transmission over physical media
- Example: signals of 1s and 0s

### Why This Matters
The OSI model helps explain networking in general and helps you understand communication inside a VPC.

---

# Section 2: Amazon VPC

## What Is Amazon VPC?

Amazon Virtual Private Cloud (Amazon VPC) lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

### Amazon VPC Lets You Control
- Selection of IP address range
- Creation of subnets
- Configuration of route tables
- Configuration of network gateways
- Overall network configuration
- Multiple layers of security

### Main Benefit
You can design a custom cloud network with both control and isolation.

---

## VPCs and Subnets

### VPC
- A VPC is a virtual network
- It is logically isolated from other VPCs
- It is dedicated to your AWS account
- It belongs to a single AWS Region
- It can span multiple Availability Zones

### Subnet
- A subnet is a range of IP addresses inside a VPC
- A subnet belongs to only one Availability Zone
- You can create subnets in multiple Availability Zones for high availability
- Subnets are generally public or private

### Public Subnet
- Has direct access to the internet

### Private Subnet
- Does not have direct internet access

---

## IP Addressing in a VPC

When you create a VPC, you assign it an IPv4 CIDR block.

### Important Rules
- You cannot change the IPv4 address range after creating the VPC
- Largest IPv4 CIDR block for a VPC is `/16`
- Smallest IPv4 CIDR block for a VPC is `/28`
- IPv6 is also supported
- Subnet CIDR blocks cannot overlap

### Examples
- `/16` gives 65,536 addresses
- `/28` gives 16 addresses

### Important Design Point
Choose the CIDR block carefully because it cannot be changed later.

---

## Reserved IP Addresses in a Subnet

AWS reserves five IP addresses in every subnet CIDR block.

### Reserved For
- Network address
- VPC router for internal communication
- DNS resolution
- Future use
- Network broadcast address

### Example
For subnet `10.0.0.0/24`:
- Total addresses = 256
- Usable addresses = 251

---

## Public IP Address Types

### Public IPv4 Address
Can be assigned:
- Automatically using the subnet auto-assign public IP setting
- Manually by using an Elastic IP address

### Elastic IP Address
- Static public IPv4 address
- Associated with your AWS account
- Can be allocated and remapped at any time
- Useful for masking instance failure by remapping to another instance
- Additional charges might apply

### Best Practice
Release Elastic IP addresses when you no longer need them.

---

## Elastic Network Interface (ENI)

An elastic network interface is a virtual network interface.

### You Can
- Attach it to an instance
- Detach it
- Reattach it to another instance

### Important Characteristics
- Its attributes move with it
- Each EC2 instance has a default primary network interface
- The primary network interface cannot be detached
- Additional network interfaces can be attached depending on instance type

### Main Use
It helps redirect network traffic by moving the interface from one instance to another.

---

## Route Tables and Routes

A route table contains a set of rules called routes that direct traffic from your subnet.

### Each Route Has
- A destination
- A target

### Default Route
Every route table includes a local route for communication inside the VPC.

### Important Rules
- Every subnet must be associated with a route table
- A subnet can be associated with only one route table at a time
- Multiple subnets can share the same route table
- The main route table is automatically assigned to the VPC
- The local route cannot be deleted

---

## Section 2 Key Takeaways

- A VPC is a logically isolated section of the AWS Cloud
- A VPC belongs to one Region and requires a CIDR block
- A VPC is subdivided into subnets
- A subnet belongs to one Availability Zone and requires a CIDR block
- Route tables control traffic for a subnet
- Route tables have a built-in local route
- You add additional routes to the table
- The local route cannot be deleted

---

# Section 3: VPC Networking

## Internet Gateway

An internet gateway is a scalable, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet.

### Main Purposes
- Provides a target in route tables for internet traffic
- Performs network address translation for instances with public IPv4 addresses

### To Make a Subnet Public
1. Attach an internet gateway to the VPC
2. Add a route such as `0.0.0.0/0` in the route table
3. Point that route to the internet gateway

---

## NAT Gateway

A NAT gateway allows instances in a private subnet to connect outbound to the internet or other AWS services, but prevents the internet from initiating connections to those instances.

### Important Points
- Must be created in a public subnet
- Requires an Elastic IP address
- Private subnet route table must point internet-bound traffic to the NAT gateway

### Why It Is Useful
Private instances can download updates or reach outside services without becoming publicly accessible.

### NAT Gateway vs NAT Instance
AWS recommends NAT gateway for common use cases because it provides:
- Better availability
- Higher bandwidth
- Less administrative effort

---

## VPC Sharing

VPC sharing lets multiple AWS accounts in the same AWS Organization share subnets in a centrally managed VPC.

### How It Works
- One account owns the VPC
- Other accounts are participants
- Participants can create their own resources in shared subnets

### Participants Can
- View, create, modify, and delete their own application resources in the shared subnet

### Participants Cannot
- View, modify, or delete resources owned by other participants or the VPC owner

### Benefits
- Separation of duties
- Central control of VPC structure and IP allocation
- Application owners keep control of their own resources
- Security group references across participants
- Higher subnet efficiency
- Better use of VPN and Direct Connect
- Cost optimization through reuse of NAT gateways and other shared network components

---

## VPC Peering

A VPC peering connection connects two VPCs privately so they can communicate as if they are on the same network.

### You Can Peer
- VPCs in the same account
- VPCs in different AWS accounts
- VPCs in different AWS Regions

### Requirements
- Route tables must be updated on both sides

### Restrictions
- IP address ranges cannot overlap
- Transitive peering is not supported
- Only one peering connection can exist between the same two VPCs

### Important Meaning of No Transitive Peering
If VPC A is connected to VPC B, and VPC A is connected to VPC C, that does **not** mean VPC B can communicate with VPC C automatically.

---

## AWS Site-to-Site VPN

AWS Site-to-Site VPN connects your VPC to a remote network such as a corporate data center.

### Basic Steps
1. Create a virtual private gateway and attach it to the VPC
2. Define a customer gateway
3. Create routes that point remote traffic to the VPN gateway
4. Establish the Site-to-Site VPN connection
5. Configure routing through the connection

### Main Benefit
It securely connects on-premises networks to AWS over the internet.

---

## AWS Direct Connect

AWS Direct Connect provides a dedicated private network connection between your on-premises network and AWS.

### Benefits
- Reduced network costs
- Increased bandwidth throughput
- More consistent performance than internet-based connections

### Technical Note
- Uses open standard `802.1q` VLANs

### Main Use Case
Useful when internet-based connectivity is not sufficient for performance or consistency needs.

---

## VPC Endpoints

A VPC endpoint lets you privately connect your VPC to supported AWS services without using:
- An internet gateway
- A NAT device
- A VPN connection
- AWS Direct Connect

### Key Benefit
Traffic stays on the Amazon network.

## Types of VPC Endpoints

### 1. Interface Endpoints
- Powered by AWS PrivateLink
- Used for supported AWS services and certain partner or customer-hosted services
- Charged hourly plus data processing fees

### 2. Gateway Endpoints
- Used for Amazon S3 and Amazon DynamoDB
- No additional charge for the endpoint itself
- Standard data transfer and service charges still apply

---

## AWS Transit Gateway

AWS Transit Gateway simplifies network connectivity by acting as a central hub.

### Why It Exists
Point-to-point connectivity between many VPCs becomes complex and expensive to manage.

### Hub-and-Spoke Model
- Transit Gateway is the hub
- VPCs, data centers, and remote offices are the spokes

### Main Benefits
- Centralized routing
- Simpler management
- Reduced operational cost
- Easier scaling across many VPCs and accounts

### Important Idea
Instead of connecting every network to every other network, each network connects only to the Transit Gateway.

---

## Activity: Label This Network Diagram

The module includes an activity where you identify:
- Route table
- Route
- VPC
- Region
- Availability Zone
- Public subnet
- Private subnet
- Internet gateway
- NAT gateway
- Elastic network interface
- Private IP addresses

### Activity Solution Highlights
The solved diagram includes:
- VPC CIDR: `10.0.0.0/16`
- Local route in route table
- Default route `0.0.0.0/0` to `igw-id`
- Internet gateway
- Public subnet
- Private subnet
- NAT gateway
- Elastic network interface
- Private IP addresses
- Region and Availability Zone labels

---

## Recorded VPC Demonstration

The module includes a recorded VPC demonstration showing how to use the VPC Wizard to create a VPC with:
- Public subnets
- Private subnets

---

## Section 3 Key Takeaways

There are several VPC networking options, including:

- Internet gateway
- NAT gateway
- VPC endpoint
- VPC peering
- VPC sharing
- AWS Site-to-Site VPN
- AWS Direct Connect
- AWS Transit Gateway

### Summary
- Internet gateway connects your VPC to the internet
- NAT gateway lets private subnets access the internet outbound
- VPC endpoint connects your VPC privately to supported AWS services
- VPC peering connects VPCs
- VPC sharing lets multiple accounts use shared VPC subnets
- Site-to-Site VPN connects AWS to remote networks
- Direct Connect uses a dedicated network connection
- Transit Gateway is a hub-and-spoke alternative to many peering links

---

# Section 4: VPC Security

## Building Security into Your VPC

You can build security into your VPC architecture by:
- Isolating subnets where possible
- Choosing appropriate gateway or VPN connectivity
- Using firewalls

The module focuses on two firewall mechanisms:
- Security groups
- Network ACLs

---

## Security Groups

A security group acts as a virtual firewall for your instance.

### Key Characteristics
- Works at the **instance level**
- Controls inbound and outbound traffic
- Each instance can have different security groups
- Security groups are **stateful**

### Default Behavior
- Deny all inbound traffic
- Allow all outbound traffic

### Important Rule
If a request is allowed out, the response is automatically allowed back in.

### Security Group Limitations
- You can create **allow** rules only
- You cannot create deny rules

### Example Custom Rules
Inbound:
- HTTP on port 80 from `0.0.0.0/0`
- HTTPS on port 443 from `0.0.0.0/0`
- SSH on port 22 from your public IPv4 address range

Outbound:
- SQL Server traffic on port 1433 to the security group of the database servers

### Rule Evaluation
All rules are evaluated before the decision to allow traffic is made.

---

## Network ACLs

A network access control list (network ACL) is an optional security layer for your VPC.

### Key Characteristics
- Works at the **subnet level**
- Controls traffic in and out of subnets
- Each subnet must be associated with a network ACL
- A subnet can be associated with only one network ACL at a time
- A network ACL can be associated with multiple subnets
- Network ACLs are **stateless**

### Default Network ACL
- Allows all inbound IPv4 traffic
- Allows all outbound IPv4 traffic
- If applicable, also allows IPv6 traffic

### Custom Network ACL
- Denies all inbound and outbound traffic until you add rules
- Supports both allow and deny rules

### Rule Evaluation
- Rules are evaluated in number order, from lowest number upward
- AWS recommends spacing rule numbers such as 10 or 100 apart so new rules can be inserted later
- Highest rule number is `32766`

### Example Custom Rules
Inbound:
- Allow HTTPS on port 443 from `0.0.0.0/0`
- Allow SSH on port 22 from `192.0.2.0/24`
- Deny everything else

Outbound:
- Allow HTTPS on port 443 to `0.0.0.0/0`
- Allow SSH on port 22 to `192.0.2.0/24`
- Deny everything else

---

## Security Groups vs Network ACLs

| Attribute | Security Groups | Network ACLs |
|---|---|---|
| Scope | Instance level | Subnet level |
| Rule Types | Allow only | Allow and deny |
| State | Stateful | Stateless |
| Rule Processing | All rules evaluated before allow decision | Rules evaluated in number order |

### Core Difference to Memorize
- Security groups = instance firewall, stateful, allow only
- Network ACLs = subnet firewall, stateless, allow and deny

---

## Activity: Design a VPC

### Scenario
A small business has:
- A website on an EC2 instance
- Customer data stored in a backend database
- The database must remain private

### Requirements
- Web server and database server must be in separate subnets
- First network address must be `10.0.0.0`
- Each subnet must have 256 total IPv4 addresses
- Customers must always be able to reach the web server
- Database server must access the internet for patching
- Architecture must be highly available
- Must use at least one custom firewall layer

### Expected Design Thinking
A good design would typically include:
- Public subnet for web server
- Private subnet for database
- Multiple Availability Zones for high availability
- NAT gateway for private subnet outbound access
- Security groups and/or network ACLs for custom firewall protection

---

## Lab 2: Build Your VPC and Launch a Web Server

## Lab Scenario
In this lab, you:
- Create your own VPC
- Add components to produce a customized network
- Create a security group
- Launch a web server on EC2 inside the VPC

## Lab Tasks
- Create a VPC
- Create additional subnets
- Create a VPC security group
- Launch a web server instance

## Lab Final Product Architecture
- VPC: `10.0.0.0/16`
- Public subnet 1: `10.0.0.0/24`
- Private subnet 1: `10.0.1.0/24`
- Public subnet 2: `10.0.2.0/24`
- Private subnet 2: `10.0.3.0/24`
- Internet gateway
- NAT gateway
- Security group
- Public route table
- Private route table
- Web server on EC2

## Lab Debrief
In the lab, you:
- Created an Amazon VPC
- Created additional subnets
- Created an Amazon VPC security group
- Launched a web server instance on Amazon EC2

---

## Section 4 Key Takeaways

- Build security into your VPC architecture
- Isolate subnets if possible
- Choose the right gateway or VPN option
- Use firewalls
- Security groups and network ACLs are firewall options you can use to secure your VPC

---

# Section 5: Amazon Route 53

## What Is Amazon Route 53?

Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service.

### Main Functions
- Routes users to internet applications
- Translates names like `www.example.com` into IP addresses like `192.0.2.1`
- Fully supports IPv4 and IPv6
- Connects users to AWS and non-AWS infrastructure
- Performs health checks
- Supports traffic flow
- Lets you register domain names

---

## Route 53 DNS Resolution

### Basic Pattern
1. User requests a domain like `www.example.com`
2. DNS resolver checks Route 53
3. Route 53 returns the correct IP address
4. Resolver returns that IP address to the user

### Main Idea
Route 53 maps human-friendly names to machine-usable IP addresses.

---

## Route 53 Routing Policies

Amazon Route 53 supports several routing policies.

### 1. Simple Routing
- Use for a single resource
- Typical for simple single-server setups

### 2. Weighted Round Robin Routing
- Send traffic to multiple resources in proportions you define
- Useful for A/B testing

### Example
If one record weight is 3 and another is 1:
- 75% of traffic goes to weight 3
- 25% of traffic goes to weight 1

### 3. Latency Routing
- Routes users to the Region that provides the best latency
- Good for global applications

### 4. Geolocation Routing
- Routes based on user location
- Useful for localization or content restrictions

### 5. Geoproximity Routing
- Routes based on resource location
- Can also shift traffic between locations

### 6. Failover Routing
- Supports active-passive failover
- Sends traffic to backup if primary becomes unhealthy

### 7. Multivalue Answer Routing
- Returns up to eight healthy records at random
- Improves availability
- Not a replacement for a load balancer

---

## Multi-Region Deployment with Route 53

A common Route 53 use case is multi-Region deployment.

### How It Helps
- Directs users automatically to the best or closest endpoint
- Often used with load balancers in different Regions

### Benefits
- Lower latency for global users
- Better application performance
- Region-aware traffic steering

---

## Route 53 DNS Failover

Route 53 can improve application availability through DNS failover.

### You Can Use It To
- Configure backup and failover scenarios
- Enable highly available multi-Region architectures
- Create health checks

### Health Checks Can Monitor
- A specified resource such as a web server
- Other health checks
- An Amazon CloudWatch alarm

---

## Example: DNS Failover for a Multi-Tier Web Application

### Architecture Idea
- Primary route points to the application load balancer
- Secondary route points to a backup static website on Amazon S3
- Route 53 health checks monitor the primary
- If the primary fails, traffic fails over to the backup

### Main Benefit
Improves availability during outages.

---

## Section 5 Key Takeaways

- Amazon Route 53 is a highly available and scalable DNS web service
- It translates domain names into numeric IP addresses
- It supports several routing policies
- Multi-Region deployment improves global performance
- Route 53 failover improves application availability

---

# Section 6: Amazon CloudFront

## What Is a CDN?

A content delivery network (CDN) is a globally distributed system of caching servers that accelerates content delivery.

---

## What Is Amazon CloudFront?

Amazon CloudFront is a fast CDN service that securely delivers:
- Data
- Videos
- Applications
- APIs

### Main Characteristics
- Low latency
- High transfer speeds
- Developer-friendly
- Global network of edge locations and Regional edge caches
- Self-service
- Pay-as-you-go pricing

### Why It Is Different
You get high-performance content delivery without:
- Negotiated contracts
- Minimum commitments
- Traditional CDN complexity

---

## CloudFront Infrastructure

## Edge Locations
- Data centers used to serve popular content quickly
- Users are routed to the edge location with the lowest latency

## Regional Edge Caches
- Used for content that is not popular enough to stay in edge locations
- Located between the origin server and edge locations
- Larger cache than individual edge locations
- Keep more content closer to users for longer

### Main Benefit
CloudFront reduces trips back to the origin server and improves performance.

---

## CloudFront Benefits

### 1. Fast and Global
- Massively scaled
- Globally distributed
- Uses edge locations and regional caches to reduce latency

### 2. Security at the Edge
- Includes built-in protections like AWS Shield Standard at no extra cost
- Can use AWS Certificate Manager for SSL/TLS certificates

### 3. Highly Programmable
- Supports Lambda@Edge
- Lets you move logic closer to users
- Supports DevOps and CI/CD integrations

### 4. Deeply Integrated with AWS
- Connected to the AWS Global Infrastructure
- Works closely with many AWS services
- Fully configurable by API or AWS Management Console

### 5. Cost-Effective
- No minimum commitments
- Pay only for what you use
- Reduces origin load
- Avoids operating your own global cache server fleet
- No data transfer charge between CloudFront and AWS origins such as Amazon S3 or Elastic Load Balancing

---

## Amazon CloudFront Pricing

CloudFront charges are based on actual usage in four areas.

### 1. Data Transfer Out
- Charged for data transferred from CloudFront edge locations to the internet or to your origin

### 2. HTTP(S) Requests
- Charged by number of HTTP(S) requests

### 3. Invalidation Requests
- First 1,000 paths each month are free
- After that: `$0.005` per path

### 4. Dedicated IP Custom SSL
- `$600` per month per custom SSL certificate using Dedicated IP custom SSL support
- Charged hourly on a prorated basis

### Important Note
If you use other AWS services as origins, you are charged separately for those services as well.

---

## Section 6 Key Takeaways

- A CDN is a globally distributed system of caching servers that accelerates content delivery
- Amazon CloudFront is a fast CDN service that securely delivers data, videos, applications, and APIs with low latency and high transfer speeds
- CloudFront benefits include:
  - Fast and global delivery
  - Security at the edge
  - High programmability
  - Deep AWS integration
  - Cost-effectiveness

---

# Module Wrap-Up

## Module Summary

In this module, you learned how to:

- Recognize the basics of networking
- Describe virtual networking in the cloud with Amazon VPC
- Label a network diagram
- Design a basic VPC architecture
- Indicate the steps to build a VPC
- Identify security groups
- Create your own VPC and add additional components to it to produce a customized network
- Identify the fundamentals of Amazon Route 53
- Recognize the benefits of Amazon CloudFront

---

## Knowledge Check
- Complete the knowledge check at the end of the module

---

## Sample Exam Question

### Question
Which AWS networking service enables a company to create a virtual network within AWS?

### Choices
- A. AWS Config
- B. Amazon Route 53
- C. AWS Direct Connect
- D. Amazon VPC

### Correct Answer
**D. Amazon VPC**

### Why
The keywords are:
- AWS networking service
- Create a virtual network

Amazon VPC is the service used to create a virtual network inside AWS.

---

## Additional Resources

- Amazon VPC Overview page:  
  https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html

- Amazon Virtual Private Cloud Connectivity Options whitepaper:  
  https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/introduction.html

- One to Many: Evolving VPC Design AWS Architecture blog post:  
  https://aws.amazon.com/blogs/architecture/one-to-many-evolving-vpc-design/

- Amazon VPC User Guide:  
  https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html

- Amazon CloudFront overview page:  
  https://aws.amazon.com/cloudfront/?nc=sn&loc=1

---

# Exam-Focused Final Review

## Memorize These Points

### Networking Basics
- A network can be divided into subnets
- IPv4 = 32 bits
- IPv6 = 128 bits
- CIDR defines network size
- `0.0.0.0/0` means the internet
- `/32` means one specific host

### VPC Basics
- A VPC is logically isolated
- A VPC belongs to one Region
- A subnet belongs to one Availability Zone
- VPC and subnet CIDR blocks must be planned carefully
- Subnet CIDR blocks cannot overlap
- AWS reserves five IP addresses per subnet

### Route Tables
- Every subnet must be associated with a route table
- Route tables have a local route by default
- The local route cannot be deleted

### Gateways and Connectivity
- Internet gateway = internet access for public resources
- NAT gateway = outbound internet access for private resources
- VPC peering = private VPC-to-VPC communication
- Site-to-Site VPN = secure connection to remote networks
- Direct Connect = dedicated private connection to AWS
- VPC endpoint = private access to supported AWS services
- Transit Gateway = hub-and-spoke connectivity

### Security
- Security groups act at the instance level
- Network ACLs act at the subnet level
- Security groups are stateful
- Network ACLs are stateless
- Security groups allow only allow rules
- Network ACLs support allow and deny rules

### Route 53
- Route 53 is DNS
- It translates names into IP addresses
- Supports multiple routing policies
- Supports health checks
- Supports failover and multi-Region architectures

### CloudFront
- CloudFront is a CDN
- Uses edge locations and Regional edge caches
- Main benefits:
  - Low latency
  - High transfer speed
  - Security
  - Programmability
  - AWS integration
  - Cost efficiency

---

# One-Line Summary

Module 5 explains networking basics, how to build and secure virtual networks with Amazon VPC, how to connect AWS networks to the internet and other networks, how Route 53 handles DNS and routing, and how CloudFront accelerates global content delivery.
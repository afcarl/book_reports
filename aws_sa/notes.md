# AWS Solutions Architect

## Resources

 - Cloud Guru: Self paced training course
 - Cloud academy: Self pace course w/ videos, sample tests
 - Quik Labs: Quick and dirty AWS labs

## Mission 0: Set Up

 - Enrolling in C1 learning curriculum 
 - Requesting access to Cloud Academy

## Mission 1: Intro

### Videos

[Cloud Academy: AWS Technical Fundamentals](https://cloudacademy.com/amazon-web-services/aws-technical-fundamentals-aws-110-course/)

 - Overview of class, AWS product categories
 - Class will focus on core services: Compute, networking & CDN, Storage & Database 
 - Auto-scaling / Load Balancing
 - Block storage options
 - Backup and archival options 
 - Replication, object storage
 - CDN to reduce user latency, by replacating geographically
 - DB services: SQL, RDBMS, No-SQL
 - VPC: Logically separate network
 - Network services: VPN services / dedicated lines
 - Security
 - Analytic Services: Split / partition data into portions w/ Hadoop. Also, data warehousing
 - App services: Emails, SMS, MQ, credentialling
 - Management services: Deployment, document architecture, metrics & dashboarding
 - Mobile services: For mobile devs, sync data across mobile devices
 - Enterprise applications: Higher level abstraction: VNC, document storage

Additional
 - AWS Support
 - App store: OSes, security, etc

[Cloud Academy Accessing services](https://cloudacademy.com/amazon-web-services/aws-technical-fundamentals-aws-110-course/accessing-aws-services.html)

Methods to access
 - AWS management console (web): Cannote be automated
 - CLI: Can be automated.
 - APIs: All services can be accessed through APIs, calls must be written by hand
 - SDK: Available in my languages. IDE integration for Eclise and Visual Studio
 - 3rd party tools: Not included in intro. E.g. Asgard by Netflix
 - AWS mobile apps: Quick check / configuration. Limited funcitonality. Mostly read only

[Regions and AZs](https://cloudacademy.com/amazon-web-services/aws-technical-fundamentals-aws-110-course/aws-regions-and-availability-zones.html)

Regions

 - Independent collections of data centers
 - Regions are within single country
 - Data should be close to upload / users
 - IAM is shared across regions
 - Not all services and products are available across all regions

Availability Zone

 - Equivalent to data center
 - Region is collection of AZs
 - Adds letter to end of region identifier. 
 - AZs in same region have low latency links

[AWS Account](https://cloudacademy.com/amazon-web-services/aws-technical-fundamentals-aws-110-course/account-and-shared-security-responsibility-model.html)

 - Can use IAM to create individual users
 - Can add multi-factor
 - Multiple accounts and AZs: AZ lettering can be different across accounts
 - Accounts have are limited number of resources (e.g. number of s3 buckets per account)

Security: 
 - Shared model
 - EC2
   - AWS: Physical access control
   - You: You are in charge of traffic, SGs, routing policies
 - RDS
   - AWS: Patching, backup
   - You: No longer have root access

[Next steps](https://cloudacademy.com/amazon-web-services/aws-technical-fundamentals-aws-110-course/using-aws-tools-and-your-next-steps.html)

Common scenarios

 - Scaling, Service oriented architecture (SOA)
 - N-tier model
 - Rapid deployment (no provisioning lag)
 - Store on-prem data offsite
 - Disaster Recovery (DR), Hot / Cold, Hot / Hot
 - Physical proximity w/ edge locations

Review. Should be able to:

 - Describe product categories
 - Six main ways of accessing AWS services
 - Describe AWS regions and AZs
 - Describe AWS accounts
 - Describe AWS shared responsibilty model
 - Describe use cases for AWS

### Lab

 - Creating an Ec2
 - SSH'ing in. Port 22 not reachable (VPN issue?)

### Recap

 - Product categories: Compute, networking & CDN, Storage & Database 
 - IAM can be used to create individual users, within AWS account
 - AWS can be accessed through: Console, CLI, APIs, SDKs, 3rd party tools, mobile apps

## Mission 02: Compute

### Video

[Intro](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/)

Topics: 
 - Very high level
 - What is compute?
 - EC2, Elastic load balancing, EC2 container service, Elastic Bean STalk, Lambda, AWS Batch, AWS Lightsail

[What is compute?](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/what-is-compute-in-aws.html)

 - CPU and RAM

[EC2](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/elastic-cloud-compute-ec2.html)

 - Most common compute service
 - AMIs: Templates of machine images
   - Can create custom AMIs
   - Can purchase AMIs from marketplace
 - Instance types
   - Size of instance, for CPU memory, storage and networking
   - General purpose, compute optimized, GPU, memory optimized, storage optimized
 - Payment plans
   - On demand: Uninterrupted
   - Reserved: 1 or 3 year time frames. Long term, predictable workloads
   - Spot: Bid for unused resources, not guaranteed for fix period of time. Two minute warning before instance interrupted. 
 - Tenancy
   - Shared: Across multiple users. Secured by AWS
   - Dedicated instances: Hardware limited one AWS account
   - Dedicated hosts: Dedicated isntances, with additional visibility, control over physical host
 - User data: Perform boot functions, get OS updates
 - Storage options
   - Persistent: EBS. Separate from Ec2 instance, which is then mounted. Automatically replicated. Can be encrypted and snapshotted. 
   - Ephemeral: Created by Ec2 instances. Instance volume, physically attached to host. If instance is stopped, all data will be lost. 
 - Security groups
   - SG is similar to firewall for incress and egress
 - Key pairs
    - Public: Held by AWS
    - Private: User's perogative
    - Can set up additional Ec2 user accounts after first access
 - User's responsibility to patch machine
 - Common faults
   - System status checks: Issue w/ AWS hardware
   - Instance status checks: Incorrect network config, kernal issues, requires user input

[Elastic Load Balancing & Auto Scaling](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/elastic-load-balancing-and-auto-scaling.html)

Elastic Load Balancer (ELB)

 - LBs
   - Classicl Load Balance: LB routes traffic based on applciation and network info
   - Application Load Balance: Based on apps on Ec2 instace
 - Focus on classic LB
   - Will distribute requests across web servers
   - ELB will detect downed instances, stop sending traffic there
   - Can deploy more instances w/ increasing traffic
 - Setting up LB
   - Internal or external: Within VPC, can be internal only
   - AZs: Should select at least 2 different AZs. Instances must be in selected AZs
   - ELB listener: Usually HTTPS, allows ELB to check for connection requests
   - Health Check: Monitor health
   - Add instances: Can happen w/ initial config or afterwards
   - Add tags: Metadata
 - Post flight, can modify SG, EC2 instances, health checks

Auto Scaling (AS)

 - E.g. spin up servers based on CPU utilization
 - Strengths: Automatic infrastructure management, better user experience, cost reduction
 - Auto scaling and ELB can integrate to keep EC2s in sync w/ ELB
 - Launching
   - Launch config: Set up for launcing new instances. Similar to EC2 launch
   - AS Group: When to scale, AZs to use


[ECS](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/amazon-ecs.html)

ECS
 - Intro
   - Docker enabled applications distributed across EC2 instances, withouth cluster management system
   - Docker: Software to run Linux containers
   - Container: Environment for applicaiton to run, does not include OS
   - CloudWatch provides monitoring
 - Cluster
   - EC2 instances are still accessible
   - Cluster acts as resrouce pool
   - Cluster can scale, within single region
   - Instances have Docker daemon and ECS agent

[Elastic Bean Stalk](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/aws-elastic-beanstalk.html)

EBS
 - Intro: Like ECS, but for web applications. Provisioned differently 
 - Can use other AWS products
 - EBS service is free, charge for resources
 - Architecture
   - Applications: Collection of environments, configs
   - Appliation version: Section of deployable code, usually in S3
   - Environment: Application taht has been deployed
   - Environment config: How resources behave
   - Configuration templte: Baseline for creating unique config
 - Workflow
   - Create app
   - Upload version
   - Launch env
   - Manage env
 - Environments
   - Web server tier: Standard web apps, serving over port 80. 
   - Worker environment: Background processing task, communicating with other resources through SQS
 - Config options
   - Platform selection
   - Single or multiple instances
   - Deployment policy (all at once or in batches)
   - URL
   - Additional resources (e.g. RDS)
   - Permissions (through IAM)

[Lambda](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/aws-lambda.html)

 - Intro: Run your code in response to events. Serviceless and scalable environment
 - EC2 charged per hour, Lambda charged to closest 100ms and number of requests triggered
 - Lambda function: Code, configs and dependencies
   - Required resources: AWS resources
   - Max execution timeout
   - IAM role
   - Handler name: Entry point in code
   - Trigger: Can be based on AWS services
 - Workflow
   - Select BluePrint (template), configure triggers, configure

[AWS Batch](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/aws-batch.html)

 - Intro: Batch computing platform
 - Components:
   - Jobs: Unit of work. Run on EC2 as containerized application. Each job has a state at all times
   - Job definitions: E.g. num cpus, IAM role, mount points
   - Job queues: Multiple queues, possibly w/ priorities. Can also use different instance types (on demand / spot)
   - Job scheduler: Usually FIFO, with preference for higher priority queues
   - Compute environemt: Managed (service handles provisioning, scaling and termination. Created as ECS cluster), or unmanaged (provisioned, managed and maintained by you)

[Lightsail](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/amazon-lightsail.html)

 - Intro: Virtual Private Server. Similar to EC2, with more limited configs. Aimed for simpler users / small businesses
 - Can deploy from console or Lightsail's dedicated dashboard
 - Can install apps (e.g. wordpress)

[Summary](https://cloudacademy.com/amazon-web-services/compute-fundamentals-for-aws-course/summary.html)

 - Ec2: Most common compute service. 
 - ELB & AS: Create highly available, responsive apps
   - Create ELB w/ Define load balance, assign SG, configure security settings, configure health checks, add EC2 instances and add tags
 - ECS: Run docker enabled apps, without management / monitoring concerns
 - Elastic Beanstalk: Deploy web apps easily
   - Create app, upload version, launch env, manage env
 - Lambda: Serverless ability to run code based on triggers
 - Batch: Can run batch jobs
   - Parts: Jobs, job definitions, job queues, job scheduling, compute environments
 - Lightsail: Virtual Private Server, really simple solution

### Recap

 - EC2: Most common compute option
 - ECS: Run Docer applications on EC2 instance
 - ELB & Auto scale: Allow responsive apps and scaling
 - Elastic Beanstalk: Take web app code, deploy appropriate resources
 - Lambda: Run code based on triggers
 - Batch: Manage and run batch computing workloads
 - Lightsail: Easy to set up compute environments


## Mission 3: Storage

[Intro](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/)

 - Storage solutions
 - Common use cases
 - When to apply data management services

### [Cloud storage options](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/High%20Level%20view%20of%20AWS%20Storage%20Solutions.html)

Storage options

 - S3: Object store, easy to set up and use. Highly available and durable. 
   - Can version and have lifecycle rules
   - Can be encrypted, have access controls
 - Glacier: Data archives, non-critical backups
   - Several hour retrive time should be acceptable
 - EBS: Highly available, can be attached to EC2 instances
 - CloudFront: Global CDN, copying from origin location edge locations

Data Management

 - Import / export disk: Can send disk or tape media
 - Import / export snowball: Physical appliance owned by AWS
 - Storage gateway, on-prem appliance to connect on prem storage and AWS

[S3](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/s3-fundamentals.html)

 - Managed object service. 
 - S3 objects are replicated across AZs in region
 - Bucket can be 0 bytes to 5 TB
 - Objects upload parts can be up to 5 GB
 - Elastic service: AWS scales as necessary
 - Access management
   - IAM
   - Access control lists: Add permissions to individual objects
   - Bucket policies: Add or deny permissions to some or all of objects w/ in a single bucket
   - Query string auth
 - Encryption: Server side encryption (SSE) - S3 keys, SSE - KMS KMS, Server side encryption
 - Storage class options: Per object. 
 - Versioning is available, will keep all previous version of objects
 - Lifecycle rules: When to archive to glacier, expire, etc
 - Logging: All requests can be logged
 - Triggers: Can trigger SNS, SQS, lambda function
 - Cross region replication: For disaster recovery, compiance, others
 - Transfer acceleration: Can significantly speed up cross-country data 

Summary:

 - Bucket name should be unique, have requirements
 - Object / bucket max sizes

[Glacier](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/amazon-glacier.html)

 - Highly durable, high replacation across multiple facilities, multiple devices.
 - Objects are stored in Vaults

[EBS](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/amazon-elastic-block-store-ebs.html)

 - Encrypted by default. Off instance storage that can be moved between instances
 - Data is physically overwritten before drive is given to a new user
 - Encryption: Many options available
 - Snapshots: Increases durability, backing up to S3. Snapshot are incremental
   - Snapshots can be used to move EBS volumes across regions, expand EBS volume size
 - Volume types
   - Magnetic volumes: low cost, good for infrequent access
   - General purpose SSDs: Low latency
   - Provisioned IOPS: Best for IO intensive workloads. Good for DBs
   - EBS througput optimized HDD: Large sequential workloads. Magnetic
   - Cold HDD Volumes: Magnetic storage, lower throughput limit. Large, sequential workloads with low access rates

 Summary

  - EBS volumes are replicated w/ in an AZ
  - EBS snapshots are stored in S3
  - EBS is off instance storage
  - Valuable data should be backed up or replicated

### [CloudFront](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/amazon-cloudfront.html)

 - Intro: CDN to allow for lower latency, high data transfer speed
 - Supports dynamic content, invalidation, cookies, query strings, HTTP methods (e.g. POST / PUT), geotargeting

### [Import / Export Disk](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/aws-import-export-disk.html), [Import / Export Snowball](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/aws-import-export-snowball.html), [Storage Gateway](https://cloudacademy.com/amazon-web-services/aws-storage-fundamentals-2016-course/aws-storage-gateway.html)

 - Disk: Transfers data from your physical device to AWS. 
 - Snowball: Secure appliance, owned by AWS. Use App to move data over. Can verify chain of custody
 - Storage gateway: Virtual appliances to completely backup local data. Can mimic hardware interface to provide connectivity to existing local resources
 - Storage gateway common scenarios:
   - Gateway cached volume: Local cache, storage in S3
   - Gateway stored volume: Export to S3
   - Gateway virtual tape library: For legacy applications

### Summary

 - Import / Export
   - Snowball: Amazon owned appliance
   - Disk: You own the appliance
   - Storage gateway: Mimics an on-site disk storage system
 - S3: Object store
 - EBS: Disks that can be mounted
 - Glacier: Low access, cheap data store
 - Cloudfront: CN network

## Mission 4: Networking 1

### [Intro](https://cloudacademy.com/amazon-web-services/aws-networking-aws-160-course/)

Goals
 
 - VPC
 - Subnets
 - Gateways, routing tables, security groups, ACLS
 - CloudFront, Route 53, VPNs, VPGs, and ACLs
 - Load Balancing and Auto-Scaling

### [IP Addresses](https://cloudacademy.com/amazon-web-services/aws-networking-aws-160-course/ip-addressing.html)

IP Addresses

 - IP address identifies network resources. 
   - Assigned by DHCP server, or manually configured
   - Private: Cannot be reached from public network

### [VPC and Subnet Overview](https://cloudacademy.com/amazon-web-services/aws-networking-aws-160-course/aws-virtual-private-clouds-vpcs.html), [Network Traffic Control](https://cloudacademy.com/amazon-web-services/aws-networking-aws-160-course/network-traffic-control.html), [Other network services](https://cloudacademy.com/amazon-web-services/aws-networking-aws-160-course/aws-networking-services.html)

VPC

 - VPC: Controlled acces network to store, integrate / blend resources. 
 - Exist in a single region
 - Each region has a default VPC

Network Traffic Control

 - New VPCs require adding a gateway for external internet access
 - Access
   - Route tables: Direct traffic between subnets and gateways
   - Subnet can control internet acces w/ route tables
   - Access control list: Rules are evaluated in ascending orde
   - Security group: Applied to numerous resources. Similar to ACLs, but at instance levels

Other network services

 - Overview of resources
 - CloudFront: CDN
 - Route 53: Domain regitration, health check, request handling
 - AS & LB
 - VPN: Link between AWS and on prem. Used for hybrid cloud
 - VPG: Is a gateway to hit VPN
 - Direct Connect: Can create dedicated network connection between your network and AWS direct connect location

### Summary

 - VPC: Isolated network, with limited internal / external access
 - Subgroup: More grandular internal / external access rules. PArt of VPNC
 - Route 53: Domain regitration, health check, request handling
 - VPN & VPG: Link between on prem services and aWS
 - Routing Table: List of resources available w/ in VPC

## Mission II: Networking II

### [VPC](https://cloudacademy.com/amazon-web-services/amazon-vpc-networking-course/)

Intro

 - VPC: Ability to create logically isolated network. Similar private data center or corporate network.
 - Strengths
   - Connection options
   - Ability to define subnets and IP addressing scheme, control routing
   - Advanced security
   - Choice of singlue tenant hardware
 - Default VPC: Logical network already conencted to internet gateway- Can manage access within VPC
 - No chargers for creating and using a VPC
 - VPC peering: Connection between VPCs in same region

### [VPN Connectivity](https://cloudacademy.com/amazon-web-services/amazon-vpc-networking-course/vpn-connectivity.html)

Connection types

 - Corporae to Amazon VPC
 - VPC to VPC
 - End point to VPC

Corporate to VPC

 - Methods for connecting Virtual Private Gateways for connecting to corporate netowkrs

VPC to VPC

 - Peering, between VPC. Should not have overlapping IP address ranges. 

Skpping the rest of this lesson

## Mission 06: Database fundamentals

### [Intro](https://cloudacademy.com/amazon-web-services/aws-database-fundamentals-aws-180-course/)

Goals

 - Managed DBs
 - AWS RDS
 - Launch MySQL on RDS

### [RDS structure](https://cloudacademy.com/amazon-web-services/aws-database-fundamentals-aws-180-course/relational-database-service-rds-structure.html)

 - Can create EC2 and manage your own DB
 - RDS makes patched, reliable deployments easier
 - Manage: AWS handles replicaiton, backups, patching, failure detection and recovery. Can't access over SSH or Putty
 - Common to create VPC for each app. Would have to create DB subgroup
 - Parameter group: Manages configurations for DBs
 - Options group: Can manage engine specific configurations
 - AWS Aurora
 - DynamoDB (NoSQL)

### [Launching a managed RDS deployment](https://cloudacademy.com/amazon-web-services/aws-database-fundamentals-aws-180-course/launch-a-managed-rds-deployment.html)

 - RDS SG only touches app, not outside
 - Can always upgrade instance type later
 - Can scale storage and IOPS up or down as necessary

### [DynamoDB, NoSQL](https://cloudacademy.com/amazon-web-services/aws-database-fundamentals-aws-180-course/dyamodb-and-nosql.html), Aurora

DynamoDB
 - Intro to SQL vs noSQL
 - Can perform basic tasks from UI
 - Structure: Tables, Items, Attributes

Aurora

 - Easy MySQL migration
 - Mostly MySQL compliant
 - Competitive high-end performance

Redshift

 - Data warehouse, integratable w/ existing SQL tools

ElastiCache: In-memory cache for apps

## Mission 07: Security

### [Intro](https://cloudacademy.com/amazon-web-services/aws-security-fundamentals-course/)

 - AWS shared shared responsibility model
 - IAM service
 - Amazon Directory service
 - Amazon Inspector: Security posture (?)

### [Shared responsibility model](https://cloudacademy.com/amazon-web-services/aws-security-fundamentals-course/aws-shared-responsibility-model.html)

 - AWS manages security of cloud
 - User manages security of resources in cloud
   - Client and server side encryption
   - Network traffic protection
   - Patching
   - Network and firewall config
   - Identity and access management
 - AWS provides security controls. Using them is customer's responsibility
 - Infrastructure services: AWS provides compute / physical resources. You are responsible for patching, data, etc. E.g. S3 or EC2
 - Managed services: Use AWS infrastructure to deliver specific service. AWS handles underlying work (e.g. RDS)

 - Acceptable use policies: Nothing illegal or offensive, etc. 

### [IAM](https://cloudacademy.com/amazon-web-services/aws-security-fundamentals-course/identity-and-access-management.html)

 - Allows access control to resources
 - Definitions
   - Authentication: Identity and verification. Proving you are who you say you are. 
   - Authorization: Once authentication occurs, determines access level and priviledges
   - Access control: Limit access to resources
 - IAM is a global service (across regions)
 - Concepts
   - Root users: Not limited in any way
   - IAM user: Can be assigned roles or policies. Person / service / physical device. IAM user does not require password
   - Access key: Can interact w/ AWS programatically
   - MFA: Another layer of security
 - IAM groups: Assign permissions to group instead of user
 - Roles: Shared by entities. They have no credentials. 
   - Only need to specify who can assume the role
   - E.g. Ec2 isntances that need to backup to an S3 bucket. Assign role, don't need to store credentials on EC2
 - Policies: How to define permissions to roles. Can allow or deny actions

Recap

 - Root user is most powerful user, and cannot be restricted
 - IAM users are identities, controlled through IAM
 - IAM groups simplify policy management
 - Roles provide temporary access to authenticated users
 - Roles are essentially identities

### [Directory Services](https://cloudacademy.com/amazon-web-services/aws-security-fundamentals-course/directory-service.html)

Directory service
 
 - Similar to DB
 - Data rarely changes, but is read often
 - Identifies resources and access
 - Single point of management
 
 - Cloud Directory: Highly available, multi-tenant. Best for large groups objects. Can organize data hierarchically
 - Directory service: Good match for user management. Equivalent to Microsoft AD service
   - Microsoft AD: Good for 5k+ users
   - Simple AD: Good for smaller number of users
   - AD Connector: Re-direct cloud based requests to on-prem. Directory gateway
 - AD services are managed services

### [Inspector](https://cloudacademy.com/amazon-web-services/aws-security-fundamentals-course/inspector.html)

 - Evaluates security of resources on AWS
 - Automated security assesment tool
 - Concepts
   - Agent: Should be installed on EC2
   - Application: Collection of resources, working toward common goal. Assessment target. Can tag resources w/ tags
   - Assessment, findings
   - Rules and rule packages: Identify best practices and exposures. Each has severity level
 - Launcing
   - Requires inspector IAM role
   - Tag EC2 isntanes
   - Install agents
   - Define assessment
 - Example finding: OpenSSL package should be updated

### [Web Application Firewell (WAF)](https://cloudacademy.com/amazon-web-services/aws-security-fundamentals-course/web-application-firewall.html)

Goals

 - Recognize and describe WAF
 - Describe core components

Intro
 
 - Managed service, control who has access to service

Concepts
 
 - Between web application and client
 - Any client can make a request

Threats
 
 - SQL injection
 - XSS
 - DDoS

CloudFront

 - CDN
 - WAF: Conditions, rules, Web access control lists
 - ACL: Combine rules, Accept / Block / count, default action

AWS shield advance

 - DDOS protection

### [Course summary](https://cloudacademy.com/amazon-web-services/aws-security-fundamentals-course/security-overview.html)

 - Shared security model: AWS handles cloud, customer handles everything in cloud
 - Access management: AWS controls physical access, customer handles virtual services
 - IAM: Root user has complete control, cannot be restricted
   - Users, groups, policies
 - Cloud Directory: Highly available directory store
 - AWS Directory services: AD replacements
 - Inspector: Automated security assessments
 - WAF: Firewall

## Mission 8: Networking III

[Intro](https://cloudacademy.com/amazon-web-services/amazon-route53-dns-course/)

Goals

 - Purchasing Domain name
 - Archtiectures for websites

Route 53: PRovides DNS lookup
 
 - Hosted zone: Info about how to route traffic
 - Routing policy. Simple, weighted, latency, failover, geolocation

### [DNS service](https://cloudacademy.com/amazon-web-services/amazon-route53-dns-course/domain-name-management-with-amazon-route-53.html), [Active passive fallover](https://cloudacademy.com/amazon-web-services/amazon-route53-dns-course/dns-active-passive-failover.html), [Latency based routing](https://cloudacademy.com/amazon-web-services/amazon-route53-dns-course/dns-latency-based-routing-amazon-route-53.html)

DNS Services

 - Purchasing domain names
 - Can transfer domain names

DNS Failover

 - Active-Active
 - Active-Passive
 - Mixed configuration
 - Determined using health checks
 - Record set: Which machine to send requests to
 - Public hosted zone: Holds information about where to route traffic to

Latency based routing

 - Similar to active-passive, but w/ latency

### [Private hosted zone](https://cloudacademy.com/amazon-web-services/amazon-route53-dns-course/dns-private-hosted-zones-virtual-private-cloud.html)

Private hosted zone

 - DNS zone assocated w/ VPC for internal routing
 - Private takes precedence over public hosted zone

### [Health checks and DNS fail over](https://cloudacademy.com/amazon-web-services/amazon-route53-dns-course/health-checks-and-dns-failover.html)

 - If no health check, all instances are assumed healthy
 - If all resources are unhealthy, will act as if all were healthy

 AWS CloudHSM
  AWS Direct Connect 
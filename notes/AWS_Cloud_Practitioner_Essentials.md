---
title: AWS Cloud Practitioner Essentials
created: '2024-02-15T22:39:37.666Z'
modified: '2024-02-19T01:11:15.402Z'
---

# AWS Cloud Practitioner Essentials

## Module 1 - Introduction to Amazon Web Services

### Introduction 
* AWS offers services such as computing, storage, and network security. This has many applications.
* The client-server model is how many IT businesses operate. Clients make a request, and with permissions, the server responds to that request. 
* The server of the client-server model is called the Amazon Elastic Compute Cloud (EC2).
* With AWS, **you only pay for what you use**. When you need instances, you have them. If you don't, you don't pay for them. 
* Going back to the client-server model, a client can be a web browser or desktop application that a person interacts with to make requests to computer servers.

### Cloud Computing
* Cloud Computing is the on-demand delivery of IT resources over the internet with pay-as-you-go pricing. Resources are already available.
* `Undifferentiated heavy lifting of IT` tasks are repetitive and time-consuming tasks that are taken care of by AWS.
#### Deployment Models

##### Cloud-Based Deployment
* Run all parts of the application in the cloud.
* Migrate existing applications to the cloud.
* Desgin and build new applications in the cloud.
##### On-Premises Deployment
* Deploy resources by using virtualization and resource management tools.
* Increase resource utilization by using application management and virtualization technologies. 
* Also known as **private cloud development**.
##### Hybrid Deployment
* Connect cloud-based resources to on-premises infrastructure.
* Integrate cloud-based resources with legacy IT applications.
* Sometimes used if government regulations require certain records on premises.

#### Benefits of cloud computing
* Less of an upfront expense for resources (no need to invest in data centers, physical servers, etc.)
* No focus on running and maintaining data centers.
* No need to predict how much infrastructure capacity is needed before deployment. Scale in or out in response to demand.
* Lower variable cost.
* Increased speed and agility.
* Global access with minimal delays due to global infrastructure.

## Module 2 - Compute in the Cloud

### Introduction
* Amazon Elastic Compute Cloud (EC2) is a service that provides access to virtual servers.
* AWS has already built datacenters, purchased servers, and set them up for instant usage.
* All that needs to be done is request usage, which can be terminated at any time. You only pay for running instances.
* Uses virtualization technology, the host is shared with other instances (virtual machines). A hypervisor shares physical resources between virtual machines.
* Sharing underlying hardware is called **multi-tenancy**.
* One EC2 instance is not aware of any other instances on that host. 
* You can configure the instance as you want, with different operating systems and software.
* EC2 instances are resizable. If a server is maxed-out, it can be given more memory and CPU. This is known as **vertical scaling**.
* The user controls the networking aspect of EC2.
* This is known as a Compute as a Service model (CaaS).
#### How Amazon EC2 Works
* First, you launch an instance. A template is selected with basic configurations for your instance. This includes the operating system, application server, or appliations. You can also select the specific hardware configuration of the instance. Security settings are specified to control the network traffic that can flow in and out of the instance. 
* Next, you connect to the instance. This can be done by connecting directly to the instance through programs and applications, or the user can connect by logging in and accessing the computer desktop.
* After connecting to the instance, you can use it. You can run commands to install software, add storage, manipulate files, and more. 

### Amazon EC2 Instance Types
* There are a variety of tasks that need to be done with different skillsets when it comes to computing. AWS has different types of EC2 instances optimized for different tasks.
* Each Amazon EC2 instance type is grouped under an instance family for certain types of tasks. These offer varying levels of memory, CPU, and networking.
* Different families include **General Purpose**, **Compute optimized**, **Memory optimized**, **Accelerated Computing**, and **Storage optimized**.
* General purposes instances contain a balanced load of resources, they can be used for applications such as application servers, gaming servers, small/medium databases, web servers, and code repositories.
* Compute optimized instances are ideal for compute-bound applications with high-performance processors. This includes gaming servers, High Performance Computing (HPC), and scientific modeling.
* Memory optimized instances are designed to deliver fast performance for workloads that process large datasets in memory. High-performance databases, and real-time processing are some examples.
* Accelerated computing instances use hardware accelerators (coprocessors). These are good for floating-point number calculations, graphics processing, and data-pattern matching.
* Storage optimized instances are designed for workloads with high, sequential read and write access to large datasets on local storage. Examples include distributed file systems, data warehousing, and high-frequency online transcation processing systems. These instances deliver thousands of low-latency input/output operations per second (IOPS).

### Amazon EC2 Pricing
* **On-demand Instances**
  * Pay as you go, per-second or per-hour.
  * No contracts, upfront costs, or minimum commitments.
  * Ideal for short-term, irregular, or interruptible workloads.
  * Provides a baseline for average costs.

* **Savings Plans**
  * Offers low pricing in exchange for consistent instance usage.
  * Contracts for one or three years.
  * Up to 72% savings.
  * Applies to Fargate and Lambda as well.

* **Reserved Instances**
  * For reserved and steady workloads.
  * One or three-year terms.
  * Up to 75% savings.
  * Payment options: all up-front, partial up-front, or no up-front.
  * **Standard Reserved Instances**
    * Specify instance type, size, platform (OS), and tenancy.
    * Suited for steady-state applications.
  * **Convertible Reserved Instances**
    * Flexibility to change availability zones or instance types.
    * Smaller discount, charged on-demand rates until modification.

* **Spot Instances**
  * Request spare EC2 computing capacity at up to 92% off.
  * Amazon may reclaim service with up to two minutes notice.
  * Suitable for workloads that can tolerate interruptions.
  * Best for batch processing workloads.

* **Dedicated Hosts**
  * Physical servers dedicated for your use.
  * Ensures compliance with specific policies.
  * No shared tenancy.

### Scaling Amazon EC2
* Scalability and Elasticity (how capacity can grow and shrink based on business needs) is a selling point of AWS.
* Workloads commonly vary over time. Data centers must purchase enough hardware to service their customers during peak business, most of the year they will have idle resources.
* AWS allows you to provision your workload to demand.
* AWS has no single point of failure. You can clone instances so that if one goes down or there is an increase in demand, you can scale up to deal with that demand. 
* **Amazon EC2 Auto Scaling**
  * Enables you to automatically add or remove Amazon EC2 instances in response to changing application demand. 
  * **Dynamic Scaling** responds to changing demand.
  * **Predictive Scaling** automatically schedules the right number of Amazon EC2 instances based on predicted demand.
  * These two features can be used in tandem.
  * You can deal with growing demand by *scaling up* or *scaling out*.
    * Scaling up means that you add more power to an instance.
    * Scaling out means that you add more instances to the same task. This allows you to process multiple requests at the same time. 
    * Instances can be stopped after they are no longer needed. You always have the correct number of instances.
  * When you create an Auto Scaling group, you can set the minimum capacity of Amazon EC2 instances. Then you can set a desired capacity. Finally, you can set a maximum capacity.
    * **You only pay for what you need.**
  
  ### Directing Traffic with Elastic Load Balancing
  * When you have multiple EC2 instances all running the same program, how do you route requests to instances to process that request?
    * A load balancer takes in requests and routes them to different instances to stabilize traffic.
  * You can use a custom third-party load balancer (which is difficult and tedious) or you can properly distribute traffic with **Elastic Load Balancing (ELB)**
  * ELB is a Regional Construct, it is automatically scalable. Able to handle different levels of throughput with no added costs.
  * ELB acts as a single point of contact for all incoming web traffic to your auto scaling group. As you add or remove Amazon EC2 instances in response to the incoming traffic, these requests route to the load balancer first. Then, the requests spread across multiple resources that will handle them.
  * ELB is not used for just incoming traffic. Front-end instances can communicate with back-end instances through the ELB. The ELB directs traffic to an instance with the least outstanding requests.
    * This is ***decoupled architecture**.
  * ELB is just one method for handling loads. Different architectures can benefit from different load balancers.

  ### Messaging and Queuing
  * Applications send messages to eachother to communicate. When they directly communicate, they are called **tightly coupled**. If a single component fails, this will cause problems to the whole system. 
  * **Loosely coupled architectures** contain a buffer between applications. This way, the messages between applications are preserved if one application fails. This prevents lost data and new instances can be made to process the outstanding messages.
  * Amazon Simple Queue Service (SQS) allows you to send, store, and receive messages between software at any volume. The data contained within a message is called a payload and is protected until delivery. These scale automatically and are reliable.
  * Amazon Simple Notification Service (SNS) is used to send out messages to services, but can also send notifications to end users. It uses a publish subscribe (pubsub) model, you can create an SNS topic which is a channel for messages to be delivered. You can add subscribers to the channel, who will all receive the message. These subscribers can also be endpoints. Can even use SMS, mobile push, and email. 
  * **Monolithic vs Microservice Approaches**
    * Applications are made of multiple components. The components communicate with eachother to transmit data, fulfill requests, and keep the application running. If components are tightly coupled, this is considered a monolithic application. **If a single component fails, other components fail.**
    * Applications can be designed through a microservices approach, where components are loosely coupled. **If a single component fails, the other componenets continue to work because they are communicating with eachother. This prevents the entire application from failing.**

  ### Additional Compute Services
  * EC2 requires that you setup and manage your fleet of instances over time. You are responsible for packaging instances, scaling them, and architecting solutions. There are still management duties.
  * AWS offers multiple **serverless** options. This means that **you cannot see or access the underlying infrastructure/instances hosting your application**.
    * All management of the environment from scaling, high availability, and maintenance are taken care of for you.
  * AWS lambda allows you to upload your code as a lambda function, wait for a trigger, and then that trigger runs your code in a managed environment. Lambda will scale your function to meet your demand.
    * Lambda is designed to run code under 15 minutes. **Not for deep learning**, but for simple requests such as a webserver backend. 
    * An example use-case of Amazon Lambda is resizing images before uploading them to the AWS Cloud. Every time an image is uploaded, a Lambda function triggers.
    * With Lambda you only pay for the compute time that you use. 
  * In AWS, you can also build and run containerized applications. 
    * Containers provide a way to package your application's code dependencies into a single object. These can also be used for processes and workflows with requirements for security, reliability, and scability. 
    * **Amazon Elastic Container Service (ECS)**:
      * A highly scalable, high-performance container management system that enables you to run and scale containerized applications on AWS.
      * Supports Docker containers. Docker is a software platform that enables you to build, test, and deploy applications quickly.
      * You can use API calls to launch and stop Docker-enabled applications with ECS.
    * **Amazon Elastic Kubernetes Service (EKS)**:
      * A fully managed service that you can use to run Kubernetes on AWS. 
      * Kubernetes is open-source software that enables you to deploy and manage containerized applications at scale. 
    * **Docker is a container runtime, while Kubernetes is a platform for running and managing containers from many container runtimes.** Kubernetes supports Docker.
  * AWS Fargate is a serverless compute engine for containers. It works with both Amazon ECS and EKS. You do not need to provision or manage servers, it manages server infrastructure for you. 

## Module 3 - Global Infrastructure and Reliability

### Introduction
* AWS has high availability and fault-tolerance.

### AWS Global Infrastructure
* AWS has global regions which are connected through fiber networks. 
* Each region has multiple availability zones which are connected with low latency, high throughput, higly redundant networking.
  * If one availability zone fails, your application can continue to run in another availability zone with no interruption. 
  * There are three or more availability zones within an AWS region.
  * **An availability zone is a logical data center. Each zone is backed up by one or more physical data centers, with the largest backed up by five.**
    * **No two zones share a data center.**
    * Availability zones are tens of miles apart from eachother. This allows for low latency.
  * **AWS reccomends running in AT LEAST two availability zones in a region.**
* Data does not leave a region unless you explicitly tell it to do so.
* There are four business factors that come into consideration when selecting a region:
  * Compliance - Government/legal requirements.
  * Proximity - Being close to your customers and having low latency.
  * Available services - Different regions have different AWS services available.
  * Pricing - Different regions have different costs due to taxes and infrastructure.
* ELB is a regional construct. It can load balances across availability zones across multiple EC2 instances. This is a **regionally scoped service**.

### Edge Locations
* An edge location is a site that Amazon CloudFront uses to store cached copies of your content closer to customers over the world for faster delivery.
  * Caching copies of data uses the concept of Content Delivery Networks (CDN). This provides low latency and high transfer speeds.
* Amazon Route 53 is a DNS service that directs customers to the correct web locations with low latency. 
* AWS Outposts allows you to install a mini-region inside of your own data center. 

### How to Provision AWS Resources
* In AWS, EVERYTHING is an API call.
* You can interact with AWS through the Web Management Console, the Command Line Interface (CLI), or AWS Software Development Kits (SDKs)
* AWS Elastic Beanstalk builds your environment for you and makes it easy to save environment configurations. 
  * Performs capacity adjustment, load balancing, automatic scaling, and application health monitoring. 
* AWS CloudFormation is an Infrastructure as code tool used to define a wide variety of AWS resources.
  * You define resources in a template ans CloudFormation will provision them in parallel. It calls APIs for you. You can create identical environments across regions.
  * You treat your infrastructure as code. 
* Overall, you can use the CLI to script interactions, use SDKs to write programs to interact, or use Elastic BeanStalk or CloudFormation to manage resources for you.

## Module 4 - Networking

### Introduction
* Amazon Virtual Private Cloud (VPCs) let you provision a logically isolated section of the AWS cloud where you can launch AWS resurces in a virtual network that you define. 
  * These can be public facing (have access to the internet) or private facing (usually for backend services like databses or application servers).
  * The public and private grouping of resources are known as subnets and are ranges of IP addresses in your VPC.

### Connectivity to AWS
* A VPC is essentially your own private network in AWS. It allows you to define a private IP range for your AWS resources, and you place things like EC2 instances and ELBs inside of it.
  * You place resources into different subnets. Subnets are chunks of IP addresses in your VPC that allow you to group resources together. Subnets control whether resources are publicly or privately available. 
    * A subnet is a section of a VPC that can contain resources such as Amazon EC2 instances.
* If you have resources that you only want to be reachable if someone is logged into a private network, you can configure this with gateways.
  * An internet gatway (IGW) is like a doorway open to the public. Without it, no one can reach the resources placed inside.
  * A VPC with all internal private resources doesn't want an internet gateway attached. A Virtual Private Gateway allows you to create a VPN connection between a private network.
    * Private gateways are private and encrypted, but they still use a regular internet connection that is being shared and has bandwidth.
      * With AWS, you can use AWS Direct Connect. This allows you to establish a completely private, dedicated fiber connection from your data center to AWS. This can help with regulatory issues and prevent any bandwidth issues.
      * A virtual private gateway only allows traffic into the VPC if it comes from an approved network.
* Public subnets have access to the internet gateway, private subnets do not. 

### Subnets and Network Access Control Lists
  * When a customer requests data from an application hosted in the AWS Cloud, this request is sent as a packet. A packet is a unit of data sent over the internet or network. 
  * This packet enters a VPC through an internet gateway. Before a packet can enter into a subnet or exit from a subnet, it checks for permissions. These permissions indicate who sent the packet and how the packet is trying to communicate with the resources in a subnet. 
  * The VPC component that checks packet permissions for subnets is a **network access control list (ACL)**. It is a virtual firewall that controls inbound and outbound traffic at the subnet level.
    * Each AWS account includes a default network ACL. By default, it allows all inbound and outbound traffic, but you can modify it by adding your own rules. For custom network ACLs, all inbound and outbound traffic is denied until you add rules to specify which traffic to allow. 
    * Network ACLs perform stateless packet filtering. They remember nothing and check packets that cross the subnet border each way (inbound and outbound). Even if a packet previously crossed, it is check again.
  * The VPC component that checks packet permissions for an Amazon EC2 instance is a **security group**. It is a virtual firewall that controls inbound and outbound traffic for an Amazon EC2 instance.
    * By default, a security group denies all inbound traffic and allows all outbound traffic. You can add custom rules to configure which traffic should be allowed.
    * If you have multiple Amazon EC2 instances within the same VPC, you can associate them with the same security group or use different security groups for each instance. 
    * Security groups perform stateful packet filtering. They remember previous decisions made for incoming packets. 

  ### Global Networking
  * Domain Name System (DNS) translates domain names to IP addresses. 
    * A DNS resolver receives the domain name request, asks the company DNS server for the IP address, and the company DNS server responds by providing the IP address.
  * Amazon Route 53 can direct traffic to different endpoints. It connects user requests to infrastructure running in AWS and can route outside of AWS.
    * Route 53 interacts with Amazon CloudFront. A user requests data from a company's website, Route 53 uses DNS resolution to identify the corresponding IP address, and the customers request is sent to the nearest edge location through CloudFront, and CloudFront connects to the Application Load Balancer, which sends the incoming packet to an Amazon EC2 instance.

## Module 5 - Storage and Databases

### Introduction
* AWS offers a variety of services to store data to meet their clients needs.

### Instance Stores and Amazon Elastic Block Store
* As applications run, they need access to block-level storage. Memory is partitioned into blocks and only the blocks that change need to be updated (hard drive).
  * EC2 instances can have **instance store volumes**, which are physically attached to the host like a normal hard-drive. All data written to the instance store volume is deleted when the instance shuts down (virtual machines change hosts). Temporary storage.
    * Used for temporary data. Do NOT write important data to this.
  * Amazon Elastic Block Store (EBS) creates virtual hard drives (called EBS volumes) that attach to EC2 instances. They are not tied directly to the host the instance is writing on. This data CAN persist between starts and stops.
    * You specify the size, type, and configuration of the memory and attach to an EC2 instance. You can then configure your application to write to the volume.
    * EBS allows you to take snapshots (incremental backups) in case your data becomes corrupted. These snapshots can be restored if problems arise.
      * When creating snapshots, only data that has changed since the most recent snapshot is backed up.
    * EBS is also block-level storage. 

### Amazon Simple Storage Service (Amazon S3)
* Allows you to store and retrieve an unlimited amount of data at any scale.
* Data is stored as objects and objects are stored in buckets. You can upload a maximum object size of 5 TB.
  * Objects are versioned, previous data is versioned.
  * Data can have permissions and different storage use cases.
* There are different storage tiers.
  * Amazon S3 Standard comes with 11 nines of durability. This has a 99.999999999% chance of being intact after one year. It has a higher cost.
   * Amazon S3 static website hosting uploads all static web assets into a bucket and hosts this as a static website. 
  * Amazon S3 Standard-Infrequent Access (S3 Standard-IA) is for data that is not used frequently but requires quick access when needed. Good for backups.
    * Has a lower storage price but a higher retrieval price.
  * S3 One Zone-Infrequent Access (S3 One Zone-IA) stores data in a single Availability Zone and has a lower price than Amazon S3 Standard-IA.
    * Data is only stored in one Availability Zone. S3 Standard and S3 Standard-IA store data in a minimum of three Availability Zones.
    * Good for when you want to save costs on storage and you can easily reproduce data in the event of an Availability Zone failure.
  * Amazon S3 Intelligent-Tiering is goof for data with unknown or changing access patterns. It requires a small monthly monitoring and automation fee per object.
    * Monitors objects' access patterns. If you haven't accessed an object for 30 consecutive days, it automatically moves it to the infrequent access tier, S3 Standard-IA. 
      * If you access an object in the infrequent access tier, it automatically moves it to S3 Standard.
  * S3 Glacier Instant Retrieval works well for archived data that requires immediate access. It can retrieve objects in a few milliseconds. 
  * Amazon S3 Glacier Flexible Retrieval is good for audit data. It can have vaults with archives that are good for long-term access but not necessarily speedy access.
    * You can use Write once/read many (WORM) where data cannot be changed after being written.
    * Different levels of retrieval speed. Can be from 1 minute to 12 hours. 
  * S3 Glacier Deep Archive is the lowest-cost object storage class ideal for archiving. You can retrieve objects within 12 hours. Ideal for long-term retention. Stored in at least three geographically separated Availability Zones. 
  * S3 Outposts creates S3 buckets on Amazon S3 Outposts. This makes it easy to retrieve, store, and access data on AWS Outposts. 
* Amazon S3 Lifecycle management can move data automatically between tiers. No need to change application code to store data.
* In object storage, each object consists of data, metadata, and a key. 
  * Data is a file. Metadata contains information about what the data is, how it is used, the object size, and so on. An object's key is its unique identifier.
* Amazon EBS can have sizes of up to 16 TiB (17.6 TB), they survive termination of EC2 instance, solid state by default, with HDD options.
* Amazon S3 has unlimited storage, up to 5000 GB objects, are ideal for WORM, have high durability.
* S3 is web enabled (each file can have an access URL), regionally distributed, offers cost savings, and is serverless. 
* Object storage treats any file as a complete object. If there is a change to the object, you must reupload the entire file. 
  * Block storage breaks down those blocks into small parts. If you were working on a huge video file and make a bunch of micro edits, using EDS is the better case.

### Amazon Elastic File System (Amazon EFS)
* Multiple instances can access the data in EFS at the same time.
* Scales up and down as needed.
* Amazon EBS volumes attach to EC2 instances. They are an Availability Zone level resource (need to be in the same AZ to attach EC2 instances). Doesn't automatically scale.
* **Amazon EFS can have multiple instances reading/writing simultaneously. It is a linux file system, a Regional resource, and automatically scales.**

### Amazon Relational Database Service (Amazon RDS)
* Used when you need to maintain relationships between various types of data and track this.
  * A lift-and-shift migration puts your on-premise environment and database onto an EC2 instance.
* Amazon RDS is a service that enable you to run relational databases in the AWS Cloud. It automates tasks such as hardware provisioning, database setup, patching, and backups. 
  * Amazon RDS includes automated patching, backups, redundancy, failover, and disaster recovery.
  * You can use AWS Lambda to query your database from a serverless application.
  * Six Amazon RDS database engines. Incudes Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and Microsoft SQL Server.
* Amazon Aurora is a managed database, compatible with MySQL and PostgreSQL databases. 
  * Up to five times faster than standard MySQL and three times than PostgreSQL databases.
  * Reduces unnecessary input/output operations.
  * 1/10th the cost of commercial databases. Data replicated across facilities for 6 copies at any time. Up to 15 read replicas to offload reads and scale performance. Continous backup to Amazon S3 and includes point-in-time recovery.

### Amazon DynamoDB
* DynamoDB is a serverless database. 
  * You create tables, which is where you can store and query data. 
  * Data is organized into items with attributes.
  * DynamoDB manages underlying storage for you, redundantly, and scales automatically.
  * single-digit ms response time
  * NOT a relational database. Less rigid and high access rate. AKA NoSQL. Simple flexible schemas.
  * **You write querys based on a small subset of attributes known as keys.** Tend to be simpler.
  * Fully managed, highly scalable.
* Amazon RDS has automatic high availability, custom ownership of data, customer ownership of schema, and custom control of network.
  * Better for complex data spread across multiple tables. Built for business analytics. 
  * Complex functionality creates lag.
* Amazon DynamoDB has a key-value access system, massive throughput, PB size potential, and granular API access.
  * Use case is for almost anything besides complex relationships. 

### Amazon Redshift
* Once data becomes too complex with traditional relational databases, you shift your focus to data warehouses.
  * Useful for looking backwards in time.
  * Maintenance of a data warehouse is difficult, maintaining the engine is tedious
* **Amazon redshift is data warehousing as a service. It can be used for big data analytics.**
  * An SQL query can be used to run against exobytes of data in warehouses.
  * Up to 10x higher performance than traditional databases when it comes to high workloads.
  * When you need big data solutions, Redshift allows you to start with a single API call. 

### AWS Database Migration Service
* If you have a database on-premise or in the cloud already, Amazon DMS can help you migrate existing databases onto AWS in a secure and easy fashion.
  * The source database remains fully operational during the migration.
  * Source and target don't need to be of the same type.
    * The same type of database migration is known as homogenization.
    * Heterogeneous migrations are a two-step process. Schema structures, data types, and database code must be converted using the AWS conversion tool. Then DMS is used.
  * DMS can be used for development and test database migrations (test against prod. data), database consolidation (multiple into one), and continous replication (disaster recovery/geographic separation).

### Additional Database Services
* There is no one-size-fits-all database for all purposes.
* Amazon DocumentDB is great for content management, catalogs, user profiles.
* Amazon Neptune is great for social networks. It is a graph database. Also great for recommendation and fraud detection.
* Amazon Quantum Ledger Database is an immutable system of record. Any entry can never be removed from the audits. 
* Database accelerators such as adding caching layers can be provided with Amazon ElastiCache. 
* Amazon DynamoDB Accelerator (DAX) accelerates DynamoDB.
* Amazon Managed Blockchain is used to create and manage blockchain networks with open-source frameworks. It is a distributed ledger system that lets multiple parties run transactions and share data without a central authority.

## Module 6 - Security

### Introduction
* With the shared responsibility model, AWS manages security **OF** the cloud. The customer is responsible for security **IN** the cloud.

### AWS Shared Responsibility Model
* Customer responsibility starts at the operating system. Only the user has the encryption key to log into to the operating system as the root user.
  * The customers team must keep the OS patched. AWS cannot deploy a patch.
  * On top of the OS, the user can run any applications and use any data. It is up to the user to secure these endpoints. 
    * AWS provides the tools to encrypt and secure this content, the user must employ it.
  

### User Permissions and Access
* When you create an AWS account, you are the root user. They have permission to do anything they want inside of the account. 
  * AWS recommends MFA (Multi Factor Authenication) to login. 
  * AWS Identity and Access Management (IAM) allows you to create IAM users which by default have no permissions. 
    * You have to explicitly give the user permission to do anything. 
      * This idea is called the principle of least privilege. You only give the user the minimum of what they need.
* An IAM policy is a JSON document that describes what API calls a user can or cannot make. 
  * It contains a version, and a statement containing `Effect` which allows or restricts a user from a service, an `Action` which is a specific command to be performed, and a `Resource` which is a unique identifier for a specific service.
    * Effect is either allow or deny. 
    * Action is any API call.
    * Resource is what specific AWS resource that API call is for.
  * You can organize users into IAM groups and attach a policy to a group. All users will have those permissions.
  * A role is an identity that can be assigned to a user for a temporary period of time.
    * No username or password. Can be assigned to AWS resources, users, external identities, and applications.
    * When someone assumes an IAM role, they abandon all previous permissions that they had under a previous role and assume the permissions of the new rule. 
* You can map corporate identities to IAM roles. This allows users to login with their coporate information. 






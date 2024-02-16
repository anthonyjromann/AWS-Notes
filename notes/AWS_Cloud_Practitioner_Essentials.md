---
title: AWS Cloud Practitioner Essentials
created: '2024-02-15T22:39:37.666Z'
modified: '2024-02-16T02:58:23.959Z'
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



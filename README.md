# AWS Certified Cloud Practitioner

This is a demo repository for the AWS Certified Cloud Practitioner course.

# AWS Certified Cloud Practitioner

## Table of Contents
1. [Types of Cloud Computing](#types-of-cloud-computing)
   - [Service Models](#service-models)
   - [Deployment Models](#deployment-models)
2. [IAM Permissions](#iam-permissions)
   - [Key Concepts](#key-concepts)
   - [Types of IAM Permissions](#types-of-iam-permissions)
   - [Best Practices](#best-practices)
3. [Amazon EC2: Deep Summary](#amazon-ec2-deep-summary)
   - [Key Features](#key-features)
   - [Common Use Cases](#common-use-cases)
   - [Management Tools](#management-tools)
4. [EC2 Storage Summary](#ec2-storage-summary)
   - [Instance Store](#1-instance-store-ephemeral-storage)
   - [Amazon EBS](#2-amazon-elastic-block-store-ebs)
   - [Amazon EFS](#3-amazon-elastic-file-system-efs)
   - [Amazon FSx](#4-amazon-fsx)
   - [Amazon S3](#5-amazon-s3-object-storage)
5. [AWS Vertical and Horizontal Scalability](#aws-vertical-and-horizontal-scalability)
   - [Vertical Scalability](#vertical-scalability-scaling-up)
   - [Horizontal Scalability](#horizontal-scalability-scaling-out)
6. [ELB and ASG Summary](#elb-elastic-load-balancer-and-asg-auto-scaling-group-summary)
   - [Elastic Load Balancer](#elastic-load-balancer-elb)
   - [Auto Scaling Group](#auto-scaling-group-asg)

This is a demo repository for the AWS Certified Cloud Practitioner course.

# Types of Cloud Computing

Cloud computing is broadly categorized into three types based on service models and four types based on deployment models. Here's an overview:

---

## **Service Models**

1. **Infrastructure as a Service (IaaS):**
   - Provides virtualized computing resources over the internet.
   - Includes services like virtual machines, storage, and networks.
   - Allows users to manage and control the infrastructure.
   - **Examples:** AWS EC2, Microsoft Azure Virtual Machines, Google Compute Engine.

2. **Platform as a Service (PaaS):**
   - Offers a platform and environment for developers to build, deploy, and manage applications without worrying about infrastructure.
   - Provides tools and frameworks for development.
   - **Examples:** Heroku, Google App Engine, Microsoft Azure App Service.

3. **Software as a Service (SaaS):**
   - Delivers software applications over the internet on a subscription basis.
   - Managed entirely by the provider, including maintenance and updates.
   - **Examples:** Google Workspace (Docs, Sheets, Gmail), Microsoft 365, Salesforce.

4. **Function as a Service (FaaS):**
   - Often categorized under serverless computing.
   - Allows developers to run specific functions or pieces of code without managing servers.
   - **Examples:** AWS Lambda, Azure Functions, Google Cloud Functions.

---

## **Deployment Models**

1. **Public Cloud:**
   - Resources are owned and operated by a third-party cloud service provider and delivered over the internet.
   - Shared infrastructure is used by multiple organizations or customers.
   - **Examples:** AWS, Google Cloud, Microsoft Azure.

2. **Private Cloud:**
   - Resources are used exclusively by a single organization.
   - Provides greater control and customization.
   - Can be hosted on-premises or by a third-party provider.
   - **Examples:** VMware, OpenStack-based private clouds.

3. **Hybrid Cloud:**
   - Combines public and private clouds, allowing data and applications to be shared between them.
   - Offers flexibility and optimizes existing infrastructure.
   - **Example Use Case:** Sensitive workloads on a private cloud and general-purpose workloads on a public cloud.

4. **Community Cloud:**
   - Shared infrastructure for specific organizations with similar goals, policies, or compliance requirements.
   - Typically managed collectively or by a third party.
   - **Example Use Case:** Government agencies with shared compliance needs.

---

These types can be tailored to meet specific business requirements, offering varying levels of control, flexibility, and cost-effectiveness.


# IAM Permissions

**IAM (Identity and Access Management)** permissions define the actions and resources a user, group, or role can access in a cloud environment. These permissions ensure secure and granular control over resources.

---

## **Key Concepts**

1. **Principals:**
   - Entities (users, groups, roles, or services) that perform actions on resources.
   - Examples:
     - **AWS:** IAM users, groups, roles.
     - **Azure:** Users, service principals, managed identities.
     - **GCP:** Google accounts, service accounts.

2. **Policies:**
   - Documents that define permissions by specifying actions, resources, and conditions.
   - Types:
     - **Allow policies**: Explicitly grant access.
     - **Deny policies**: Explicitly restrict access (overrides allow policies).

3. **Actions:**
   - Operations a principal can perform (e.g., `ec2:StartInstances` in AWS, `storage.buckets.create` in GCP).

4. **Resources:**
   - Cloud objects or entities to which permissions apply, such as VMs, storage buckets, or databases.

5. **Conditions:**
   - Optional criteria that must be met for permissions to apply (e.g., time of access, IP ranges).

---

## **Types of IAM Permissions**

### 1. **User Permissions**
   - Permissions assigned directly to individual users.
   - Best for specific, unique access requirements.

### 2. **Group Permissions**
   - Permissions applied to a group of users.
   - Easier to manage access for teams.

### 3. **Role Permissions**
   - Permissions assigned to roles that can be assumed temporarily.
   - Commonly used for cross-account access and service permissions.

### 4. **Service Account Permissions**
   - Permissions granted to applications or services.
   - Enable secure communication and operations between services.

---

## **Best Practices**

1. **Principle of Least Privilege:**
   - Grant only the permissions necessary to perform a task.

2. **Use Groups and Roles:**
   - Avoid assigning permissions directly to individual users; use groups or roles instead.

3. **Regular Auditing:**
   - Periodically review and update permissions to maintain security.

4. **Conditions for Specificity:**
   - Use conditions to narrow down the scope of access (e.g., restrict access to specific IPs or times).

5. **Enable Multi-Factor Authentication (MFA):**
   - Add an extra layer of security for sensitive permissions.

---

## **IAM Across Cloud Providers**

### **AWS IAM:**
   - Permissions are defined in JSON policy documents.
   - Managed, inline, and customer-managed policies are supported.
   - Examples:
     - `s3:PutObject`
     - `ec2:DescribeInstances`


---

IAM permissions play a vital role in securing cloud environments by controlling who can access and perform actions on resources.


# Amazon EC2: Deep Summary

Amazon Elastic Compute Cloud (EC2) is a core AWS service that provides scalable and resizable compute capacity in the cloud. It enables developers to run virtual servers, known as instances, with various configurations.

---

## **Key Features**
### 1. Instances
- Virtual servers with customizable CPU, memory, storage, and networking.
- Instance types categorized into families:
  - **General Purpose**: Balanced performance (e.g., `t2`, `m6`).
  - **Compute Optimized**: High CPU workloads (e.g., `c5`).
  - **Memory Optimized**: Large memory requirements (e.g., `r5`).
  - **Storage Optimized**: High I/O performance (e.g., `i3`).
  - **Accelerated Computing**: GPUs or FPGAs (e.g., `p3`, `g4`).

### 2. Elasticity
- Scale resources up or down based on demand.
- Integration with **Auto Scaling** for automatic capacity adjustments.

### 3. Storage
- **EBS (Elastic Block Store)**: Persistent, block-level storage.
- **Instance Store**: Temporary storage tied to the instance lifecycle.
- **S3**: Object storage for backup and archiving.

### 4. Networking
- **VPC Integration**: Isolated, secure networks.
- **Elastic IPs**: Static public IP addresses.
- Support for high-performance networking and multiple network interfaces.

### 5. Flexible Pricing
- **On-Demand Instances**: Pay-as-you-go.
- **Reserved Instances**: Lower cost with long-term commitments (1–3 years).
- **Spot Instances**: Use spare capacity at a lower price.
- **Savings Plans**: Commit to usage for cost savings.
- **Dedicated Hosts**: Physical servers for regulatory compliance.

### 6. Security
- **Security Groups**: Virtual firewalls to control traffic.
- **IAM Integration**: Role-based access control.
- Encryption for data at rest (EBS, S3) and in transit.
- **AWS KMS**: Manage encryption keys securely.

### 7. Customizability
- Wide selection of operating systems (Linux, Windows, etc.).
- **User Data Scripts**: Automate initialization tasks.

---

## **Common Use Cases**
- **Web Hosting**: Host dynamic websites and applications.
- **Big Data**: Process large-scale datasets with tools like Hadoop.
- **High-Performance Computing (HPC)**: Solve complex computational problems.
- **Dev/Test Environments**: Quickly build and test applications.
- **Disaster Recovery**: Serve as a failover option for on-premises systems.

---

## **Management Tools**
1. **AWS Management Console**: Web-based GUI for managing resources.
2. **AWS CLI & SDKs**: Automate and manage EC2 programmatically.
3. **Amazon CloudWatch**: Monitor metrics and set alarms.
4. **AWS Systems Manager**: Manage and automate tasks at scale.

---

## **Benefits**
- **Scalability**: Quickly add or remove resources based on demand.
- **Flexibility**: Choose from a wide range of configurations.
- **Cost-Effectiveness**: Multiple pricing models to suit workloads.
- **Global Reach**: Available in multiple regions and Availability Zones (AZs).

---

## **Challenges and Considerations**
- **Cost Management**: Avoid unused resources and overprovisioning.
- **Security**: Properly configure IAM roles, security groups, and VPCs.
- **Monitoring**: Ensure adequate logging and performance tracking.

---

## **Advanced Capabilities**
1. **Elastic GPUs**: Add GPU power to instances for graphics-heavy workloads.
2. **Nitro System**: AWS hypervisor for better performance and security.
3. **Placement Groups**:
   - **Clustered**: For low-latency, high-throughput workloads.
   - **Spread**: Distribute instances for fault tolerance.
   - **Partitioned**: For large-scale distributed systems.
4. **Elastic Load Balancing**: Distribute traffic across instances.

---

EC2 provides a powerful, flexible, and cost-effective compute platform suitable for a wide range of workloads, from small-scale web apps to enterprise-grade systems.

# EC2 Storage Summary

## 1. Instance Store (Ephemeral Storage)
- **Description**: Temporary block-level storage physically attached to the host. Data is lost when the instance stops, terminates, or fails.
- **Use Case**: High-performance temporary storage, e.g., for caching, scratch data, or temporary processing.
- **Key Features**:  
  - Extremely low latency.  
  - Available at no additional cost (included in instance price).  
  - Non-persistent: Data does not survive instance stops or terminations.  

---

## 2. Amazon Elastic Block Store (EBS)
- **Description**: Persistent block storage for EC2 instances. Data persists independently of the instance lifecycle.  
- **Types**:  
  - **General Purpose SSD (gp3/gp2)**: Balanced price/performance for general workloads.  
  - **Provisioned IOPS SSD (io2/io1)**: High performance and durability for latency-sensitive, I/O-intensive applications.  
  - **Throughput Optimized HDD (st1)**: Low-cost storage for frequently accessed, throughput-intensive workloads like big data.  
  - **Cold HDD (sc1)**: Lowest-cost storage for infrequently accessed data.  

- **Use Case**: Boot volumes, databases, file systems, backup and disaster recovery.  
- **Key Features**:  
  - Snapshots for backup and disaster recovery (stored in Amazon S3).  
  - Encryption at rest and in transit.  
  - Easily scalable: Resize volumes or change types without downtime (Elastic Volumes).  
  - Durability: Replicated across multiple AZs within the region.  

---

## 3. Amazon Elastic File System (EFS)
- **Description**: Fully managed, scalable, shared file storage for Linux-based workloads. Accessible across multiple instances.  
- **Use Case**: Content management, web serving, application workloads requiring shared access.  
- **Key Features**:  
  - Elastic scaling: Automatically grows/shrinks as you add/remove data.  
  - Two storage classes:  
    - Standard (frequent access).  
    - Infrequent Access (lower cost).  
  - Supports NFS protocol (Network File System).  
  - Encryption and lifecycle policies for data tiering.  

---

## 4. Amazon FSx
- **Description**: Fully managed file storage for specific workloads.  
- **Types**:  
  - **FSx for Windows File Server**: Supports SMB protocol, Active Directory integration.  
  - **FSx for Lustre**: High-performance file system for compute-intensive workloads (e.g., HPC, machine learning).  
  - **FSx for NetApp ONTAP**: Enterprise-grade features like data replication, snapshots, and caching.  

- **Use Case**: Enterprise applications, machine learning, HPC, analytics, and content collaboration.  
- **Key Features**:  
  - Fully managed with high availability.  
  - Integration with EC2, S3, and on-premises systems.  

---

## 5. Amazon S3 (Object Storage)
- **Description**: Scalable object storage for storing and retrieving any amount of data, anywhere. Ideal for unstructured data.  
- **Use Case**: Backup, archiving, big data analytics, data lakes, and content delivery.  
- **Key Features**:  
  - 99.999999999% durability (11 9’s).  
  - Multiple storage classes for different use cases:  
    - Standard, Intelligent-Tiering, Glacier, and Glacier Deep Archive.  
  - Encryption and access control (IAM policies, bucket policies).  
  - Designed for high availability and fault tolerance.  

---

## 6. AWS Storage Gateway
- **Description**: Hybrid storage service for integrating on-premises applications with AWS storage.  
- **Types**:  
  - File Gateway.  
  - Volume Gateway.  
  - Tape Gateway.  

- **Use Case**: Backup and disaster recovery, hybrid cloud storage, and tiering inactive data to AWS.  
- **Key Features**:  
  - Seamless integration with S3, Glacier, and EBS.  
  - Optimized data transfer.  

---

## 7. Local NVMe Storage
- **Description**: High-speed, directly attached storage available on certain instance types (e.g., i3, i4, c5d).  
- **Use Case**: Real-time data processing, high-performance applications requiring very low latency.  
- **Key Features**:  
  - Extremely low latency and high IOPS.  
  - Not persistent: Data is lost when the instance stops.  

---

## 8. AWS Backup
- **Description**: Centralized backup service for automating backup across multiple AWS resources (EBS, EFS, S3, etc.).  
- **Use Case**: Compliance, centralized backup management, disaster recovery.  
- **Key Features**:  
  - Centralized dashboard for backup management.  
  - Supports backup policies, lifecycle management, and encryption.  

---

## Choosing the Right Storage
- **Short-lived, high-speed processing**: Instance Store, Local NVMe.  
- **Persistent block storage**: EBS (gp3/gp2 for general, io2/io1 for high IOPS).  
- **Shared file storage**: EFS or FSx.  
- **Object storage**: S3 for scalable, cost-effective unstructured data.  
- **Hybrid environments**: AWS Storage Gateway.  


# AWS Vertical and Horizontal Scalability

## **Vertical Scalability (Scaling Up)**  
Vertical scalability refers to increasing the capacity of a single instance by upgrading its resources, such as CPU, RAM, or storage. This is akin to making a machine more powerful to handle a larger workload.

In AWS, vertical scaling is achieved by switching to a larger instance type within the same instance family. For example:  
- Upgrading from a `t3.micro` instance to a `t3.large` instance.  
- Increasing the storage size of an EBS volume attached to the instance.  

### **Advantages**  
- Simple to implement since it involves modifying the existing instance.  
- Requires no architectural changes to the application.  

### **Limitations**  
- There are physical hardware limits (e.g., the maximum size of an instance type).  
- Downtime may be required while resizing the instance.  

---

## **Horizontal Scalability (Scaling Out)**  
Horizontal scalability involves adding more instances to distribute the workload across multiple machines. This approach focuses on handling increased demand by scaling the system outward rather than relying on a single, powerful instance.

In AWS, horizontal scaling is often implemented using services like **Auto Scaling Groups (ASGs)** and **Elastic Load Balancers (ELBs)**:  
- **Auto Scaling Groups** automatically launch or terminate instances based on traffic and load.  
- **Elastic Load Balancers** distribute incoming requests across multiple instances.  

### **Advantages**  
- Virtually unlimited scaling potential by adding more instances.  
- Better fault tolerance and availability since the load is distributed across multiple machines.  

### **Limitations**  
- Requires applications to be designed for distributed systems (e.g., stateless services).  
- More complex to implement and manage compared to vertical scaling.  

---

## **Comparison**

| Feature                  | Vertical Scalability                | Horizontal Scalability             |
|--------------------------|-------------------------------------|------------------------------------|
| **Approach**             | Upgrade a single instance's resources | Add more instances to distribute load |
| **AWS Services**         | Larger EC2 instance types, EBS resizing | Auto Scaling Groups, Load Balancers |
| **Simplicity**           | Easier to implement                | Requires architectural planning   |
| **Fault Tolerance**      | Limited (single point of failure)  | High (load distributed)           |
| **Scalability Limit**    | Limited by hardware                | Virtually unlimited               |
| **Downtime**             | Possible during upgrades           | Minimal to none                   |

---

Both vertical and horizontal scaling can be used together in AWS to create highly scalable, reliable, and efficient applications.

# ELB (Elastic Load Balancer) and ASG (Auto Scaling Group) Summary

## **Elastic Load Balancer (ELB)**
ELB is a fully managed load-balancing service by AWS designed to distribute incoming application or network traffic across multiple targets, such as EC2 instances, containers, and IP addresses. It improves application fault tolerance and scalability.

### **Key Features**
1. **Types of Load Balancers:**
   - **Application Load Balancer (ALB):** Operates at the application layer (Layer 7) and is ideal for HTTP/HTTPS traffic. It supports host-based and path-based routing.
   - **Network Load Balancer (NLB):** Operates at the transport layer (Layer 4) for TCP/UDP traffic and provides ultra-low latency.
   - **Gateway Load Balancer (GWLB):** Used for deploying and scaling third-party virtual appliances like firewalls and intrusion detection systems.

2. **High Availability:** Distributes traffic across multiple targets in one or more Availability Zones.
3. **Health Checks:** Continuously monitors target health and stops sending traffic to unhealthy targets.
4. **SSL/TLS Termination:** Offloads SSL/TLS decryption to reduce compute load on targets.
5. **Auto Scaling Integration:** Works seamlessly with ASG to dynamically scale the target capacity.
6. **Sticky Sessions:** Supports session persistence to direct requests from a user to the same target.
7. **WebSocket Support:** Maintains long-lived connections for real-time applications.
8. **Cross-Zone Load Balancing:** Distributes traffic evenly across registered targets in all enabled Availability Zones.

---

## **Auto Scaling Group (ASG)**
ASG is a service designed to maintain application availability and automatically adjust EC2 instance capacity to meet changing demand. It ensures that the desired number of instances are running at all times.

### **Key Features**
1. **Scaling Policies:**
   - **Dynamic Scaling:** Automatically adjusts capacity based on CloudWatch metrics (e.g., CPU utilization).
   - **Scheduled Scaling:** Scales capacity based on a pre-defined schedule.
   - **Predictive Scaling:** Uses machine learning to predict traffic patterns and scale in advance.

2. **High Availability:**
   - Distributes instances across multiple Availability Zones for fault tolerance.
   - Automatically replaces unhealthy instances with healthy ones.

3. **Integration with ELB:**
   - Ensures new instances are automatically registered with an ELB and start receiving traffic once healthy.

4. **Health Checks:**
   - Performs periodic instance health checks (EC2 and ELB health).
   - Automatically terminates and replaces unhealthy instances.

5. **Launch Configurations/Launch Templates:**
   - Define EC2 instance settings such as AMI ID, instance type, key pairs, security groups, and user data.

6. **Scaling Strategies:**
   - **Target Tracking Scaling:** Adjusts capacity to maintain a target metric (e.g., 50% CPU utilization).
   - **Step Scaling:** Scales incrementally based on a range of metrics.
   - **Simple Scaling:** Scales up/down based on a single threshold metric.

7. **Cost Optimization:**
   - Right-sizes resources by scaling down during low demand and scaling up during peak demand.
   - Supports mixed instance types and purchase options (On-Demand, Spot Instances).

---

## **ELB and ASG Integration**
The combination of ELB and ASG allows for a robust, fault-tolerant, and highly available application architecture:

1. **Traffic Distribution:** ELB evenly distributes traffic across ASG instances.
2. **Dynamic Scaling:** ASG automatically adjusts the number of instances based on traffic and workload demands.
3. **Fault Tolerance:** ELB stops routing traffic to unhealthy instances, while ASG replaces unhealthy instances automatically.
4. **Seamless Updates:** ASG integrates with ELB during instance launches and terminations, ensuring a smooth user experience without downtime.

---

## **Best Practices**
1. Enable **Cross-Zone Load Balancing** in ELB for even traffic distribution.
2. Configure **Lifecycle Hooks** in ASG to perform initialization tasks before instances are marked healthy.
3. Use **Target Tracking Policies** in ASG for efficient scaling.
4. Regularly monitor ELB and ASG metrics via **CloudWatch** to ensure optimal performance.
5. Design your architecture across multiple **Availability Zones** for resilience.

---


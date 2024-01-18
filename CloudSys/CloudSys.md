## Objectifs d'apprentissage, compétences à acquérir

Concepts, principles and architectures of **IaaS**, **PaaS** and **FaaS** services, as well as deployment and implementation
environments.
Able to use and choose the appropriate **IaaS**, **PaaS** and **FaaS** Cloud environments
Understand the APIs allowing access to IaaS and PaaS services.
Choose appropriate measures to **secure** a Cloud.
Be able to design **"cloud-native" services and applications**.
Characteristics of the cloud: **on-demand resources, elasticity, multi-user, metered services, broadband network access**.
Be able to evaluate the economic, legal and technological advantages/limits of the cloud as well as its intrinsic limitations.

## Lecture's Content

Definition, principles, services and deployment models (1 session)
Comparative study of different infrastructure services (IaaS), including storage (2 sessions)
Comparative study of container technologies: Docker, SWARM, Kubernetes (2 sessions)
Edge-Cloud technology (1 session)
Cloud-based Function-as-a-Service, Serverless Computing (1 session)
Network Resource Virtualization (1 session)
Security for Cloud (1 session)
Platform-as-a-Service (2 sessions)
Continuous Delivery and Deployment in a Cloud environment (1 session)
Persistence services and Database-as-a-Service (1 session)
Cloud-Native applications (1 session)

---

# CloudSys Lecture Summary

## 1. Introduction to Cloud Computing

### Definition and Principles

Cloud computing is a style of computing where massively scalable IT-related capabilities are provided as a service using internet technologies. This includes on-demand access to computing resources like applications, servers (both physical and virtual), data storage, development tools, networking capabilities, and more, which are hosted at remote data centers managed by cloud service providers (CSPs). CSPs make these resources available for a monthly subscription fee or bill them according to usage​​.

### Services and Deployment Models

Software as a Service (SaaS): Delivers software applications over the internet, on demand and typically on a subscription basis.
Platform as a Service (PaaS): Provides a platform allowing customers to develop, run, and manage applications without the complexity of building and maintaining the infrastructure.
Infrastructure as a Service (IaaS): Offers essential computing, storage, and networking resources on demand, over the internet, and on a pay-as-you-go basis.
Function as a Service (FaaS): Also known as Server-less Computing, FaaS allows building and running applications and services without managing servers. It involves a high level of abstraction and is event-driven, starting the function when needed and shutting it down afterwards. Providers include AWS Lambda, Azure Functions, Cloud Functions, Manta, etc​​.

## 2. Infrastructure as a Service (IaaS)

### Comparative study of different IaaS

Amazon Web Services (AWS): Introduced in 2006/2007, AWS is a collection of remote infrastructure services, initially offering services in the IaaS category, but now also includes PaaS and SaaS categories. AWS's IaaS services primarily include compute, storage, database, and networking services, targeted towards operations engineers and developers​​.
Amazon Elastic Compute Cloud (EC2): A web service providing resizable compute capacity in the cloud, allowing developers to rent virtual machines (EC2 instances) with many instance types available​​.
Amazon Simple Storage Service (S3): A high-performance, highly-available, web-oriented storage service supporting very large files, allowing for unlimited storage of objects (files) ranging from 1 byte to 5 TB​​.
OpenStack Storage Services: Includes Cinder (block storage component analogous to traditional disk drive access) and Swift (storage system for objects and files)​​.

### Storage systems

Block Storage: Amazon Elastic Block Store (EBS) provides persistent storage for EC2 instances, offering off-instance storage that persists independently from the lifecycle of an instance. EBS allows for the creation of point-in-time consistent snapshots of volumes, which are stored in S3 and replicated across multiple available zones. These snapshots can be used as the starting point for new EBS volumes, to protect data for long-term durability, and to be easily shared​​.
Solid State Drive & File System: Not specifically covered in the provided lecture materials.
Virtual Storage: AWS provides virtual disks that can be attached to virtual machines, including EBS Volumes (managed by the storage service, lifecycle independent of virtual machine) and Instance Store Volumes (allocated on the same server that hosts the virtual machine, deallocated when the virtual machine is deallocated, and rarely used nowadays)​​.
Snapshot: EBS snapshots provide point-in-time, consistent backups of volumes, stored in S3 and replicated across multiple available zones for durability and accessibility​​.
Logical Volume Manager: Not specifically covered in the provided lecture materials.

## 3. Platform as a Service (PaaS)

- Understanding PaaS architectures
- APIs for accessing PaaS services

## 4. Function as a Service (FaaS) and Serverless Computing

- Principles and use cases
- Serverless data processing: Parameters, Pricing, Execution environment lifecycle, Object lambdas

## 5. Container Technologies

- Comparative study: Docker, SWARM, Kubernetes
- Benefits and use cases

## 6. Edge-Cloud Technology

- Overview and applications

## 7. Network Resource Virtualization

- Concepts and technologies

## 8. Security for Cloud

- Measures and strategies for cloud security

## 9. Continuous Delivery and Deployment

- Techniques and tools in a Cloud environment

## 10. Persistence Services and Database-as-a-Service

- Overview and comparison

## 11. Cloud-Native Applications

- Designing "cloud-native" services and applications
- Characteristics: On-demand resources, Elasticity, Multi-user, Metered services, Broadband network access

## 12. The Twelve Factors

- Summary of the 12 factors (from your notes):
  - Codebase
  - Dependencies
  - Config
  - Backing Services
  - Build-Release-Run
  - Processes
  - Port Binding
  - Concurrency
  - Disposability
  - Dev/Prod Parity
  - Logs
  - Admin Processes

## 13. Economic, Legal, and Technological Aspects

- Evaluating advantages and limitations of cloud computing

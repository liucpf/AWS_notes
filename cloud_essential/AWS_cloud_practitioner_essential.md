# AWS Cloud Practitioner Essentials

## Module 1: intro to amazon web services
client-server model and pay-as-you-go pricing model

Cloud computing
- The on-demand delivery of IT resources over the internet with pay-as-you-go pricing

Three cloud computing deployment models:
- Cloud based deployment
    - run all parts of the application in the cloud
    - migrate existing application to the cloud
    - design and build new applications in the cloud
- on-premises deployment
    - deploy resources by using virtualization and resource management tools
    - increase resource utilization by using application management and virtualization technologies
- hybrid deployment
    - connect cloud-based resources to on-premises infrastructure
    - integrate cloud-based resources with legacy IT applications

Benefits of cloud computing
- trade upfront expense for variable expense
- stop spending money to run and maintain data centers
- stop guessing capacity
- benefit from massive economies of scale
- increase speed and agility
- go global in minutes

## Module 2 Compute on the cloud

### Summary
- Amazon EC2 instance types and pricing options
- Amazon EC2 Auto Scaling
- Elastic Load Balancing
- AWS services for messaging, containers, and serverless computing

### On premises vs Amazon EC2
on-premises resources
- spend money upfront to purchase hardware
- wait for the servers to be delivered to you
- install the servers in your physical data center
- make all the necessary configurations

Amazon EC2
- you can provision and launch an EC2 instance within minutes
- you can stop using it when you finished running a workload
- you pay only for the compute time you use when an instance is running, not when it is stopped or terminated
- you can save costs by paying only for server capacity that you need or want


### EC2 instances types

- General purpose instances
    - application servers
    - gaming servers
    - backend servers for enterprise applications
    - small and medium databases

- Compute optimized instances
    - high-performance web servers
    - compute-intensive applications servers
    - dedicated gaming servers
    - batch processing workloads that require processing many transactions in a single group

- Memory optimizied instances
    - high-performance database
    - a workload performing real-time processing of a large amount of unstructured data

- Accelerated computing instances
    - floating-point calculations, graphics procesing, data pattern matching
    - graphics applications, game streaming, and application streaming

- Storage optimized instances
    - distributed file systems
    - data warehousing applications
    - high-frequency online transaction processing (OLTP) systems
    - low-latency random input/output operations per second (IOPS)

### EC2 pricing
- on-demand
- reserved instances
    - standard reserved instance
    - convertible reserved instances
- EC2 instance savings plans
- spot instances
- dedicated hosts

### Amazon EC2 Auto Scaling
- dynamic scaling: changing on demand
- predictive scaling: automatically schedules the right number of instances based on predicted demand

auto scaling group
- minimum capacity
- desired capacity
- maximum capacity

Elastic load balancing
- automatically distributes incoming application traffic across multiple resources

### Messaging and queueing
Monolithic applications
- an application with tightly coupled components, which might include databases, servers, the user interface, business logic, etc.
- if a single component fails, other will fail

microservice approach
- application components are loosely coupled. different components communicating with each other
- two service facilitate application integration
    - Amazon Simple Notification Service (Amazon SNS)
    - Amazon Simple Queue Service (Amazon SQS)

Amazon SNS
- publish/subscribe service
- a publisher publishes messages to subscribers
- subscribers can be web servers, email addresses, AWS Lambda functions, etc.

Amazon SQS
- message queuing service
- an app sends messages into a queue, and a user or service retrieves a message from the queue, processes it, and then deletes it from the queue

### Serverless 
AWS Lambda (15min)
- no need to provision or manage servers
- process
    - upload code to lambda
    - set code to trigger from an event source
    - code runs only when triggered
    - pay only for the compute time you use

Containerized applications
- containers provide you with a standard way to package your applications's code and dependencies into a single object
- services
    - Amazon Elastic Container Service (Amazon ECS)
        - supports Docker
    - Amazon Kubernetes Service (Amazon EKS)
        - Kubernetes is open-source software that enbales you to deploy and manage containerized applications at scale.
    - AWS Fargate
        - a serverless compute engine for containers
        - it works with both Amazon ECS and EKS

## Module 3 Global infrastructure and reliability

### Summary
- AWS regions and availability zones
- edge locations and amazon cloudfront
- AWS management console, AWS CLI and SDK
- AWS Elastic Beanstalk
- AWS CloudFormation

### AWS regions
- compliance with data governance and legal requirements
- proximity to your customers
- available services within a region
- pricing

### Availability Zones
- a single data center or a group of data centers within a region
- located tens of miles apart from each
- a region consists of three or more availability zones

### Content delivery networks
- AWS cloudfront
    - a content delivery service
    - using a network of edge locations to cache content
- Amazon Route 53
- Edge locations
    - a site that Amazon CloudFront uses to store cached copies of your content closer to your customers for faster delivery
- AWS outposts
    - set a server next to your building
    - run infrastructure in a hybrid cloud approach

### AWS APIs
- AWS management console
- AWS command line interface (CLI)
- AWS software development kits (SDK)

### AWS elastic Beanstalk
- with code and configuration settings, and Elastic Beanstalk deploys the resources necessary to perform:
    - adjust capacity
    - load balancing
    - automatic scaling
    - application health monitoring

### AWS cloudformation
- build an environment by writing lines of code
- provision resources in a safe, repeatable manner, enabling you to frequently build your infrastructure and applications without having to perform manual actions
- manage your stack and rolls back changes automatically if detecting errors

## Module 4 Networking

### Amazon virtual private cloud (VPC)
- subnet: a section of VPC that you can group resources based on security or operational needs
- public subnet
    - have access to the internet gateway
- private subnet
    - should be accessible only through your private network

### internet gateway
- a connection between a VPC and the internet
- virtual private gateway
    - allows protected internet traffic to enter into the VPC

### AWS direct connect
- reduce network costs
- increase the amount of bandwidth

### Network access control list (ACL)
- a virtual firewall that controls inbound and outbound traffic at the subnet level
    - who send the packet
    - how the packet is trying to communicate with the resources
- each AWS account includes a default network ACL
- default network ACL
    - allows all inbound and outbound traffic
- custom network ACL
    - all inbound and outbound traffic is denied until you add rules to specify which traffic to allow
- all network ACL have an explicit deny rule
    - if a packet does not match any of the other rules on the list, the packet is denied
- perform stateless packet filtering

### security group
- a virutal firewall that controls inbound and outbound traffic for an EC2 instance
- default
    - denies all inbound traffic and allow all outbound traffic
- custom
    - when customizing which traffic would be allowed, any other traffic would then be denied
- different EC2 instances within the same VPC can be associated with the same or different security groups
- perform stateful packet filtering
    - when a packet response for that request returns to the instance, the security group remembers your previous request

### Global networking
- Amazon Route 53
    - a domain name system (DNS) web service
    - new domain name can be directed registered in Route 53
    - existing domain names can also be transferred
- Amazon cloudfront
    - content delivery network (CDN)

## Module 5 storage and databases

### summary
- Amazon EC2 instance store and Amazon EBS
- Amazon S3
- Amazon EFS
- Relational databases and Amazon RDS
- nonrelational databases and DynamoDB
- Amazon Redshift
- AWS DMS
- Additional database services and accelerators

instance store volumes
- temporary block level storage for EC2
- physically attached to the host computer for an EC2 instance
- has the same lifespan as the instance

### Amazon elastic block store (EBS)
- need to define configuration (volume size and type)
- backups by creating EBS snapshots
- incremental backups is only about chained volume
- full backup includes data that has not changed since the most recent backup

### Amazon simple storage service (S3)
- store and retrieve an unlimited amount of data
- store data as objects
    - each object consists of data, metadata and a key
- store objects in buckets
- upload a maximum object size of 5TB
- version objects
- create multiple buckets
- when a file in block storage is modified, only the pieces that are changed are updated
- when a file in object storage is modified, the entire object is updated

Amazon S3 storage classes
- S3 standard
    - designed for frequently accessed data
    - stores data in a minimum of three availability zones
    - has a higher cost than other storage classes intended for infrequently accessed data and archival storage
- S3 standard-infrequent access (S3 standard-IA)
    - ideal for infrequently accessed data, but requires high availability when needed
    - same level of availability to S3 standard but has a lower storage price and higher retrieval price
    - stores data in a minimum of three availability zones
- S3 one zone-infrequent access (S3 One-Zone-IA)
    - stores data in a single availability zone
    - has a lower storage price than S3 standard-IA
    - when to use
        - you want to save costs on storage
        - you can easily reproduce your data in the event of an availability zone failure
- S3 intelligent-Tiering
    - ideal for data with unknown or changing access patterns
    - requires a small monly monitoring and automation fee per object
    - if an object has not been accessed for 30 consecutive days, S3 automatically moves it to the infrequent access tier S3 standard-IA
    - if you access an object in the infrequent access tier, S3 automatically moves it to the frequent access tier S3 standard
- S3 Glacier instant retrieval
    - works well for archived data that requires immediate access
    - can retrieve objects within a few milliseconds
- S3 Glacier flexible retrieval
    - low cost storage designed for data archiving
    - able to retrieve objects within a few minutes to hours
- S3 Glacier deep archive
    - lowest-cost object storage class ideal for archiving
    - able to retrieve objects within 12 hours
    - all objects from this storage class are replicated and stored cross at least three geographically dispersed availability zones
- S3 outposts
    - creates S3 buckets on S3 outposts
    - makes it easier to retrieve, store, and access data on AWS outposts
- two factors to consider when selecting a S3 storage class
    - how often you plan to retrieve your data
    - how available you need your data to be
 
EBS vs S3
- EBS
    - sizes up to 16 TiB
    - survive terminations of their EC2 instance
    - solid state by default
    - HDD options
    - block storage
- S3
    - unlimited storage
    - regionally distributed
    - individual objects up to 5TBs
    - write one/read many
    - 99.99% durability
    - object stroage

### Amazon Elastic File System (EFS)
EBS vs EFS
- EBS
    - volumes attach to EC2 instances
    - availability Zone level resource
    - need to be in the same AZ to attach EC2 instances
    - Volumes do not automatically scale
- EFS
    - multiple instances reading and writing simultaneously
    - linux file system
    - regional resource
    - automatically scales (on demand to petabytes)
    - on-premises servers can access Amazon EFS using AWS direct connect

file storage
- multiple clients can access data that is stored in shared file folders
- a storage server uses block storage with a local file system to organize files
- ideal for use cases in which a large number of services and resources need to access the same data at the same time

### Amazon relational database service (RDS)
Amazon RDS
- a service that enables you to run relational databases in the AWS cloud
- features
    - Automated patching
    - backups
    - redundancy
    - failover
    - disaster recovery
    - encryption at rest (protecting data while it is stored)
    - encryption in transit (protecting data while it is being sent and received)
- database engines
    - Amazon Aurora
    - PostgreSQL
    - MySQL
    - MariaDB
    - Oracle Database
    - Microsoft SQL Server

Amazon Aurora
- enterprise-class relational database
- compatible with MySQL and PostgreSQL
- 1/10th the cost of commercial databases
- Data replication
- up to 15 read replicas
- replicates six copies across three AZ
- continuous backup to S3
- point-in-time recovery

### non-relational database
Amazon DynamoDB
- a key-value database service
- features
    - non-relational NoSQL database
    - purpose built
    - millisecond response time
    - fully managed
    - highly scalable

RDS vs DynamoDB
- RDS
    - automatic high availability, recovery provided
    - customer ownership of data
    - customer ownership of schema
    - customer control of network
- DynamoDB
    - key-value
    - massive throughput capabilities
    - PB size potential
    - Granular API access

### Amazon redshift
features
- datawarehouse as a service
- bigdata BI analytics
- collect data from many sources
- helps understand relationships and trends across data

### AWS Database Migration Service (DMS)
features
- relational or nonrelational or other types
- source database remains fully operational during migration
- downtime is minimized for applications that rely on that database
- source and target databases do not have to be fo the same type
    - homogenous vs heterogenous
- development and test database migrations
- database consolidation
- continuous database replication

### additional database services
- Amazon DocumentDB
    - a document database service that supports MongoDB workloads
- Amazon Neptune
    - a graph database service
        - recommendation engines
        - fraud detection
        - knowledge graphs
- Amazon managed blockchain
    - create and manage blockchain networks with open-source frameworks
- Amazon quantum ledger database (QLDB)
    - a ledger database service
    - a complete history of all the changes that have been made to your application data
- Amazon ElastiCathe
    - adds caching layers on top of databases to help improve the read times of common requests
    - supports Redis and Memcached
- Amazon DynamoDB Accelerator
    - in-memory cache for DynamoDB
    - helps improve reponse time from single-digit milliseconds to microseconds


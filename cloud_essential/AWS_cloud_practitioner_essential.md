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




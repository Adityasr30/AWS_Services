## AWS Services
1. IAM
2. S3
3. EC2
4. VPC
5. GLUE
6. LAMBDA
7. API gateway
8. SQS
9. SNS
10. DynamoDB
11. EMR
12. Kinesis
13. Athena
14. Cloud formation

## Region and Availability Zones

**Region:** Geographic areas that AWS uses to house its infrastructure. These are distributed around the world. The closer the network, lower is the network latency.

**Availability Zone:** Each region has multiple AZs. The availability zones in a region are connected using fibre optic cables.

![image](https://github.com/Adityasr30/AWS_Services/assets/86728825/1893450f-d421-482c-8b9c-ffab15397772)

## IAM
- Identity access and management
- Use to create identities, policies
- Types of policies:
  - Identity policy
    - AWS managed: managed by AWS
    - Customer managed: managed by customer
    - Inline: tightly coupled with an identity
  - Resource based policy: Attached to a resource
  - Session based policy: Limited to the session
- Service --> resource
- Identities in AWS: Roles, Users, User groups
-	To give access to someone trying to access AWS outside the organization:
  -	Access key, secret access key
-	To give access to someone trying to access AWS from within:
  -	Role
- Policy is attached to a role. Role is attached to a resource. That resource will assume the role.
- We try to give minimum access to AWS using the principle of least privilege.
- Deny has the highest precedence
- Policy can have many permissions.
- It is written in a json.
- Precedence highest to lowest:
1. Resource based
2. Session policies
3. Identity based
- Components of a policy:
1. Effect
2. Action
3. Resource
4. Condition
5. Principal

## S3
-	Object storage solution, considers every file as an object
-	Includes name, size, date
-	S3 is an implementation of MAP
-	Storage solution In AWS:
1. S3
2. EFS – file system for ec2
3. FSx – file system for windows and lustre
4. EBS – volumes of storage attached to EC2
5. RDS – relational data store
6. Red swift – data warehousing
7. DynamoDB – no sql database
- Storage classes in s3
1. Standard – default
2. Standard IA – cheaper than standard. Used for infrequent access
3. Glacier – Cheapest. Data retrieval is slow. Used for archival.
-	S3 is a regional service
-	Good for many reads, not ideal for many writes.
-	Durability: 11 9’s
-	Versioning – files does not get overridden, instead copies are saved. By default, it is disabled
-	Use cases:
1. Static website hosting
  - Only for displaying information.
  - User cannot enter anything on the website
2. Analytics
-	ACL disabled: only the account owner can access the bucket.

## EC2

- Compute service provided by AWS that allows you to launch and manage virtual machines, known as instances, in the cloud.
- Virtual machines (instances): virtual servers that run in the AWS cloud.
- Flexible scaling
- Various operating systems: Amazon linux, ubuntu, windows server, centos etc.
- Persistent storage: EBS volumes.
- Load balancing: ELB is used to distribute incoming traffic across multiple instances.
- EC2 pricing
1. On demand instances: pay by hour.
2. Reserved instances: instance for a specified duration (1 year or 3 years).
3. Spot instances: bid on unused EC2 capacity, and pay the current spot price.
4. Dedicated hosts: pay for entire physical server. 

## VPC
-	LAN on AWS
-	Purpose: keeping data safe
-	Subnets: logical partitioning of the network
-	How to create VPC:
  -	CIDR range
  -	AWS uses CIDR ranges from 16 and 28
-	First four and last IP address is reserved by AWS.
-	Private subnet – no internet connection
-	Public subnet – internet access
-	Internet gateway: used to provide internet access
-	NAT gateway: Used to allow private instances in a private subnet to access the internet.
-	Bastion host/ Jump server: server whose purpose is to provide access to a private network from external network.
-	Route tables: contains a set of rules that determine how network traffic is directed within the VPC.
-	Security groups – firewall. It is attached to the vpc.
-	VPC endpoint: enable you to privately connect VPC to supported AWS services.
-	Api endpoint: URL used to interact with an application or service throught an API.

## Glue
- ETL servie, data catalog, data integration.
- Offers both visual and code based interfaces.
- Catalog: stores metadata
- Classier: determines schema of the data.
- Connection: Used to connect to a data storage.
- Crawler: Explores data respositories.
- Architecture

![image](https://github.com/Adityasr30/AWS_Services/assets/86728825/343e182a-fda4-44a1-94f8-fc297e08e16f)

- Advantages
1. Serverless - eliminates requirement for infrastructure creation and management.
2. Provides scheduling of jobs.

## Lambda

- Serverless compute service.
- Event-driven execution: Lambda functions are triggered by various AWS services or custom events. Example: an S3 bucket upload.
- Supports multiple languages: Node.js, Python, Java, Go, Ruby, and .NET Core.
- Scales automatically
- Handler function: Entry point to the lambda function. It must be specified in the format of filename.handler_function.
- Event: It the input data that triggered the lambda function. It can be a S3 object creation, API gateway request etc.
- Context: provides information about runtime environment and the execution context of lambda function.

## API Gateway

- Service provided by AWS that makes it easy to create, deploy, and manage APIs.
- It acts as a front door to your backend services, allowing you to expose your application functionality to external clients and developers in a secure and scalable way.
- Types of request: GET, POST, PUT, DELETE.

## SQS

- Queuing service.
- Used to decouple components of any application.
- Types of Queues:
  - FIFO: guarantees order of messages.
  - Standard: order is not preserved.
- At least once delivery.
- Visibility timeout: When a consumer retrieves a message from the queue, SQS makes the message invisible to other consumers for a specific period called the visibility timeout. This prevents multiple consumers from processing the same message simultaneously.
- Dead-Letter Queues: You can set up a Dead-Letter Queue to capture and store messages that couldn't be successfully processed after a specified number of retries. This helps in identifying and handling problematic messages.

## SNS

- Messaging service
- Topic - a communication channel to which messages are sent. All subscribers get the messages.
- Types of topic: Standard and FIFO.
- Publisher: entity that sends messages to an SNS topic.
- Subscriber: endpoint that receives messages.

## Difference between SQS and SNS

SQS is focused on message queuing and decoupling application components, while SNS is focused on message broadcasting to multiple subscribers.

## DynamoDB

- NoSQL database service
- Partition Key: The partition key is a primary key attribute used to distribute data across multiple storage partitions in DynamoDB. It is used to uniquely identify an item within a table and is used as the input to an internal hash function to determine the partition in which the item is stored.
- Sort Key: In a table with a composite primary key, the sort key (also known as range key) is used in combination with the partition key to uniquely identify an item. It is used to determine the sort order of items within a partition. Sort keys are useful for organizing related data together and performing range queries.
- Provisioned Throughput: DynamoDB allows you to provision read and write capacity for your tables to ensure the desired level of performance. You can specify the number of read capacity units (RCUs) and write capacity units (WCUs) to be allocated to the table. Provisioned throughput is measured in RCUs and WCUs, where each unit represents one read or write operation per second for items up to 4 KB in size.
- Types of table class: DynamoDB standard and DynamoDB IA

## EMR

- Cloud based big data processing service.
- Managed hadoop frameworks: EMR enables you to launch and manage hadoop clusters.
- Scalable
- Suppport for various frameworks: supports hadoop, spark, hive, hbase, etc.
- Cluster: group of EC2 instances.
- Instance types: EMR supports various instance families, such as General Purpose, Memory Optimized, Compute Optimized, and GPU instances.
- HDFS: distributed file system that allows EMR to store data across multiple nodes in the cluster.
- YARN: resource manager
- MapReduce: processing model

## Kinesis

- Real-time streaming and processing service for large amounts of data.
- Three main services in Kinesis family:
1. Amazon Kinesis Data Streams: Kinesis Data Streams is the core service and provides real-time data streaming capabilities.
2. Amazon Kinesis Data Firehose: Kinesis Data Firehose is a service that simplifies the process of loading streaming data into other AWS services for further processing or storage.
3. Amazon Kinesis Data Analytics: Kinesis Data Analytics is a service that enables you to analyze streaming data in real-time using SQL queries.

## Athena

- Interactive query service.
- Enables you to analyze and query data stored in Amazon S3 using standard SQL.
- Serverless architecture
- Supports file formats such as CSV, JSON, Parquet, ORC, Avro, etc.

## CloudFormation

- Service that allows you to define and provision infrastructure resources and applications in a declarative and automated manner.
- It enables you to use a template to describe the resources you want to create, modify, or delete, and CloudFormation takes care of the provisioning and management of those resources.
- Infrastructure as Code (IaC): CloudFormation enables you to define your infrastructure as code using JSON or YAML templates.
- Declarative templates.

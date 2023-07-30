AWS Services:
1)	IAM
2)	S3
3)	EC2
4)	VPC
5)	GLUE
6)	LAMBDA
7)	SQS
8)	Kinesis
9)	DynamoDB
10)	SNS
11)	Cloud form
12)	Athena
13)	Airflow

IAM:
•	Identity access and management
•	Use to create identities, policies
•	Types of policies:
o	Identity
	AWS managed
	Customer: managed by customer
	Inline: tightly coupled with an identity
o	Resource
	Attached to a resource
o	Session
	Limited to the session
•	Service  resource
•	Identities in AWS  Roles, Users, User groups
•	To give access to someone trying to access AWS outside the organization:
o	Access key, secret access key
•	To give access to someone trying to access AWS from within:
o	Role
•	Policy is attached to a role. Role is attached to a resource. That resource will assume the role.
•	We try to give minimum access to AWS using the principle of least privilege.
•	Deny has the highest precedence
•	Policy can have many permissions.
•	It is written in a json.
•	Precedence highest to lowest:
1)	Resource based
2)	Session policies
3)	Identity based
•	Components of policy;
1)	Effect
2)	Action
3)	Resource
4)	Condition
5)	Principal
S3:
•	Object storage solution, considers every file as an object
•	Includes name, size, date
•	S3 is an implementation of MAP
•	Storage solution In AWS:
1)	S3
2)	EFS – file system for ec2
3)	FSx – file system for windows and lustre
4)	EBS – volumes of storage attached to EC2
5)	RDS – relational data store
6)	Red swift – data warehousing
7)	DynamoDB – no sql database
•	Storage classes in s3
1)	Standard – default
2)	Standard IA – cheaper than standard. Used for infrequent access
3)	Glacier – Cheapest. Data retrieval is slow. Used for archival.
•	S3 is a regional service
•	Good for many reads, not ideal for many writes.
•	Durability: 11 9’s
•	Versioning – files does not get overridden, instead copies are saved
•	By default, it is disabled
•	Use cases:
o	Static website hosting
	Only for displaying information
	User cannot enter anything on the website
o	Analytics
•	ACL disabled: only the account owner can access the bucket.

VPC:
•	LAN on AWS
•	Purpose: keeping data safe
•	Subnets: logical partitioning of the network
•	How to create VPC:
o	CIDR range
o	AWS uses CIDR ranges from 16 and 28
•	First four and last IP address is reserved by AWS.
•	Private subnet – no internet connection
•	Public subnet – internet access
•	Internet gateway: used to provide internet access
•	Bastion host: server used whose purpose is to provide access to a private network from external network
•	Security groups – firewall
•	Is attached to a vpc

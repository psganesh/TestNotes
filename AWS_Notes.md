# Blue Print
  - Ability to write code using AWS security best practices (e.g., not using secret and access keys in the code,instead using IAM roles)

***
#### (from old course)-----************************------BEGIN

## AWS Global Infrastructure - Exam Tips
  - Understand the difference between a region, an Availability Zone (AZ) and an Edge Location
  - A REGION is the physical location in the world which consists of 2 or more Availability Zones (AZ's) (E.g.: London)
  - An AZ is one or more discrete Data Centers, each with redundant power, networking and connectivity, housed in separate facilities.
  - Edge Locations are endpoints for AWS which are used for caching content. Typically consists of CloudFront, Amazon's Content Delivery Network. (NY <-> Melbourne, caching to nearest (Sydney) when accessing 2nd time it will be accessed from sydney).

## AWS Platform Components

### Compute *
- EC2 (Elastic Compute Cloud) – vm in AWS platform
- EC2 container service - this is where you manage & run docker container at scale
- Elastic BeanStalk - (developer who don't understand AWS, they will just upload code to this) then it provision things like auto Scaling groups, Load balancing, EC2 instance and etc
- Lambda - code - upload into cloud and control it. E.g., lambda function will be triggered if any image is uploaded and text will be writing on top (overlay) of it using lambda.
- Lightsail – Virtual private service, provisioning a server with fixed IP address (RDP access for windows, SSH for Linux) - Control through Management console - Like lower version of EC2 :)
- Batch –  Batch computing in cloud 

### Storage *
- S3 – simple storage service, object based stored, Files will be stored into bucket
- EFS – Elastic File System -  Network attach storage - store into volume and mounted to multiple machines
- Glacier – Data Archival - for eg. need once in a year - cheap
- Snowball – way to bring in large data into data center 
- Storage Gateway – Virtual appliance, replicates info back to S3 - 4 types

#### Database *
- RDS – Relational Db service, mysql, postgress, oracle 
- DynamoDB – Non relational 
- Elasticache -  caching data - for Eg. to store top 10 products in cache rather than to pull from DB using web service - it free up the DB to run the other queries.
- Red Shift – Data Warehousing or BI - here run complex query (lot time complete, joins & etc) for analysis (for e.g. mgmt want to know profit and loss)

### Migration 
- AWS Migration Hub – track your application as you migrate to AWS and integrate with other services within migration framework
- Application Discovery service - Automated discover the dependencies. Eg: share-point or dependency with DB
- Database migration service - for e.g: On premises DB into AWS
- Server migration service - for e,g: server to migrate to AWS
- Snowball - migrate TB data into AWS

### Networking & Content Delivery*
- VPC – virtual private cloud.  Configure your own private cloud (firewall, AZ, N/W side IP range, route tables and etc)
- CloudFront – CDN,  stores your image/video closer to your AZ, edge location
- Route53 – DNS service 
- API Gateway – Create own API to talk to other services
- Direct Connect – direct line from HDQ to amazon cloud / VPC

### Developer Tools 
- CodeStar – collaborating code
- CodeCommit – store code. Version controller. Store GitHub repository
- Code Build - Compile then run tests then produce software packages ready to deploy
- Code Deploy - Automate deployment process into EC2 instances
- CodePipeline - Continuous Delivery service
- X-Ray - debug the application
- Cloud9 – IDE, inside web browser

### Management Tools*	
- Cloud watch – Monitoring service
- Cloud formation – Turning your infrastructure into code (script)
- CloudTrail – log the changes in the AWS ENV. (default turned on for 1 week records)
- Config – monitor the configuration, visual (eg: how on May 4th and 6th)
- OpsWorks - like EBS, automating (configuring) the env
- Service Catalog - used by Big companies for Compliance
- Systems Manager – Managing AWS resources (EC2). Eg. patch maintenance - roll-out patch to 1000 of EC2 instances. Group the resources.
- Trusted Advisor – advice security (eg. port open), risks, capacity 
- Managed services - No need to worry about EC2, Scaling and etc., it helps - New service

### Media Services
- invented into 2017 (new)
- Elastic Transcoder – (old service) resize video to android /ios
- MediaConvert - File based media transcoding service
- MediaLive - Live video processing service
- MediaPackage - protects from Internet
- MediaStore - store service
- MediaTailor - 

### Machine Learning 
- Sagemaker – 
- Comprehend 
- Deeplens – physical hardware – camera
- Lex
- Machine learning 
- Polly – text to voice 
- Rekognition – upload image / video, will tell you what it is
- Amazon translate – translator
- Amazon Transcribe – speech recognition – speech to text  

### Analytics *
- Athena - run SQL queries against S3 bucket. (report excel)
- EMR – big data solution. To process large data 
- Cloudsearch 
- ElasticSearchService
- Kinesis – bigdata, ingesting large amount of data into cloud (eg tweets # hash tag)
- Kinesis Video Streams - 
- Quicksight – BI tool
- Data Pipleline – moving the data bw diff amazon services
- Glue – used for ETL

### Security & Identity & Compliance *
- IAM – Identify Access Management
- Cognito – Authentication service, gives temp access to AWS
- GuardDuty – Monitors for malicious activity
- Inspector – Agent (to be installed). governance tool, check the vulnerability 
- Macie – scans S3 for PII data
- Certificate Manager – manage SSL 
- CloudHSM – Hardware security Module - stores encryption keys 
- Directory Service – integrating Active directory
- WAF – Web Application Firewall – prevent XSS, Sql injection
- Shield – prevent Ddos attacks 
- Artifact – download compliance report, PCI report (downloading & inspecting AWS documentation)

### Mobile Service 
- Mobile Hub – management console for mobile apps, 
- PinPoint – push notifications to mobile users
- AWS Appsync – automatically updates the data (off-line).  
- Device Farm - testing apps in real devices
- Mobile Analytics

### AR / VR 
- Sumerian – code name 

### Application Integration*
- Step functions - way of managing diff Lambda function
- Amazon MQ
- SNS – Notification service (eg. if bill reaches 10$ then notification will be sent to your phone)
- SQS - Simple Queue service. Decoupling infrastructure. Queue -> EC2 (for processing), in case EC2 is died the queue still has request data.
- SWF – Simple Work-flow Service 

### Customer Engagement 
- Amazon Connect
- SES - Simple Email Service 

### Business Productivity 
- Alexa for Business 
- Chime – Video conference like xoom / Google handout
- Work Docs - like drop box
- WorkMail – like office 365

### Desktop and App Streaming 
- Workspaces - VDI solution - literally run OS
- AppStream 2.0 - like citrix 

### IOT
- IOT device management 
- Amazon FreeRtos – OS for micro controller 
- GreenGrass 

### Game Development
- GameLift - to develop VR games in cloud

#### (from old course)-----************************------END
***


# Identity Access Management (IAM)
  - IAM allows you to manage users and their level of access to the AWS console.
  - Critical Terms
    - Users - End users (think people)
    - Groups - A collection of users under one set of permissions (ex: Marketing Group / Sys Admin Group)
    - Role - can assign to AWS resources (not for people) (e.g. Assign Role to EC2 to access S3)
    - Policy - A document that defines one (or more) permissions. This can be attached to User/Group/Role. Possible for user/group/role to share the same policy.
  - LAB
    - US East (N. Virgina) - New services are launched first in this region.
  - IAM is universal (Global). It does not apply to regions at this time.
  - "root account" -> first setup AWS account (email id). it has complete Admin Access.
  - New users have no permissions when first Created.
  - New Users are assigned Access Key Id & Secret Access keys (first created, if lost then regenerate) -> not for login using AWS console -> used to access AWS via API & CLI
  - arn -> Amazon Resource Name
  - FAQ????????? https://aws.amazon.com/iam/faqs/
  
***
#### ***************** OLD COURSE **********************-- Beg
# STS – Security Token Service
- Grants users limited & temp access to AWS resources
- Federation – SAML, AD, Single sign on 
- Federation Mobile – FB, amazon, Google or openId to login
- Cross account access – one aws account to access another resource 
- Federation – Combining list of users from one domain with list of users in another domain. Like from IAM to AD or FB
- Identity Broker – service that allows you take an identity from point A and join (federate) it with point B
- Identity Store – AD, FB, Google 
- Identity – user of service like FB
- Identity Broker always authenticate with federation (AD, LDAP, FB, Google)  first then STS
# Active Directory Federation 
- AssumeRoleWithSAML API 
- Always authenticated with AD first then AWS
- SAML – Security Assertion Markup language 
# Web Identity Federation 
- Authenticate using Google, FB, LinkedIn 
- AssumeRoleWithWebIdentity API
- ARN – Amazon Resource Name
# Cognito
- Web identity federation service 
- User first authenticated with web identity provider (FB). Received auth token, exchanged for temp. aws credentials allowing them to assume an IAM role
- Provide signup / signin for your apps
- Access for guest users 
- Acts identity broker between your app and web ID providers (FB or Google)
- Recommended for mobile apps runs on aws
- Uses Push synchronization – to push updates and synchronize user data across multiple devices 
- SNS is used to silent push notification to all the devices associated with the given user identity 
- User pools - A user pool is a user directory in Amazon Cognito. With a user pool, your users can sign in to your web or mobile app through Amazon Cognito. Your users can also *sign in through social identity providers* like Facebook or Amazon, and through SAML identity providers.  
- Identity pools  - Identity pools provide AWS credentials to grant your users access to other AWS services. To enable users in your user pool to access AWS resources, you can configure an identity pool to exchange user pool tokens for AWS credentials  
- 
#### ***************** OLD COURSE **********************-- End
***


# EC2 (Elastic Compute Cloud)
  - VM - Pay only for capacity that you actually use
  - Pricing Options:
    - On Demand Instance
      - Fixed rate by the hour or second with no commitment (linux by second & Windows by hours now)
      - who want low cost, no upfront payment & longterm commitment, flexible, short term, unpredictable workload, first time
    - Reserved Instance
      - contract with AWS, 1 or 3 years terms reserve - significant discount on the hourly charge
      - steady state or predictable usage appl, reserved capacity
      - Standard RIs (up-to 75% off on-demand), Convertible RIs (up-to 50%) - change reservations, Scheduled RIs (within timewindow, requires for a day/week/month, eg: every weekend / friday)
    - Spot Instance 
      - to bid price (assume, share market price variation) - greater saving if flexible start & end times (eg: 4am on sunday morning)
      - e.g. Bid at 100$. if spot price goes down to 90$ then no issue (provisioned). if 110$ then those instances will be terminated.
      - If amazon terminates the instance (bid range), you don’t have to pay (not charged for partial hour)
      - If you terminate the instance, you will be charged for the complete hour in which the instance ran.
    - Dedicated Hosts 
      - physical EC2 dedicated for use. use existing software licenses.
      - not support multi-tenancy or cloud deployments
      - can be purchased on Demand (hourly), as reservation (up-to 70% off on-demand)
  - EC2 Instance Types
    - FIGHT_DR_MC_PX !!!!!!!!!!
      - F -> Field Programmable Gate Array (FPGA) => Genomics research, Financial analytics, real time video processing, big date & etc
      - I -> High speed Storage (IOPS) => NoSQL DBs, Date Warehousing etc
      - G-> Graphics Intensive => Video Encoding / 3D Application Streaming
      - H -> High Disk Throughput => MapReduce-based workloads, distributed file systems such as HDFS & MapR-FS
      - T -> cheap general purpose (think T2 Micro) => Webservers / small DBs
      - D -> Density Storage => Fileservers / Datawarehousing / Hadoop
      - R -> Memory optimized (RAM) => Memory Intensive Apps/DBs
      - M -> Main choice for general purpose apps => Application Servers
      - C -> Compute optimized => CPU Intensive Apps/DBs
      - P -> Graphics/General purpose GPU (think PICS) => Machine Learning, Bit coin mining etc
      - X -> Extreme Memory optimized => SAP HANA/Apache Spark etc

## EBS (Elastic Block Storage)
  - Virtual Disk, Storage volume attached to EC2 Instances. run DB or use like block device
  - Placed in a specific AZ. Automatically replicated to protect from failure
  - EBS attached with EC2 is called Root Device Volume. (eg. windows -> C: drive)
  - Types
    - General Purpose SSD (GP2)
      - General purpose, balances both price and perf.
      - Ratio of 3 IOPS per GB ~ 10,000 IOPS
      - burst up-to 3000 IOPS for extended periods for vol 3334 GiB and above
     - Provisioned IOPS SSD (IO1)
       - I/O Intensive such as large relational or NoSQL DB
       - '> 10,000 IOPS (extreme perf)
       - ~ 20,000 IOPS per volume
     - Throughput Optimized HDD (ST1)
       - Low cost, Freq accessed, throughput intensive workloads
       - Big Data, Date warehousing, Log Processing
       - Cannot be a boot volume (eg. not C: drive, can be D:)
     - Cold HDD (SC1)
       - Lower cost, infreq accessed workloads
       - File server
       - Cannot to be boot volume
     - Magnetic (Standard)
       - Previous Generation. BOOTABLE, Lower cost, infreq accessed workloads, lowest storage cost is important (eg. might use it DEV or TESTING environment then move over to SSD)
    
    - (copied below)
    - Cannot mount 1 EBS volume to multiple EC2 instances – instead us EFS
    - Can transfer reserved instance from one AZ to another

### EC2 Lab (copied)
- AMI – Amazon Machine Instance  (when you create AMI, registerImage is the final process)
- AMI can be shared to other AWS account 
- AMI can be changed to public
- If you make AMI, it will not be immediately available across all regions
- AMI’s can be only be shared within region.  For other regions do copy
- Instance type – t2 micro 
- Default VPC
- One subnet always will be in one AZ.  Same subnet range will not be shared across AZ.
- Termination protection – by default its Off
- Monitoring – cloud watch 
- Tenancy – dedicated 
- Advanced Details – user input, Boot instructions (install PHP SDK, apache)
- Storage – Root, Boot volume
- By default Root volume can’t be encrypted.  Either bit locker, or encrypt when creating AMI or API.  
- By Default Root EBS volume will be deleted on termination.  Option can be changed
- Tags
- Security Group, SSH, SSL, HTTP. 
- Source – Custom, Anywhere, My IP.  Anywhere means open to world 
- Key Pair – Pem file
- Same private key can be used for multiple EC2
- Status check –System Status check, Instance Status check 
- Monitoring, Cloud watch – basic monitoring, CPU. Disk,Nw
- Standard monitoring – 5 mins 
- Private key should be protected from read/write from other users. 
- Unprotected private key file – do chmod 400
- Unix
  - Change the permission chmod 400 *.pem
  - ssh ec2-user@<ip> -i <pem>
  - sudo yum update -y ->   to update security packages, -y to force update 
  - yum install httpd –y –>  install apache 
  - cd /var/www/html 
  - nano – text editor 
  - nano index.html 
  - Add something 
  - Ctrl X to exit and save 
  - service httpd start
  - chkconfig httpd on -  starts automatically with boot
- Windows
  - Putty Keygen to convert pem to ppk

## Elastic Load Balancers
  - Balance the load across multiple instances
  - 3 types
    - Application Load Balancers
      - works at OSI Layer 7. takes clever decision. (for eg: sales.gane.com => route to sales EC2)
      - Suited for HTTP & HTTPS traffic. Sending specific request to specific web servers. (think: model X tesla car -> route to specific EC2)
    - Network Load Balancers
      - layer 4. Extreme speed. costlier.
      - suited for TCP Traffic. Capable of handling millions of request per sec. (think: tesla car -> 0~2 sec reach -> 60 mph -> super fast)
    - Classic Load Balancers
      - legacy. Balance HTTP/HTTPS applications using layer 7 specific features such as X-Forward. 
   - 504 error (ELB response) means the gateway has timed out. This means that the application not responding within the idle timeout period.
     - Troubleshoot the application. Is it the web server or Database server?
   - If you need the IPv4 address of your end user, look for the X-Forwarded-For Header. (ie. to see the public ip address 124.12.3.121, where the request is coming from)

## Route 53 Lab
  - DNS service
  - Domain names to 
    - EC2 instances
    - Load Balancers
    - S3 Buckets
  - Steps
    - Services >> N/w CDN >> Route 53 >> Create Hosted Zones
      - First time means -> Register a Domain (eg. imcloudguru.com -> 12$) -> complete purchase (3 days to complete creation)
      - Create Record Set
        - A record (A -> IPv4 address, AAAA -> IPv6 address) => Alias (supports A & AAAA) => Map ALB (create a new ApplicationLoadBalancer before that) (can map not only ALB, S3 & etc)
        - Create ALB
          - Load Balancers >> Create LB >> Application LB >> Specify (Name: eg.MyALB, Scheme: Internet-facing, IPAddress Type: ipv4, Listeners: HTTP 80, HTTPS 443 if needed, AZ: All) >> Assign Security Groups (eg. MyWebDMZ) >> Configure Routing (Create Target group.eg> MyWebServerGroup. Note: Each target group to only one One LB, Specify Health Checks eg. index.html) >> Register Targets (Add to registered eg. already created EC2 instance) >> CREATE
   - imcloudguru.com -> ALB -> EC2 instance -> index.html ("Welcome to AWS world..!!!")

### CLI Demo Lab
  - Commands used in Video
    - ssh ec2-user@xx.xx.xx.xx -i MyNewKeyPair.pem 
    - sudo su
    - aws <commands>
    - aws s3 ls ==>ERROR: unable to locate credentials. You can configure credentials by running "aws configure"
    - aws configure (then enter Access key Id, Secret Access key, Default Region: 'eg: us-east1', Default output format: 'eg. text')
    - aws s3 mb s3://ganeshps123-psg (here mb -> make bucket)
    - echo "hello AWS" > hello.txt
    - aws s3 cp hello.txt s3://ganeshps123-psg
    - aws s3 ls (it will list hello.txt)
    - able to see in console? - make public - 'ganeshps123-psg'
  - https://docs.aws.amazon.com/cli/latest/index.html => commands
  - Least Privilege - Give users min amount of access
  - Create groups - assign to users. will auto inherit the permissions from group
  - Secret Access Key - only once. if lost, delete the pair and re-generate it. Need to 'aws configure' again.
  - Do not use just one access key - create per developer
  - You can use the CLI on your PC

### EC2 with S3 Role Lab
  - create role for ex: full access to S3 and attach with EC2 then try following commands
    - aws s3 ls
    - sometimes access error still will be shown due to credentials stored in server. Delete them using following steps
      - cd ~/.aws
      - rm config
      - rm credentials
    - then try 'aws s3 ls' => this time it should list the S3    
  - https://docs.aws.amazon.com/cli/latest/userguide/cli-config-files.html => check for windows to access credential files
  - Exam Tips
    - Roles allow you to not use Access key ID's and Secret Access Keys
    - Roles are preferred from a security perspective
    - Roles are controlled by policies
    - You can change a policy on a role and it will take immediate effect
    - You can attach or detach roles to running EC2 instances without having to stop or terminate

## How to Encrypt an EBS volume
  - 1. Additional Volume ?
    - EC2 >> EBS >> Volume >> Create Volume >> Select Volume type (GP2), size 100 GB, AZ (same AZ where EC2 present).... SELECT Encryption, Select Master key (default - aws/ebs) >> Create column
    - Actions >> Attach volume >> Select the EC2 instance >> Attach
    - Note: If you create volume from ENCRYPTED Snapshot, then the volume also will be encrypted.
    - Commands
      - ssh *** >> sudo su 
      - lsblk (=> it will show default attached with root '/' xvda & recently attached volume above xvdf)
      - file -s /dev/xvdf (=> check file system. Default: "/dev/xvdf: data" -> means no data in the volume and can proceed to create file-system)
      - mkfs -t ext4 /dev/dvdf (=> Create file system)
      - file -s /dev/xvdf (=> now it will show file system which was created just before)
      - How to mount?
        - cd /
        - mkdir filesystem
        - mount /dev/xvdf /filesystem
        - lsblk (=> it will show the mountpoint as /filesystem)
      - unmount?
        - cd /
        - umount -d /dev/xvdf
    - Create snapshot
      - EBS >> Volume >> after detach >> Actions >> create snapshot (specify description)
      - view : EBS >> Snapshots >> View all the snapshots here
      - now you can delete the above created volume. 
      - Can CREATE volume (EBS >> Snapshots >> Action >> Create Volume (Specify Type, SIze.... note here volume is encrypted because this snapshot was encrypted)). Can attach this created vol to EC2. This time you will see the files which created earlier.
  - 2. Root Volume ?
    - 2 ways
      - 1. bitlocker - windows
      - 2. create snapshot of root volume >> Snapshots >> Select the newly created root snapshot >> actions >> copy >> specify AZ & SELECT Encryption >> Copy.
        - then '>> snapshots >> Actions >> Create Image
        - then '>> Images >> AMIs >> Launch >> select the Instance Type and Launch the new instances
  - EXAM TIPS
    - 1. can encrypt root device volume (the vol of the OS is installed on) using OS level encryption (ex: bitlocker)
    - 2. can encrypt root device vol by first taking a snapshot then copy with encryption then make AMI of this snap and deploy the encrypted root device volume
    - You can encrypt the additional attached volumes using the console, CLI or API
	
# RDS 101 - Relations DataBase Service
  - RDS - OLTP (On-line Transaction Processing)
    - SQL, MySQL, PostgreSQL, Oracle, Aurora, MariaDB
  - DynamoDB - NoSQL
    - Database
      - Collection => Table
      - Document => Row
      - key value pairs => Fields
      (think JSON sample)
  - Redshift - OLAP (On-line Analytical Processing)
  - Elasticcache - In Memory Caching:
    - 2 engines: Memecached
    - Redis
    
### RDS Lab
  - Create RDS DB (MySQL)
  - Commands for startup script EC2
    - "#!/bin/bash  
	yum install httpd php php-mysql -y  
	yum update -y  
	chkconfig httpd on  
	service httpd start  
	echo "<?php phpinfo();?>" > /var/www/html/index.php
	cd /var/www/html  
	wget https://s3.eu-west-2.amazonaws.com/acloudguru-example/connect.php"
    - Create EC2 instance using above startup script
    - Change connect.php
    - Specify EC2 security group (myWebDMZ) as source in Inbound of rds security group with port 3306. ???? i.e. since the security group of RDS and EC2 is different, allow EC2 security Group in RDS inBound. EC2 must be allowed to talk to RDS.
    
### RDS Multi-AZ and Read Replicas
  - 2 types of backups
    - Automated Backups
      - recover at any point of time within a "retention period" (1~35 days)
      - full daily snapshot. AWS will choose first the most recent daily back up. recovery down to a second    
      - enabled by default. stored in S3. free data storage 10GB RDS = 10GB S3 storage
      - Backups are taken on defined window. suspended during that time.
    - Database snapshots
      - Manual (user initiated). They are stored even after delete the original RDS instance, unlike automated backups.
  - Restoring backups => restored version of DB will be new RDS instance with new DNS endpoint (ie., original.eu-west-1.rds.amazonaws.com => restored.eu-west-1.rds.amazonaws.com)
  - Encryption
    - supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora.
    - done using AWS Key Management service (KMS).
    - once RDS instance is encrypted, data stored also encrypted.
    - At present, encrypting an existing DB instance is not supported. 
    - To use amazon RDS encryption for existing, 1. create snapshot 2. copy snapshot 3. encrypt the copy
  - Multi AZ
    - DR only. (US-EAST-1A <=> US-EAST-1B). Any change in 1A will be synchronously replicated to 1B (diff AZ). If 1A is failed due to Disaster, then 1B will be pointed.
    - RDS is dealt with DNS (gane.xxxxxxx.eu-west-1.rds.amazonaws.com). if primary DB is failed, then the secondary IP address will be mapped with this DNS (during fail over).
    - not for improving performance. Only for DR.
    - SQL Server, Oracle, MySQL Server, Postgre SQL, MariaDB
  - Read Replicas
    - 5 Read replicas for production for default. New writes will be pushed to other replica DB.
    - allow you to have a read-only copy of your production DB. This is achieved by using Async replication from primary RDS instance to the read replica.
    - mainly for very read-heavy DB workloads.
    - MySQL Server, PostgreSQL, MariaDB, Aurora
    - used for SCALING, NOT for DR. Must have auto backup turned on in order to deploy a read replica. Up-to 5 readreplica of any DB.
    - Read replica of Read replica is possible (but watch out for latency). Each read replica has its own DNS end point.
    - Can have RR that multi AZ. Can create RR of multi AZ source DB.
    - RR can be promoted to be their own DB. This breaks the replication. (For eg. if not using all RR for production, you can use for other DB purpose)
    - can have RR in a 2nd region.
# Elasticache 101
  - In-memory cache. (e.g. Results of Querying top 10 products in Elasticache than accessing DB)
  - Improve latency & thoughput for read-heavy application workloads (such as social networking, gaming, media sharing, Q&A portals & recommendation engines)
  - Types
    - Memcached
      - widely adopted. NO persistence. Pool that grow and shrink like EC2 Auto scaling group (i.e., auto adds web server).
      - Use Case
        - Is Object caching is primary goal, for ex to offload your DB?
	- Simple caching model?
	- Are you planning on running large cache nodes and require multi-threaded performance with utilization of multiple CPU cores?
	- scale your cache horizontally as you grow?
    - Redis
      - open source in-memory key-value store that supports data structure such as sorted sets and Lists.
      - Support master/slave replication & Multi-AZ to achieve cross AZ redundancy.
      - like relation DB. failover like RDS DB failover
      - Use Case
        - Advance types such as LISTS, Hashes & Sets?
	- Sorting and ranking datasets in memory help you such as with LEADERBOARDS?
	- Is persistence of your key store important?
	- want to run multiple AWS AZ with failover?
	- Pub/Sub capabilities are needed?
   - TIPS
     - Elasticache is a good choice if your DB is paricularly read-heavy and not prone to frequent changing
     - REDSHIFT is a good answer if the reason your database is feeling stress is because management keep running OLAP transcations on it etc.
     - Dataware housing questions => choose Redshift
### EC2 Summary
  - Developer Associate exam is Server less focused than EC2.
# S3 (Simple Storage Service)
  - Object based Storage (files, images, web pages... NOT for OS, DB). Not Block Storage.
  - Not Suitable to install an OS or running a DB on.
  - Files can be from 0 - 5 TB. Unlimited Storage.
  - Files are stored in buckets (folders).
  - S3 is a universal name-space. (like website - DNS ). Ex. https://s3-eu-west-1.amazonaws.com/ganeshps123
  - Read after Write consistency for PUTS of new Objects
  - Eventual Consistency for overwrite PUTS and DELETES (can take sometime to propagate)
  - S3 Storage classes/Tiers:
    - S3 => Durable, immediately available, Frequently accessed
    - S3 - IA => Durable, immediately available, IN-Frequently accessed
    - S3 - One Zone IA => Same as IA. However, data is stored in a single AZ only.
    - S3 - Reduced Redundancy Storage (data this is easily reproducible, such as thumbnails etc)
    - Glacier => Archived data, where you can wait 3-5 hrs before accessing
  - Remember the core fundamentals of an S3 Object:
    - key (name of the file)
    - value (data)
    - version ID
    - Meta data
    - Subresources - bucket-specific configuration:
      - Bucket Policies, Access Control Lists
      - Cross Origin Resource sharing (CORS) (=>accessing files in another bucket)
      - Transfer Acceleration (=>using CloudFront)
  - Successful uploads will generate a HTTP 200 status code - when you use CLI or API (not in console)
  - FAQ : https://aws.amazon.com/s3/faqs
  - S3 Charges
    - Storage per GB
    - Requests (Get, Put, Copy, etc)
    - Storage Management Pricing
      - Inventory, Analytics, and Object Tags
    - Data Management Pricing
      - Data transferred out of S3
    - Transfer Acceleration
      - Use of CloudFront to Optimize transfers
  - S3 Security
    - By Default, all newly created buckets are PRIVATE.
    - Bucket's Access control
      - Bucket Policies => Applied at a bucket level.
      - Access Control Lists => Applied at an object level.
    - S3 buckets can be configured to create access logs, which log all request made to the S3 bucket. These logs can be written to another bucket.
  - Sample Bucket Policy
    - "{
	  "Id": "Policy1538559530437",
	  "Version": "2012-10-17",
	  "Statement": [
	    {
	      "Sid": "Stmt1538559526441",
	      "Action": [
		"s3:GetBucketPolicy"
	      ],
	      "Effect": "Allow",
	      "Resource": "arn:aws:s3:::ganeshps123-psg",
	      "Principal": "\*"
	    }
	  ]
	}"
  - S3 Encryption
    - Encryption In-Transit
      - SSL/TLS (HTTPS) => over the network
    - Encryption At Rest
      - Server Side Encryption
        - S3 Managed Keys (SSE-S3)
	- AWS Key management service, managed keys(SSE-KMS) (=> has audit features like who used keys last time etc)
	- Customer provided keys => SSE-C
      - Client Side Encrption
    - To enforce the use of encrption for your files stored in S3, use an S3 Bucket Policy to deny all PUT requests that don't include the x-amz-server-side-encryption parameter in the request header:
      - 2 options
        - x-amz-server-side-encryption:AES256
	- x-amz-server-side-encryption:aws:kms
  - Setup Encryption On an S3 Bucket
	  - {
	    "Id": "Policy1538564409891",
	    "Version": "2012-10-17",
	    "Statement": [
		{
		    "Sid": "Stmt1538564407861",
		    "Action": [
			"s3:PutObject"
		    ],
		    "Effect": "Deny",
		    "Resource": "arn:aws:s3:::ganeshps1234-psg/*",
		    "Condition": {
			"NumericNotEquals": {
			    "s3:x-amz-server-side-encryption": "aws:kms"
			}
		    },
		    "Principal": "*"
		}
	    ]
	}

  - CORS Configuration Lab
	  - "&lt;!-- Sample policy --&gt;
		&lt;CORSConfiguration&gt;
			&lt;CORSRule&gt;
				&lt;AllowedOrigin&gt;http://myindexprojectpsg.s3-website.ap-south-1.amazonaws.com/&lt;/AllowedOrigin&gt;
				&lt;AllowedMethod&gt;GET&lt;/AllowedMethod&gt;
				&lt;MaxAgeSeconds&gt;3000&lt;/MaxAgeSeconds&gt;
				&lt;AllowedHeader&gt;Authorization&lt;/AllowedHeader&gt;
			&lt;/CORSRule&gt;
		&lt;/CORSConfiguration&gt;"
# CloudFront
  - Edge Location 
    - This is the location where content will be cached. This is separate to an AWS Region/AZ.
  - Origin
    - This is the origin of all the files that the CDN will distribute. Origins can be an S3 bucket, EC2 instance, ELB, Route53.
  - Distribution
    - This is the name given the CDN, which consists of a collection of Edge Locations.
    - Web Distribution => Typically used for websites
    - RTMP => (Adobe Real time messaging protocol) used for media streaming.
  - Edge locations are not just READ only - you can WRITE to them too. (i.e., PUT an object on to them)
  - CloudFront Edge Locations are utilized by S3 Transfer Acceleration to reduce latency for S3 uploads.
  - Objects  are cached for life of the TTL (Time to Live). (Default 24 hours)
  - You can clear cached objects, but you will be charge. (invalidation)
  
### S3 Performance Optimization - Exam Tips
  - 1. GET-Intensive workloads => use CloudFront
  - 2. Mixed workloads => Avoid sequential key names (S3 Objects). Use Random prefix like a hex hash 'eg. 7d4532-xxxx' to prevent multiple objects being stored on the same partition.
  - In July 2018, Amazon increase S3 performance
    - 3,500 put requests per second
    - 5,500 get requests
  - FAQ: https://aws.amazon.com/s3/faqs
  
# Server-less 101
  - 
## Lambda
  - Compute service where you can upload your code and create a Lambda function. Lambda takes care of provisioning and managing the servers that you use to run the code.
  - Use lambda in following ways:
    - As an event driven compute service where AWS Lambda runs your code in response to events.
    - As a compute service to run your code in response to HTTP requests using Amazon API gateway or API calls made during AWS SDKs.
  - Lambda scales out (not up) automatically. (can have/run millions of functions in parallel but if run out of memory you need to update the amount of memory lambda using) (in other words, you can have many many concurrent functions running at once)
  - Lambda functions are independent, 1 event = 1 function
  - Lambda is server-less
  - Know what services are server-less ! (things like Lambda, Gateway, S3, DynamoDB etc.., not RDS)
  - Lambda functions can trigger other lambda functions, 1 event = x functions if function trigger other functions
  - AWS X-ray allows to debug
  - Lambda can do things globally. (for e.g. used to backup S3 buckets to other S3 buckets)
  - Know your triggers. (memorize the list triggers that can be configured like S3, SNS and etc) - exam?
## API Gateway
  - Think Waiters in hotel to serve food. (Customer -> waiter -> chef)
  - has caching capabilities 
  - low cost, scales automatically
  - can throttle API Gateway to prevent attacks (same-origion-policy)
  - log results to CloudWatch
  - Enable CORS if multiple domains
  - CORS is enforced by client
### Build Simple Serverless
  - Create Lambda => Create API GateWay
  - Create S3 
    - ?????
## Version Control with Lambda
  - Exam Tips
    - Can have multiple versions of Lambda Expressions.
    - Latest version will use $Latest
    - Qualified version will use $Latest, unqualified will not have it.
    - Versions are immutable (cannot be changed)
    - Can split traffic using aliases to different versions
      - Cannot split traffic with $Latest, instead create an alias to latest
### Step Functions =?
  - Great way to visualize your serverless application & test. It provides graphical console.
  - Step functions automatically triggers and tracks each step.
  - Step functions logs the state of each step so if something goes wrong you can track what went wrong and where.
### X-Ray =?
  - The X-Ray SDK Provides:
    - Interceptors to add to your code to trace incoming HTTP requests
    - Client handlers to instrument AWS SDK clients that your application uses to call other AWS Services
    - An HTTP client to use to instrument calls to other internal and external HTTP Web services
  - The X-Ray integrates with the following AWS Services:
    - Elastic Load Balancing
    - AWS Lambda
    - Amazon API Gateway
    - Amazon Elastic Compute Cloud
    - AWS Elastic Beanstalk
  - The X-Ray integrates with the following languages:
    - Java, Go, Node.js, Python, Ruby, .Net
### Advanced API Gateway
  - Import API's using Swagger 2.0 definition files
  - API Gateway can be throttled
    - Default limits are 10,000 rps (req per sec) or 5,000 concurrently
  - You can configure API gateway as a SOAP Webservice passthrough
# Introduction to DynamoDB
  - Low latency NOSQL DB
  - Consists of Table items (rows) and Attributes (columns)
  - Support both document and key-value data models
  - supported document formats are JSON, HTML, XML
  - 2 types of primary key
    - Partition Key (unique key) => eg. User Id
    - Composite key (Partition key + Sort Key) => eg. User Id + Date A/c created
  - 2 consistency models
    - Strongly consistent => Any write before read will be reflected and consistent
    - Eventually Consistent => Best performance
  - Access controlled using IAM policies
  - Fine grained access control using IAM condition parameter 'dynamodb:LeadingKeys' to allow users to access only the items where the parition key value matches their user id.
### DynamoDB Indexes
  - enable fast queries on specific data columns.
  - Give you a different view of you data based on alternative parition or Sort Keys
  - 1. Local Secondary Index
    - Must be created at when you create your table
    - Same Partition key as your table
    - Different Sort key
  - 2. Global Secondary Index
    - Can create any time - at tabel creation or after
    - Different Partition Key
    - Different Sort key
### Scan Vs Query API Call
  - A Query operation finds items in a table using only the Primary Key Attribute.
  - You provide the Primary key name and a distinct value to search for.
  - A Scan operation examines every item in the table
  - By default returns all date attributes.
  - Use the __ProjectionExpression__ parameter to refine the results.
  - Query results are always sorted by the sort key is there is one
  - SOrted in ascending order
  - Set ScanIndexForward parameter to false to reverse the order queries only
  - Query operation is generally more efficient than a scan.
  - Reduce the impact of a query or scan by setting a smaller page size which uses fewer read operations.
  - Isolate scan operations to specific tables and segregate them from your mission-critic traffic
  - Try parallel scans, rather than the default sequential scan
  - Avoid using scan operations if you can: design tables in a way that you can use the query, get, or BatchGetItem APIs.
### DynamoDB Provisioned Throughput
  - Provisioned Throughput is measured in Capacity Units
  - 1 x Write Capacity Unit = 1 x 1 KB Write per Second
  - 1 x Read Capacity Unit = 1 X 4 KB Strongly consistent Read or 2 x 4 KB Eventually Consistent Read
  - Calculate - capacity Units for each READ
    - 1. How many __READ capacity Units = size of each item / 4 KB__ then round to the nearest whole number (eg 3KB/4KB = 0.75 => 1)
    - 2. 
      - for Strongly consistent Reads=> No. of capacity Unites * no. of read per sec required (eg. 1 * 80 => 80 Read Capacity units required )
      - for Eventually consistent Reads => No. of capacity Unites * no. of read per sec required (eg. 1 * 80 / 2 => 40 Read Capacity units required )
  - Calculate - capacity Units for each WRITE
     - 1. How many __WRITE capacity Units = size of each item / 1 KB__ then round to the nearest whole number (eg. 512B/1KB = 0.5 => 1)
     - 2. No. of capacity Unites * no. of write per sec required (eg. 1 * 100 => 100 write Capacity units required)
### DynamoDB Accelerator (DAX)
  - Provides in-memory caching for DynamoDB tables
  - Improves response times for Eventually Consistent reads only
  - You point your API calls the DAX cluster, instead of your table
  - If the item you are querying is on the cache, DAX will return it; otherwise it will perform an Eventually Consistent GetItem operation to your DynamoDB table.
  - Not suitable for write intensive applications, or applications that require Strongly consistent reads.
  - Suitable sites eg. Auction Sites, Black Friday Sale and etc...
### Elasticache
  - In memory cache sits between your application and DB
  - 2 different caching strategies: Lazy loading and Write Through
  - Lazy loading only caches the data when it is required
  - Elasticache Node failures not fatal, just lots of cache misses
  - cache miss penalty: initial request, query database, writing to cache
  - Avoid stale data by implementing TTL
  - Write Through strategy writes data into the cache whenever there is a change to the DB
  - Data is never stale
  - Write Penalty: each write involves a write to the cache
  - Elasticache node failure means that data is missing until added or updated in the DB
  - Wasted resources if most of the data is never used
# KMS 101 - AWS Key Management Service
  - to create and control the encryption keys
  - integrate with EBS, S3, Amazon Redshift, Amazon Elastic Transcoder, Amazon WorkMail, RDS, and others to make it simple to encrypt your data with encryption keys that you manage
  - Encryption keys for KMS is regional (but not IAM). i.e., can not use the key created in one region to other region.
  - Customer Master Key (CMK) consists of following:
    - Alias
    - Creation Date
    - Description
    - key state
    - key material (either customer/AMS provided)
  - can NEVER be exported (if export needed then use CloudHSM not CMK)
  - Setup a CMK
    - 1. Create Alias and Description
    - 2. Choose material option....
      - Define key __Administrative permissions__
        - IAM users/role that can administer (but not use) the key through the KMS API
      - Define key __Usage Permissions__
        - IAM users/role that can use the key to encrypt or decrypt data.
  - Key Material Options:
    - Use KMS generated key material
    - Your own key material (not for dev associate exam - outside scope)
### KMS API Calls
  - aws kms encrypt --key-id YOURKEYIDHERE --plaintext fileb://secret.txt --output text --query CiphertextBlob | base64 --decode > encryptedsecret.txt
  - aws kms decrypt --ciphertext-blob fileb://encryptedsecret.txt --output text --query Plaintext | base64 --decode > decryptedsecret.txt
  - aws kms re-encrypt --destination-key-id YOURKEYIDHERE --ciphertext-blob fileb://encryptedsecret.txt | base64 > newencryption.txt 
  - aws kms enable-key-rotation --key-id YOURKEYIDHERE
### KMS Envelope Encryption
  - CMK (Customer master key)
  - CMK used to decrypt the data key (Envelope key)
  - Envelope key is used to decrypt the data 
# SQS
  - SQS is a distributed message queueing system
  - Allows you to decouple the componenets of an application so that they are independent
  - PULL based, NOT PUSH based
  - 1. Standard Queues (default) => best-effort ordering (not guarantee); message delivered at least once
  - 2. FIFO Queues (First In First Out) => Ordering strictly preserved, message delivered once, no duplicates. e.g. good for banking transactions which need to happen in strict order.
  - Visibility Timeout 
    - Default is 30 seconds - increase if your task takes > 30 seconds to complete
    - Max 12 hours
  - Types of Polling
    - 1. Short polling => returned immediately even if no messages are in the queue
    - 2. Long polling => polls the queue periodically and only returns a response when a message is in the queue or the timeout is reached.
# SNS (Simple Notification Service)
  - SNS is a scalable and highly available notification service which allows you to send push notifications from the cloud
  - Variety of message formats supported: SMS text message, email, Amazon Simple Queue Service (SQS) queues, any HTTP endpoint.
  - Pub-Sub model whereby users subscribe to topics
  - It is a push mechanism, rather than a pull(poll) mechanism.
### SES Vs SNS
  - SES is for email only
  - It can be used for incoming and outgoing mail
  - It is not subscription based, you only need to know the email address
  - SNS supports multiple formats (SMS, SQS, HTTP, Email)
  - Push notifications only
  - Pub/Sub model: consumers must subscribe to a topic
  - You can fan-out messages to large number of recipients (e.g., multiple clients each with their own SQS Queue)
  
# Kinesis 101
  - Streaming Data => Data that is generated continously by thouands of data sources, which typically send in the data records simultaneously, and in small bytes (KB). (e.g., think purchases from online stores - amazon, stock prices, Game data etc) 
  - Kinesis is a platform on AWS to send your streaming data too. Kinesis makes it easy to load and analyze streaming data, and also providing the ability for you to build your own custom applications for you business needs.
  - 3 core Kinesis Services
    - 1. Kinesis Streams
      - Data comes from sources like EC2, Mobile, PC, IOT
      - it stores the data in __Shards__ (Duration: 24hours (default) ~ 7 days)
      - then used for calculation (EC2) then stored (S3, EMR, Redshift, DynamoDB)
        - Shards => Kinesis Streams consists of Shards.
	- Total Capacity of Stream = Sum of capacities of its shards
    - 2. Kinesis Firehose
      - Automatted way. Analyzed using Lambda. Then send to S3. NO duration like Streams to store, it will send as soon it analyze or receive.
      - Analyzing the data, Automatically using lambda, not having to worry about consumers
    - 3. Kinesis Analytics
      - Run SQL queries on Streams / Firehose. 
      - Then send the results of SQL to S3 / Redshift / Elasticsearch Cluster
      - In general, Analyzing the kinesis using way like SQL Querying
      
# ElasticBeanStalk 101
  - Like CloudFormation (JSon format - Scripting your environment) But ElasticBeanStalk is GUI based (provisioning resources)
  - Deploys and scales web application
  - Support widely used programming like JAVA, .Net, PHP, Python, Ruby, GO, Docker, Node.js
  - Application server like Tomcat, Passenger, Puma, IIS
  - Provisons underlying services for you
  - Manage EC2 instances and admistrative control
  - Updates, Monitoring, metrics and health checks all included
  - 4 Deployment Approaches:
    - 1. All At Once
      - Service Interruption while you update the entire environment at once
      - To roll back, perform a further all at once Upgrade
    - 2. Rolling
      - Deploys the new version in batches. (e.g., 2 instances taken out of service from 8 instances while deployement then next 2)
      - Not ideal for performance sensitive systems
      - Reduced capacity during deployment
      - To roll back, perform a further rolling update      
    - 3. Rolling with Additional Batch
      - Launches an additional batch of instances then deploy new version in that batches
      - Maintains full capacity
      - to roll back, perform a further rolling update
    - 4. Immutable
      - Deployes the new version to a fresh group of instances. Once passed health check then old instances are terminated and new moved to existing auto scaling group.
      - Preferred option for mission critical production systems
      - Maintains full capacity
      - To roll back, just delete the new instances and autoscaling group
  - Lab: refer 'Deployment policy' under 'Configuration' (ElasticBeanStalk >> --Application-- >>)
### Advanced ElasticBeanStalk
  - Can customize your Elastic Beanstalk environment by adding configuration files
  - The files are written in YAML or JSON
  - Files have .config extension
  - The .config files are saved in the .ebextensions folder
  - Your .ebextensions folder must be located in the top level directory of your application source code bundle
### RDS & Elastic Beanstalk
  - 2 options for launching RDS instance:
  - 1. Launch within EBS (From EBS console)
    - when you terminate the EBS env, the DB will also be terminated
    - Quick and easy to start & Suitable for Dev and Testing env only
  - 2. Launch outside of EBS (From RDS console)
    - Additional configuration steps required - Security Group and connection information
    - Suitable for Production Env
    - Allow connection from multiple environments, you can tear down the application stalk without impacting the db

# CI/CD
  - CI => is about integrating or merging the code changes frequently at lease once per day, enables multiple devs to work on the same application.
  - C Delivery => is all about automating the build, test and deployment functions. (however manual intervention is required for deployment to start)
  - C Deployment => fully automates the entire release process, code is deployed into Production as soon it has successfully passed thourgh the release pipeline.
  - AWS CodeCommit => Source control service (git)
  - AWS CodeBuild => compile source code, run tests and package code
  - AWS CodeDeploy => Automated Deployment on EC2, on premises systems and Lambda
  - AWS CodePipeline => CI/CD workflow tool, fully automates the entire release process (build, test, deployment)	

### CodeCommit 101
  - AWS CodeCommit
    - based on Git
    - Centeralized repository for all your code, binaries, images, and libraries.
    - Track and manages code changes
    - Maintains version history
    - Manages updates from multiple sources and enables collaboration
### CC Lab
  - ??
### CodeDeploy 101
  - Fully Automated deployment service
  - 2 types
    - 1. In-Place or Rolling Update
      - You stop the application on each host and deploy the latest code.
      - EC2 and on premise systems only (not for lambda).
      - To roll-back, you must re-deploy the previous version of the application.
    - 2. Blue/Green
      - Brand new instances are provisioned and the new application is deployed to these new instance.
      - Traffic is routed to the new instances according to your own schedule.
      - Supported for EC2, on-premise systems and Lambda functions.
      - Roll back is just route the traffic back to the original instances.
      - Blue => Active Deployment, Green => New release.
### CD Lab
  - ??? revisit LAB - billing?
### CodePipeline 101
  - Continuous Integration / Continuous Delivery Service
  - Automates your end-to-end software release process based on a user defined workflow
  - Can be configured to automatically trigger your pipeline as soon as a change is detected in your source code repository
  - Integrates with other services from AWS like CodeBuild and CodeDeploy, as well as third party and custom plug-ins.
### CP Lab
  - ??
### Advanced CodeDeploy the AppSpec File
  - The AppSpec file defines all the parameters needed for the deployment. e.g. location of application files and pre/post deployment validation tests to run
  - For EC2/On premises Systems, the appspec.yml file must be placed in the root directory of your revision (the same folder that contains your application code). Written in YAML 
  - Lambda Supports YAML or JSON
  - The run order for Hooks in a CodeDeploy Deployment:
    - BeforeBlockTraffic -> BlockTraffic -> AfterBlockTraffic
    - ApplicationStop
    - BeforeInstall
    - Install
    - AfterInstall
    - ApplicationStart
    - ValidateService
    - BeforeAllowTraffic -> AllowTraffic -> AfterAllowTraffic
    
### Docker and CodeBuild Lab1 -- ???
  - Docker commands to build, tag (apply an alias) and push your Docker image to the ECR repository.
    - docker build -t myimagerepo
    - docker tag myimagerepo:latest 72345009400.dkr.ecr.eu-central-1.amazonaws.com/myimagerepo:latest
    - docker push 72345009400.dkr.ecr.eu-central-1.amazonaws.com/myimagerepo:latest
  - Use buildspec.yml to define the build commands and settings used by CodeBuild to run your build
  - you can override the settings in buildspec.yml by adding your own commands in the console when you launch the build
  - If your build fails, check the build logs in the CodeBuild console and you can also view the full codeBuild log in the CloudWatch
  
### CloudFormation
  - it allows you to manage, configure and provision AWS infrastructure as code (YAML/JSON)
  - Main Sections in the template:
    - Parameters => input custom values
    - Conditions => e.g., provision resources based on environment
    - Resources => Mandatory - the AWS resources to create
    - Mappings => create custom mappings like Region: AMI
    - Transforms => reference code located in S3 e.g., Lambda code or reusable snippets of CloudFormation code.
### CF Lab
  - ???
### Serverless Application Model (SAM)
  - Allows you to define and provision serverless applications using cloudFormation
  - Uses the SAM CLI commands to package and deploy:
    - sam package => packages your application and uploads to S3
    - sam deploy => deploys your serverless app using CloudFormation
### Summary
  - https://d0.awsstatic.com/whitepapers/DevOps/practicing-continuous-integration-continuous-delivery-on-AWS.pdf

# Advanced IAM
### Web Identity Federation
  - Federation Allows users to authenticate with a Web Identity Provider (Google, Facebook, Amazon)
  - The user authenticates first with the Web ID Provider and receives an authentication token, which is exchanged for temporary AWS Credentials allowing them to assume an IAM role.
  - Cognito is an Identity Broker which handles interation between your applications and the Web ID provider (you don't need to write your own code to do this)
    - it provides sign-up, sign-in, and guest user access
    - Synces user data for a seamless experience across your devices
    - Cognito is the AWS recommended approach for Web ID Federation particularly for mobile apps
    - Congnito User Pools
      - Cognito uses User pools to manage user sign-up and sign-in directly or via Web Identity Providers.
      - Cognito acts as an Identity broker handling all the interactions with Web Identity Providers.
      - Cognito uses Push synchronization to send a silent push notification of user data updates to muliple device types associated with a user ID.
### Cognito Lab
  - ???
### Inline Policies Vs Managed Policies Vs Custom Policies
  - 3 different Types
    - 1. Managed Policy => AWS managed default policies (READ only)
    - 2. Customer Managed policy => Managed by you (can be EDITED)
    - 3. Inline POlicy => Managed by you, and embedded in a single user / group / role. (one to one relationship, deleted along when the user /group/role is deleted)
  - In most cases, AWS recommends using Managed Policies over inline Policies.
  

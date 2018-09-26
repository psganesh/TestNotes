# Blue Print
  - Ability to write code using AWS security best practices (e.g., not using secret and access keys in the code,instead using IAM roles)

# (from old course)-----************************------BEGIN

# AWS Global Infrastructure - Exam Tips
  - Understand the difference between a region, an Availability Zone (AZ) and an Edge Location
  - A REGION is the physical location in the world which consists of 2 or more Availability Zones (AZ's) (E.g.: London)
  - An AZ is one or more discrete Data Centers, each with redundant power, networking and connectivity, housed in separate facilities.
  - Edge Locations are endpoints for AWS which are used for caching content. Typically consists of CloudFront, Amazon's Content Delivery Network. (NY <-> Melbourne, caching to nearest (Sydney) when accessing 2nd time it will be accessed from sydney).

# AWS Platform Components

# Compute *
- EC2 (Elastic Compute Cloud) – vm in AWS platform
- EC2 container service - this is where you manage & run docker container at scale
- Elastic BeanStalk - (developer who dont understand AWS, they will just upload code to this) then it provision things like auto Scaling groups, Load balancing, EC2 instance and etc
- Lambda - code - upload into cloud and control it. eg. lambda function will be triggered if any image is uploaded and text will be writing on top (overlay) of it using lambda.
- Lightsail – Virtual private service, provisioning a server with fixed IP address (RDP access for windows, SSH for Linux) - Control through Management console - Like lower version of EC2 :)
- Batch –  Batch computing in cloud 

# Storage *
- S3 – simple storage service, object based stored, Files will be stored into bucket
- EFS – Elastic File System -  Network attach storage - store into volume and mounted to multiple machines
- Glacier – Data Archival - for eg. need once in a year - cheap
- Snowball – way to bring in large data into data center 
- Storage Gateway – Virtual appliance, replicates info back to S3 - 4 types

# Database *
- RDS – Relational Db service, mysql, postgress, oracle 
- DynamoDB – Non relational 
- Elasticache -  caching data - for Eg. to store top 10 products in cache rather than to pull from DB using web service - it free up the DB to run the other queries.
- Red Shift – Data Warehousing or BI - here run complex query (lot time complete, joins & etc) for analysis (for eg. mgmt want to know profit and loss)

# Migration 
- AWS Migration Hub – track your application as you migrate to AWS and integrate with other services within migration framework
- Application Discovery service - Automated discover the dependencies. Eg: sharepoint or dependency with DB
- Database migration service - for eg: On premises DB into AWS
- Server migration service - for eg: server to migrate to AWS
- Snowball - migrate TB data into AWS

# Networking & Content Delivery*
- VPC – virtual private cloud.  Configure your own private cloud (firewall, AZ, N/W side IP range, route tables and etc)
- CloudFront – CDN,  stores your image/video closer to your AZ, edgelocation
- Route53 – DNS service 
- API Gateway – Create own API to talk to other services
- Direct Connect – direct line from hdq to amazon cloud / VPC

# Developer Tools 
- CodeStar – collaborating code
- CodeCommit – store code. Version controller. Store GitHub repository
- Code Build - Compile then run tests then produce software packages ready to deploy
- Code Deploy - Automate deployment process into EC2 instances
- CodePipeline - Continuous Delivery service
- X-Ray - debug the application
- Cloud9 – IDE, inside web browser

# Management Tools*	
- Cloud watch – Monitoring service
- Cloud formation – Turning your infrastructure into code (script)
- CloudTrail – log the changes in the AWS env. (default turned on for 1 week records)
- Config – monitor the configuration, visual (eg: how on May 4th and 6th)
- OpsWorks - like EBS, automating (configuring) the env
- Service Catalog - used by Big companies for Compliance
- Systems Manager – Managing AWS resources (EC2). Eg. patch maintenance - roll-out patch to 1000 of EC2 instances. Group the resources.
- Trusted Advisor – advice security (eg. port open), risks, capacity 
- Managed services - No need to worry about EC2, Scaling and etc., it helps - New service

# Media Services
- invented into 2017 (new)
- Elastic Transcoder – (old service) resize video to android /ios
- MediaConvert - File based media transcoding service
- MediaLive - Live video processing service
- MediaPackage - protects from Internet
- MediaStore - store service
- MediaTailor - 

# Machine Learning 
- Sagemaker – 
- Comprehend 
- Deeplens – physical hardware – camara
- Lex
- Machine learning 
- Polly – text to voice 
- Rekognition – upload image / video, will tell you what it is
- Amazon translate – translator
- Amazon Transcribe – speech recognition – speech to text  

# Analytics *
- Athena - run SQL queries against S3 bucket. (report excel)
- EMR – big data solution. To process large data 
- Cloudsearch 
- ElasticSearchService
- Kinesis – bigdata, ingesting large amount of data into cloud (eg tweets # hash tag)
- Kinesis Video Streams - 
- Quicksight – BI tool
- Data Pipleline – moving the data bw diff amazon services
- Glue – used for ETL

# Security & Identity & Compliance *
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

# Mobile Service 
- Mobile Hub – management console for mobile apps, 
- PinPoint – push notifications to mobile users
- AWS Appsync – automatically updates the data (offline).  
- Device Farm - testing apps in real devices
- Mobile Analytics

# AR / VR 
- Sumerian – code name 

# Application Integration*
- Step functions - way of managing diff Lambda function
- Amazon MQ
- SNS – Notification service (eg. if bill reaches 10$ then notification will be sent to your phone)
- SQS - Simple Queue service. Decoupling infrastructure. Queue -> EC2 (for processing), in case EC2 is died the queue still has request data.
- SWF – Simple Workflow Service 

# Customer Engagement 
- Amazon Connect
- SES - Simple Email Service 

# Business Productivity 
- Alexa for Business 
- Chime – Video conference like xoom / Google handout
- Work Docs - like drop box
- WorkMail – like office 365

# Desktop and App Streaming 
- Workspaces - VDI solution - literally run OS
- AppStream 2.0 - like citrix 

# IOT
- IOT device management 
- Amazon FreeRtos – OS for micro controller 
- GreenGrass 

# Game Development
- GameLift - to develop VR games in cloud

# (from old course)-----************************------END


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
  
# ***************** OLD COURSE **********************-- Beg
# STS – Security Token Service
- Grants users limited & temp access to AWS resources
- Federation – SAML, AD, Single sign on 
- Federation Mobile – FB, amazon, google or openId to login
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
# ***************** OLD COURSE **********************-- End


# EC2 (Elastic Compute Cloud)
  - VM - Pay only for capacity that you actually use
  - Pricing Options:
    - On Demand Instance
      - Fixed rate by the hour or second with no commitment (linux by second & Windows by hours now)
      - who want low cost, no upfront payment & longterm commitment, flexible, short term, unpredictable workload, first time
    - Reserved Instance
      - contract with AWS, 1 or 3 years terms reserve - significant discount on the hourly charge
      - steady state or predictable usage appl, reserved capacity
      - Standard RIs (upto 75% off ondemand), Convertible RIs (upto 50%) - change reservations, Scheduled RIs (within timewindow, requires for a day/week/month, eg: every weekend / friday)
    - Spot Instance 
      - to bid price (assume, share market price variation) - greater saving if flexible start & end times (eg: 4am on sunday morning)
      - eg. Bid at 100$. if spot price goes down to 90$ then no issue (provisioned). if 110$ then those instances will be terminated.
      - If amazon terminates the instance (bid range), you don’t have to pay (not charged for partial hour)
      - If you terminate the instance, you will be charged for the complete hour in which the instance ran.
    - Dedicated Hosts 
      - physical EC2 dedicated for use. use existing software licenses.
      - not support multi-tenancy or cloud deployments
      - can be purchased on Demand (hourly), as reservation (upt 70% off ondemand)
  - EC2 Instance Types
    - FIGHT_DR_MC_PX !!!!!!!!!!
      - F -> Field Programmable Gate Array (FPGA) => Genomics research, Financial analytics, real time video processing, big date & etc
      - I -> High speed Storage (IOPS) => NoSQL DBs, Date Warehousing etc
      - G-> Graphics Intensive => Video Encoding / 3D Application Streaming
      - H -> High Disk Throughput => MapReduce-based workloads, distributed file systems such as HDFS & MapR-FS
      - T -> cheap general purpose (think T2 Micro) => Webservers / small DBs
      - D -> Density Storage => Fileservers / Datawarehousing / Hadoop
      - R -> Memory optimised (RAM) => Memory Intensive Apps/DBs
      - M -> Main choice for general purpose apps => Application Servers
      - C -> Compute optimized => CPU Intensive Apps/DBs
      - P -> Graphics/General purpose GPU (think PICS) => Machine Learning, Bit coin mining etc
      - X -> Extreme Memory optimized => SAP HANA/Apache Spark etc

# EBS (Elastic Block Storage)
  - Virtual Disk, Storage volume attached to EC2 Instances. run DB or use like block device
  - Placed in a specific AZ. Automatically replicated to protect from failure
  - EBS attached with EC2 is called Root Device Volume. (eg. windows -> C: drive)
  - Types
    - General Purpose SSD (GP2)
      - General purpose, balances both price and perf.
      - Ratio of 3 IOPS per GB ~ 10,000 IOPS
      - burst upto 3000 IOPS for extended periods for vol 3334 GiB and above
     - Provisioned IOPS SSD (IO1)
       - I/O Intensive such as large relational or NoSQL DB
       - '> 10,000 IOPS (extreme perf)
       - ~ 20,000 IOPS per volume
     - Throughput Optimized HDD (ST1)
       - Low cost, Freq accessed, throughtput intensive workloads
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

# EC2 Lab (copied)
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

# Elastic Load Balancers
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

# Route 53 Lab
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
          - Load Balancers >> Create LB >> Applicaton LB >> Specify (Name: eg.MyALB, Scheme: Internet-facing, IPAddress Type: ipv4, Listeners: HTTP 80, HTTPS 443 if needed, AZ: All) >> Assign Security Groups (eg. MyWebDMZ) >> Configure Routing (Create Target group.eg> MyWebServerGroup. Note: Each target group to only one One LB, Specify Health Checks eg. index.html) >> Register Targets (Add to registered eg. already created EC2 instance) >> CREATE
   - imcloudguru.com -> ALB -> EC2 instance -> index.html ("Welcome to AWS world..!!!")

# CLI Demo Lab
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

# EC2 with S3 Role Lab
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
    - Roles are perferred from a security perspective
    - Roles are controlled by policies
    - You can change a policy on a role and it will take immediate effect
    - You can attach or detach roles to running EC2 instances without having to stop or terminate

# How to Encrypt an EBS volume
  - 1. Additional Volume ?
    - EC2 >> EBS >> Volume >> Create Volume >> Select Volume type (GP2), size 100 GB, AZ (same AZ where EC2 present).... SELECT Encryption, Selecte Master key (default - aws/ebs) >> Create colume
    - Actions >> Attach volume >> Select the EC2 instance >> Attach
    - Note: If you create volume from ENCRYPTED Snapshot, then the volume also will be encrypted.
    - Commands
      - ssh *** >> sudo su 
      - lsblk (=> it will show default attached with root '/' xvda & recently attached volume above xvdf)
      - file -s /dev/xvdf (=> check file system. Default: "/dev/xvdf: data" -> means no data in the volume and can proceed to create filesystem)
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
  - RDS - OLTP (Online Transaction Processing)
    - SQL, MySQL, PostgreSQL, Oracle, Aurora, MariaDB
  - DynamoDB - NoSQL
    - Database
      - Collection => Table
      - Document => Row
      - key value pairs => Fields
      (think JSON sample)
  - Redshift - OLAP (Online Analytical Processing)
  - Elasticcache - In Memory Caching:
    - 2 engines: Memecached
    - Redis
    
# RDS Lab
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
    
# RDS Multi-AZ and Read Replicas
  - 2 types of backups
    - Automated Backups
      - recover at any point of time within a "retention period" (1~35 days)
      - full daily snapshot. AWS will choose first the most recent daily back up. recovery down to a second    
      - enabled by default. stored in S3. free data storage 10GB RDS = 10GB S3 storage
      - Backups are taken on defined window. suspended during that time.
    - Database snapshots
      - Manual (user initiated). They are stored even after delete the original RDS instance, unlike automated backups.
  - Restoring backups => restored version of DB will be new RDS instance with new DNS endpoint (ie., orginal.eu-west-1.rds.amazonaws.com => restored.eu-west-1.rds.amazonaws.com)
  - Encryption
    - supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora.
    - done using AWS Key Management service (KMS).
    - once RDS instance is encrypted, data stored also encrypted.
    - At present, encrypting an existing DB instance is not supported. 
    - To use amazon RDS encryption for existing, 1. create snapshot 2. copy snaphot 3. encrypt the copy
  - Multi AZ
    - DR only. (US-EAST-1A <=> US-EAST-1B). Any change in 1A will be synchronizely replicated to 1B (diff AZ). If 1A is failed due to Disaster, then 1B will be pointed.
    - RDS is dealt with DNS (gane.xxxxxxx.eu-west-1.rds.amazonaws.com). if primary DB is failed, then the secondary IP address will be mapped with this DNS (during fail over).
    - not for improving performance. Only for DR.
    - SQL Server, Oracle, MySQL Server, Postgre SQL, MariaDB
  - Read Replicas
    - 5 Read replicas for production for default. New writes will be pushed to other replica DB.
    - allow you to have a read-only copy of your production DB. This is achieved by using Async replication from primary RDS instance to the read replica.
    - mainly for very read-heavy DB workloads.
    - MySQL Server, PostgreSQL, MariaDB, Aurora
    - used for SCALING, NOT for DR. Must have auto backup turned on in order to deploy a read replica. Upto 5 readreplica of any DB.
    - Read replica of Read replica is possible (but watch out for latency). Each read replica has its own DNS end point.
    - Can have RR that multi AZ. Can create RR of multi AZ source DB.
    - RR can be promoted to be their own DB. This breaks the replication. (For eg. if not using all RR for production, you can use for other DB purpose)
    - can have RR in a 2nd region.
# Elasticache 101
  - 

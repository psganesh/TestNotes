# Blue Print
  - Ability to write code using AWS security best practices (e.g., not using secret and access keys in the code,instead using IAM roles)

# (from old course)-----************************------BEGIN

# AWS Global Infrastructre - Exam Tips
  - Understand the difference between a region, an Availability Zone (AZ) and an Edge Location
  - A REGION is the physical location in the world which consists of 2 or more Availability Zones (AZ's) (E.g.: London)
  - An AZ is one or more discrete Data Centers, each with reduntant power, networking and connectivity, housed in separate facilities.
  - Edge Locations are endpoints for AWS which are used for caching content. Typically consists of CloudFront, Amazon's Content Delivery Network. (NY <-> Melborn, caching to nearest (sydney) when accessing 2nd time it will be accessed from sydney).

# AWS Platform Components

# Compute *
- EC2 (Elastic Compute Cloud) – vm in AWS platform
- EC2 container service - this is where you manage & run docker container at scale
- Elastic BeanStalk - (developer who dont understand AWS, they will just upload code to this) then it provision things like auto Scaling groups, Load balancing, EC2 instance and etc
- Lambda - code - upload into cloud and control it. eg. lambda function will be triggered if any image is uploaded and text will be writting on top (overlay) of it using lambda.
- Lightsail – Virtual private service, provisoning a server with fixed IP address (RDP access for windows, SSH for linux) - Control through Management console - Like lower version of EC2 :)
- Batch –  Batch computing in cloud 
# Storage *
- S3 – simple storage service, object based stored, Files will be stored into bucket
- EFS – Elastic File System -  Network attach storage - store into volume and mounted to multiple machines
- Glacier – Data Archival - for eg. need once in a year - cheap
- Snowball – way to bring in large data into datacenter 
- Storage Gateway – Virtual appliance, replicates info back to S3 - 4 types
# Database *
- RDS – Relational Db service, mysql, postgress, oracle 
- DynamoDB – Non relational 
- Elasticache -  caching data - for Eg. to store top 10 products in cache rather than to pull from DB using web service - it freeup the DB to run the other queries.
- Red Shift – Data Warehousing or BI - here run complex query (lot time complete, joins & etc) for analysis (for eg. mgmt want to know profit and loss)
# Migration 
- AWS Migration Hub – track your application as you migrate to AWS and integrate with other service
- Application Discovery service - Automated discover the dependencies. Eg: sharepoint or dependency with DB
- Database migration service - for eg: oracle DB to migrate to AWS
- Server migration service - for eg: server to migrate to AWS
- Snowball
# Networking & Content Delivery*

- VPC – virtual privacy cloud.  Configure your own private cloud
- CloudFront – CDN,  stores your image/video closer  to your AZ, edgelocation
- Route53 – DNS service 
- API Gateway – 
- Direct Connect – direct line from hdq to amazon cloud

# Developer Tools 

- CodeStar – colabrating code
- CodeCommit – store code. Version controller 
- Code Build
- Code Deploy
- CodePipeline
- X-Ray - debug
- Cloud9 – IDE, browser

# Management Tools*	

- Cloud watch – 
- Cloudformation – 
- CloudTrail – log the changes 
- Config – monitor the configuration, visual 
- OpsWorks 
- Service Catalog 
- Systems Manager – patch all the EC2
- Trusted Advisor – advice security, risks, capacity 
- Managed services 

# Media Sevices
- Elastic Transcoder – resize video to android /ios

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
- Athena
- EMR – big data solution. To process large data 
- Cloudsearch 
- ElasticSearchService
- Kinesis – bigdata, ingesting large amount of data in cloud
- Kinesis Video Streams
- Quicksight – BI tool
- Data Pipleline – moving the data bw to amazon services
- Glue – ETL

# Security & Identity & Compliance *
- IAM – Identify Access Management
- Cognito – Auth service, gives temp access to AWS
- GuardDuty – malicious activity
- Inspector – governance tool, check the vulnerability 
- Macie – scans S3 for PII data
- Certificate Manager – manage SSL 
- CloudHSM – Hardware security Module - stores encryption keys 
- Directory Service – integrating Active directory
- WAF – Web Application Firewall – prevent XSS, Sql injection
- Shield – prevent Ddos attacks 
- Artifact – compliance report, PCI report 
# Mobile Service 

- Mobile Hub – management console for mobile apps, 
- PinPoint – push notifications 
- AWS Appsync – automatically updates the data (offline).  
- Device Farm 
- Mobile Analytics 

# AR / VR 
- Sumerian – code name 
# Application Integration*
- Step functions
- Amazon MQ
- SNS – Notification service 
- SQS -  Decoupling 
- SWF – Simple Workflow Service 

# Customer Engagement 
- Amazon Connect
- SES - Simple Email Service 

# Business Productivity 
- Alexa for Business 
- Chime – Video conference like xoom
- Work Docs 
- WorkMail – like office 365

# Desktop and App Streaming 

-  Workspaces 
- AppStream 2.0 like citrix 

# IOT
-  IOT device management 
- Amazon FreeRtos – OS for microcontroller 
- GreenGrass 

# Game Development
- GameLift

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
    - 
  

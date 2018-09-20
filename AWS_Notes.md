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
      - (old notes) If you terminate the instance, you have pay for the partial hour
      - (old notes) If amazon terminate the instance (bid range), you don’t have to pay
    - Dedicated Hosts 
      - physical EC2 dedicated for use.
      - not support multi-tenancy or cloud deployments
      - can be purchased on Demand (hourly), as reservation (upt 70% off ondemand)
  - EC2 Instance Types
    - 
    

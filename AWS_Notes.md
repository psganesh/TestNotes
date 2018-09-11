# Blue Print
  - Ability to write code using AWS security best practices (e.g., not using secret and access keys in the code,instead using IAM roles)

(from old course)
# Exam Tips
  - Understand the difference between a region, an Availability Zone (AZ) and an Edge Location
  - A REGION is the physical location in the world which consists of 2 or more Availability Zones (AZ's) (E.g.: London)
  - An AZ is one or more discrete Data Centers, each with reduntant power, networking and connectivity, housed in separate facilities.
  - Edge Locations are endpoints for AWS which are used for caching content. Typically consists of CloudFront, Amazon's Content Delivery Network. (NY <-> Melborn, caching to nearest when accessing 2nd time).

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
  

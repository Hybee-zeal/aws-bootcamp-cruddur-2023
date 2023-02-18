# Pre-requisite technologies

We are required to have the following technologies set up, as they will be needed in the course of the bootcamp. These  includes:

- Create a Github account. We will create our own repo from Andrew's repository, using template, with the right formatting of the repo and must be public.
- Download a gitpod extension and then create a gitpod account. This way, the gitpod tab will appear on our github.
- Create github codespace
- Create an AWS free tier account, as we will be utilizing the free tier benefit to spin up resources as we progress in the bootcamp.
- Create a Lucidchat account. With this account, we can create an architectural design of the application we want to create. This will enable us explain our work to the   stakeholders.
- Create Honeycomb.io account.
- Create Rollbar account. This will enable us to capture application crashes and uncaught errors. 
- 
# Week 0 — Billing and Architecture
This week (week 0), we will be looking at billing, architecture and security.
Billing in aws varies across regions, so we will keep this mind as we choose a region to provision our resources. As advised by the instructor, we will try to stay within the free tier limit of our account (newly created accounts have free tier benefit for 12 months)

# Billing Alerts

There are 2 ways to set the billing alerts.

- Using Budget. This is simplest way to monitor your AWS spend and be alerted when you exceed or are forecasted to exceed your desired spending limit.
- Using Cloudwatch Alarm. In this case, you need to create an alarm . You can create up to 10 free cloudwatch alarms

# Free Tier
This section will show all the usage of your free tier. It will show all the services that are free for the next 12 months (starts counting from the registration date) and their usage and forecast. After 12 months, they are still some services that are always free. And also there is some service that is "Trial" which means that is available for a short period such as 30 days.

# Tags
Tags (are Key/Value pair) are useful when you want to know how your cost is allocated. For example, if your want to identify all the services you used under the tag environment: dev (for example).

# Cost Explorer
Cost explorer is a service which visualises, understands and manages your AWS costs usage over time. You can view data for up to the last 12 months, forecast how much you're likely to spend for the next 12 months, and get recommendations for what Reserved Instances to purchase. You can use Cost Explorer to identify areas that need further inquiry and see trends that you can use to understand your costs.

# Report
The section report allows for generating reports. there are some reports already created by AWS that you can use

Credit
This is the section where you submit the credit that you obtained during an event (for example after submitting a feedback questionnaire). And also it shows when the expiration date.

# AWS Calculator
This is a tool where you want to estimate the cost of one or more services. Useful when someone asks you to give an estimated cost of the service you are going to use. It enables you to have an estimate of the cost of the AWS services you intend to use.

## ARCHITECTURAL DIAGRAM

I will display the architectural diagram below, but before that, I will lists the requirements of the architecture

# Requirements
- Application using micro services
- The frontend is in JS and the backend is in Python
- Using api to communicate
- Authentication using Cognito
- Use as much as possible the aws free tier
- Momento as a third party caching system

![The Architectural diagram](assets/Cruddur%20-%20Conceptual%20Diagram.jpeg)

Kindly click on the url below to find the architectural diagram
(https://lucid.app/lucidchart/7c696a51-bc90-46ee-8439-4d69a6efa04a/edit?invitationId=inv_2c3aba1c-4acf-4740-a43e-1f1a45518685&page=0_0#)

# Security

The important thing when it comes to security. It is a best practice to always inform the business of the technical risk that can exist if  open vulnerabilities have not been resolved and can potentially affect the business and how will be solved.

## Definition of the cloud security
Cybersecurity protects data, applications and services associated with cloud environments from both external and internal security threats.

## Why care about cloud security
- Reducing the impact of the breach
- Protecting all the system (application, network etc) against malicious data theft
- Reducing the human error responsible for data leaks


## Cloud Security requires practice
- Understand the complexity of the system
- Always keep updated with the new services announced
- Bad hackers are constantly improving as well.


## Activate MFA for root account

Root user is the most powerful user in aws environment. It is considered security best practice not to use the root account for our daily task, we should instead     create an IAM user for such purpose


## AWS Organization
Create an organization unit (AWS Organization) AWS Organization allows you to create and manage multiple account. Also it allows to apply governance policies to     accounts or group. There are 2 approce to create the organization:

- Creating business unit (HR Ou, Finance Ou, Engineering Ou)
- Creating a Standby and Active Pool.
- 
SCP (Service Control Policy) are a type of organisational policy that you can use to manage permission in your organisation.

## AWS Cloud Trail

Auditing Service in AWS. Most all the api will be recorded in this service. Cloudtrail will record only the activity in the region you will operate. This service is not free

## IAM
Recommended to be used for our everyday tasks and can be created using the root account. It has 3 kinds of users:

- IAM user with user and password (make sure MFA is active as well as you activated on root account)
- Federated user are users federated from an on-premise environment without a password
- Web Token User

Always Give the least privilege to the users. Don't give more than what it is necessary. This is considered security best practice.

When you are working on AWS, it is a best practice to use the IAM user instead of the Root account. If for some reason the IAM user is compromised, it is simple to solve the problem by removing the policy attached to it/deleting the user himself.

Policies are assigned to either an IAM user or IAM role or IAM group and consist of what the entity can/can not do. For example, a policy could be the possibility to read the content of the s3 bucket.

Access Key and Secret Access key are similar to the user and password (keep it always secret). One reason you need to use it is for example you need to do some calls using CLI. Never hardcode this information on services that it is public expose (for example code on github with access key and secret access key) as bad actors could reuse those access to do bad actions (exploit your application and get sensible information or spin services)In some cases you need to use an IAM Role and attach it to a service or even a user. The difference between Iam user and Iam role is that IAM Role is for a short-term use while IAM User is used when long-term is desired.

# Shared Responsibility Model

Security in AWS cloud is considered a shared responsibility. It means both AWS and the customer both share in the security responsibilities. AWS is responsible for security of the cloud, while the customer is responsible for security in the cloud.

# AWS CLI

There are 2 ways to access the AWS via the CLI. One is installing the aws CLi from you terminal and after providing the secret key, secret access key and the region where you will call the api.

Another way is to use cloudshell from your the aws console. Note that not all the region are available for this functionality. Please check the icon close to the name of you IAM User.

A proof that I configured my AWS CLI can be found in the image below

![AWS CLI](assets/Screenshot%202023-02-18(caller-identity).png)


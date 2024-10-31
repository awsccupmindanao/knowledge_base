---
title: Backbone of AWS
---

<!-- <h2 align="center">Strengthen Your AWS Account: Security 101 with IAM</h2> -->

<img alt="AWS Workshop Banner" width="1412" src="img/banner.png">

<h1 align="center" style="border-bottom: none; ">Amazon Cloud Compute Workshop: Backbone of AWS</h1>

<p align="center">
    <a href="https://www.facebook.com/awscc.up"><img src="https://img.shields.io/badge/Facebook-@awscc.up-blue?logo=facebook&style=for-the-badge"></a>
    <a href="https://www.instagram.com/awscc_upmin/"><img src="https://img.shields.io/badge/Instagram-@awscc__upmin-E4405F?logo=instagram&style=for-the-badge"></a>
    <a href="https://www.linkedin.com/company/awscc-upmin"><img src="https://img.shields.io/badge/LinkedIn-@awscc--upmin-0077B5?logo=linkedin&style=for-the-badge"></a>
</p>

## **Table of Contents**

- [**Table of Contents**](#table-of-contents)
- [**Workshop Overview**](#workshop-overview)
- [**Prerequisites**](#prerequisites)
- [**Workshop Elements**](#workshop-elements)
  - [History of AWS](#history-of-aws)
  - [AWS Architecture](#aws-architecture)
  - [EC2 and its Pricing](#ec2-and-its-pricing)
  - [Creating an Instance](#creating-an-instance)
  - [Creating an Instance using AWS CLI](#creating-an-instance-using-aws-cli)
  - [Instance Connect](#instance-connect)
  - [Security Groups](#security-groups)
  - [S3 and IAM with EC2](#s3-and-iam-with-ec2)
  - [EC2 Amazon Machine Image](#ec2-amazon-machine-image)
  - [Elastic IP](#elastic-ip)
  - [Elastic Block Storage](#elastic-block-storage)
  - [Creating a load balancer](#creating-a-load-balancer)
  - [Auto Scaling Group](#auto-scaling-group)

## **Workshop Overview**

In this workshop, you'll gain a deep understanding of **AWS Elastic Compute Cloud (EC2)**, with a focus on launching and managing EC2 instances. Through hands-on activities, you'll learn to configure and secure your EC2 environments, manage instance types, and optimize performance for your applications.

By the end of the session, you will have the skills to effectively deploy, manage, and scale EC2 instances, ensuring high availability, security, and cost-efficiency in your AWS infrastructure.

## **Prerequisites**

Ensure you have the following tools installed before starting:

- **Windows Subsystem for Linux (WSL)**: [Install WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
- **AWS CLI v2**: [Install AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- **AWS IAM User with Admin Access:** [Create an IAM User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)

## **Workshop Elements**

### [History of AWS](00%20-%20History%20of%20AWS.md)

This section covers the Emergence of Cloud-Based Services.

### [AWS Architecture](01%20-%20AWS%20Architecture.md)

Explore and know how the AWS provides a vast and scalable cloud platform that enables companies to deliver services globally. Key points include:

- **AWS Global Infrastruture**: This tackles regions and availability Zones along with its purpose, usage and exaples.
- **Core AWS Services**: Compute services as the backbone for processing power on AWS, Storage, Networking, Databses, Content Delivery, Security, Elasticity & sclaing, and Serverless architecture and their importance to AWS Architecture.
- **Key Benefits of AWS Global Architecture**

### [EC2 and its Pricing](02%20-%20EC2%20and%20its%20Pricing.md)

Understand the Amazon Elastic Compute Cloud (Amazon EC2) along with it features. This will cover also the different pricing for related services.

### [Creating an Instance](03%20-%20Launching%20your%20own%20instance.md)

Learn the steps in launching your first EC2 instance. The following will serve as the primer to your journey:

- **Guide to Launching Your First EC2 Instance**: Detailed instructions on setting up new AWS accounts.  
  
### [Creating an Instance using AWS CLI](04%20-%20Creating%20an%20ec2%20instance%20using%20aws%20cli.md)

- Making an EC2 Instance using AWS CLI, the way to interact with AWS services programmatically, this guide also gives you the guide to Create Access Keys in the Management Console .

### [Instance Connect](05%20-%20All%20About%20Connecting%20to%20an%20Instance.md)

This will give you an understanding regarding the access to a server in the cloud, allowing administrators and developers to manage, configure, and maintain the infrastructure remotely. This module includes:

- **What is key pair?**: Vital to secure access to your Amazon EC2 instance.
- **How the Key Pairs Work in SSH**: Demonstration of user and host key pairs.
- **SSH Handshake and its benefits**
- **Connecting to your instance**: steps to connect after launching EC2 instance.

### [Security Groups](07%20-%20Security%20Group.md)

Know the role of security groups in EC2 instances and the best practices for using one along with Understanding IP addresses.

- **Apache Web Server Setup on EC2 instace**

### [S3 and IAM with EC2](09%20-%20Adding%20files%20to%20an%20instance.md)

Understanding what is Amazon S3 and IAM role and its relation EC2 isntance.

- **Guide to Adding files to EC2 instance**

### [EC2 Amazon Machine Image](10%20-%20Making%20an%20Image%20of%20the%20instance.md)

Discover Amazon Machine Image as a requirement to set up and boot an Amazon EC2 instance.

- **Creating a Pre-built AMI from an Instance**: Steps to create a pre-built AMI with the image captured from our instance.

### [Elastic IP](11%20-%20Elastic%20IP.md)

Introduction to Elastic IP with its Key Features and Benefits, security access, cost and tagging, and regional availability.

- **Setting Up an Elastic IP**

### [Elastic Block Storage](13%20-%20Storage%20in%20EC2.md)

Explore the range of EC2 storage available particularly understanding what is EBS and EFS. The following includes in this section:

- **Storage in EC2**: Storage options can be used independently or in combination.
- **EBS volumes**: It's the storage volumes that you attach to Amazon EC2 instances.
- **EBS snapshots**: The backups of Amazon EBS volumes.
- **EBS volume types**:
- **Features and benefits of Amazon EBS volumes**
- **Elastic File System (EFS)**: 'for limux instance'
- **EBS Lifecycle Manager**: This is for the automation of the creation, retention, and deletion of EBS snapshots and EBS-backed AMIs.
- **Expanding an EBS Volume**: Steps to expand the EBS volume and the file system on the EC2 instance.
- **Configuring an Elastic Load Balancer with Multiple Instances**: This is the guide in setting up an (ELB) with three EC2 instances that provide slightly different outputs.

### [Creating a load balancer](15%20-%20Elastic%20Load%*20Balancer*.md)

- This part will walk you through the process of setting up an Elastic Load Balancer (ELB) with three EC2 instances that provide slightly different outputs. This setup will help demonstrate how load balancing works by distributing traffic across the instances.

### [Auto Scaling Group](17%20-%20EC2%20Auto%20Scaling.md)

This will help in ensuring the correct number of Amazon EC2 instances available to handle the load for an application. Key points include:

- **Creating a launch template**: Best practices for attaching and managing policies.
- **Create ASG using launch configurations**: Best practices for attaching and managing policies.
- **Scaling Methods**: Several ways to scale Auto Scaling group.
- **Challenges of using EC2 Auto Scaling**'

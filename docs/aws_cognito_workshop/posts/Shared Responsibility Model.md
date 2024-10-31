---
date: 2024-08-27
---

# **AWS: Shared Responsibility Model**

The **_AWS Shared Responsibility Model_** is a foundational concept in cloud security. It defines the division of security responsibilities between AWS and its customers, ensuring both parties contribute to a secure cloud environment.

<!-- more -->

![](img/AWS%20Shared%20Responsibility%20Model.png)

## **Customers: Security _in_ the Cloud**

Customers are responsible for the security of everything that they create and put *in* the AWS Cloud.

- Data Control: Deciding which data to store in AWS, managing permissions, and ensuring proper access controls.
- Configuration Management: Configuring and managing security settings for AWS services, including Identity and Access Management (IAM) policies.
- Data Protection: Implementing measures such as encryption, backup, and compliance with relevant regulations.
- Application Security: Ensuring the security of applications, including patch management and application-level encryption.

## **AWS: Security _of_ the Cloud**

AWS is responsible for securing the infrastructure that runs all of the services offered in the AWS Cloud. This includes:

- AWS operates, manages, and controls the components at all layers of infrastructure. This includes areas such as the host operating system, the virtualization layer, and even the physical security of the data centers from which services operate.
- AWS is responsible for protecting the global infrastructure that runs all of the services offered in the AWS Cloud. This infrastructure includes AWS Regions, Availability Zones, and edge locations.
- Infrastructure Security: Managing the physical security of data centers, including hardware, software, networking, and facilities.
- Service Availability: Ensuring the resilience and redundancy of the global infrastructure, including AWS Regions, Availability Zones, and edge locations.
- Operational Security: Protecting the underlying infrastructure through robust security measures, such as intrusion detection systems and regular audits.

[Next >> Creating AWS Account](Creating%20AWS%20Account.md)

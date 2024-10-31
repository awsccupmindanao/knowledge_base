# **AWS Identity and Access Management**

## **Introduction**

**AWS Identity and Access Management (IAM)** is a fundamental service in AWS that allows you to control access to AWS resources securely. This workshop will guide you through the key features of IAM, how they work, and best practices for implementing IAM in your AWS environment.

>IAM enables the creation and management of users, user groups, and permissions for AWS services. It also supports integration with third-party solutions, facilitating the management of federated users, which allows external users to access AWS resources securely.

## **IAM Identities**

### IAM Identities: IAM Users

An AWS Identity and Access Management (IAM) user is an entity that you create in AWS to represent a human user or a workload that interacts with AWS. Each IAM user has a name and credentials, and there are several ways to manage and use these credentials:

- Friendly Name: This is the name you specify when creating the IAM user, visible in the AWS Management Console.  
- Amazon Resource Name (ARN): A unique identifier used to specify the IAM user across all of AWS, useful in IAM policies.  
- Unique Identifier: Returned when creating the IAM user via API, CLI, or Tools for Windows PowerShell. 

>Default limit is 5,000 IAM Users per account. You can request an increase if needed.  

**Permissions**:

* **Default:** No permissions initially; must be granted via IAM policies.  
* **Permissions Boundary:** Limits maximum permissions.  
* **Account Association:** No separate payment method needed; all activities billed to the account.  
* **Service Accounts:** Use IAM users with credentials for AWS requests; avoid embedding keys in code; prefer temporary credentials (IAM roles).

### IAM Identities: IAM Groups

An IAM Group is a collection of IAM users that simplifies the management of permissions. Instead of assigning policies individually to each user, you can attach policies to groups, and all users within that group will inherit those permissions.

**Key Points**

* **No Nested Groups:** AWS IAM does not support nested groups. Groups can only contain users, not other groups. However, users can belong to multiple groups. For example, a user who is both a developer and an artist could be part of separate groups like Developers and CreativeTeam.  
* **Centralized Management:** Manage permissions for multiple users collectively from a single location.  
* **Inheritance:** Users in a group automatically inherit the permissions assigned to the group.  
* **Scalability:** Streamlines permissions management as teams expand or change.

### IAM Roles

Roles offer a way to _**grant temporary access**_ to AWS resources without relying on **permanent credentials**. This approach is especially useful for scenarios that require **short-term access** or adhere to best practices that discourage hardcoding credentials.

**Key Uses of IAM Roles**

- Secure Resource Access: Allow AWS services like EC2 to access other resources, such as S3 buckets, without storing credentials.  
- Cross-Account Access: Enable sharing of resources and permissions between different AWS accounts.  
- Role Chaining: Support sequential role assumption for varying levels of access and control.


**Structure of IAM Roles**

- Trust Policies: Specify which entities (users or services) are allowed to assume the role.  
- Permissions Policies: Define the actions the role can perform on AWS resources.  
- Permissions Boundaries: Set limits on the maximum permissions that the role can grant, ensuring adherence to the principle of least privilege.

### Policies

IAM Identities enables you to grant different levels of access to different identities, but how exactly do you manage the credentials attached and the access-level allowed? 

IAM policies are attached to identities. IAM Policies are JSON documents that define the permissions for API calls and entities, detailing effects, actions, resources, and conditions. They determine what controls are activated, as all controls are off by default. These policies are attached to identities, such as users, groups, and roles, to manage their permissions. IAM Policies are accessible through the AWS CLI, AWS SDKs, and the AWS Management Console.

**Policy Categories:**

- Identity-Based:

  - Inline: Directly attached to IAM identities.  
  - Managed: Reusable and attachable to multiple identities. Can be AWS-managed or customer-managed.

- Resource-Based: Attached to resources (e.g., S3 buckets), specify access controls directly on the resource.

## **Key Features of AWS IAM**

### **1. Fine-Grained Access Control**

IAM provides the ability to define precise permissions, allowing you to specify who can access particular AWS services and resources and under what conditions. This control is implemented through policies that define the actions that can be performed on specific resources.

* **Granular Permissions:** Control access at a detailed level by defining policies that specify allowed actions and resources.  
* **Conditional Access:** Set conditions for access, such as requiring requests to come from a specific IP range or requiring multi-factor authentication (MFA).

### **2. Delegating Access Using IAM Roles**

IAM roles allow you to delegate access to users or AWS services without needing to share long-term credentials. Roles provide temporary security credentials for users, applications, or services that need to perform actions in your AWS environment.

* **Temporary Credentials:** Roles grant short-term access, ideal for use cases like automated workflows, third-party applications, and cross-account access.  
* **Role Assumption:** Users or services assume a role to receive temporary credentials and access AWS resources as defined by the role's policies.

### **3. IAM Roles Anywhere**

IAM Roles Anywhere extends the ability to use IAM roles to workloads that run outside of AWS, such as on-premises or in hybrid and multicloud environments. This feature uses X.509 digital certificates for authentication.

* **External Access:** Workloads outside AWS can securely obtain temporary AWS credentials and access AWS resources.  
* **Consistency:** Use the same IAM roles and policies for both AWS-hosted and external workloads.

### **4. IAM Access Analyzer**

IAM Access Analyzer helps you manage and refine permissions by continuously analyzing access policies to ensure they adhere to the principle of least privilege.

* **Permissions Analysis:** Identify unused or excessive permissions and adjust them to align with best practices.  
* **Least Privilege:** Continuously refine permissions to ensure that users and services have the minimum access necessary.

[Next >> IAM Users](06%20-%20IAM%20Users%20and%20ARNs.md)
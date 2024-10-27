# All About Connecting to an Instance
An **EC2 instance** is a virtual server in Amazon's Elastic Compute Cloud (EC2) that provides scalable compute capacity. It allows users to run applications, host websites, or perform any kind of computation in the cloud without the need for physical hardware. The instance operates much like a physical computer, but it's managed and provisioned from the AWS platform. EC2 instances come with different configurations of CPU, memory, storage, and networking capacity, making them customizable for various workloads.

![image](https://github.com/user-attachments/assets/72381336-0487-4e50-bd12-56a605ac14c3)

### Why do we connect to an instance?
Connecting to an instance allows an access to a server in the cloud, allowing administrators and developers to manage, configure, and maintain the infrastructure remotely. By connecting, we can install and update software, troubleshoot issues, and monitor performance. It ensures that cloud-hosted services are secure and functions efficiently.

## Secure Shell (SSH)
EC2 supports different methods for connecting to instances using SSH, including direct connections using an SSH client or browser-based SSH connections using EC2 Instance Connect. SSH is widely used for securely connecting to remote servers, particularly Linux-based systems. Additionally, every connection attempt via SSH is logged, making it easier to audit and track who accessed the instance. This is especially important in environments with multiple users and instances.

### What is Key-pair?
A **key pair** is a set of two cryptographic keys—a **public key** and a **private key**—that work together to secure access to your Amazon EC2 instance.

![keypair](https://github.com/user-attachments/assets/085613dc-ceab-451e-a9ca-9098cb4d2bbf)

 It consists of:

**Public Key** - stored on the EC2 instance and can be shared publicly

**Private Key** - stored seccurely on your computer, ensuring that only authorize users can connect to the EC2 environment

These two keys work together to encrypt and decrypt data, enabling secure, password-free access to servers.

## SSH and Key-Pair
SSH (Secure Shell) uses public-key cryptography, a method of encryption that relies on two mathematically linked keys, known as a key pair: a public key (shareable) and a private key (secret). In SSH, two separate key pairs are involved—user key pair (client) and host key pair (server)—each with its own public and private key. This dual setup enhances mutual authentication and ensures a secure SSH connection between the client and server.

### How the Key Pairs Work in SSH
- **User (Client-Side Authentication) Key Pair:**
    - **Private Key:** Stored securely on the user's local machine. It is never transmitted or shared and is used to authenticate the user by digitally signing requests during the SSH handshake.
    - **Public Key:** Shared with the server to allow authentication. It is used by the server to validate the user’s private key during authentication.
      
- **Host (Server-Side Authentication) Key Pair:**
    - **Private Key:** Stored securely on the server. It is used to decrypt encrypted communications and is never exposed to the client.
    - **Public Key:** Provided to users when they first connect to the server. SSH clients store this public key and use it to verify the server’s identity in future sessions.

## SSH Handshake

The SSH Handshake is a foundational process in the SSH protocol that establishes a secure and authenticated connection between a client (your local machine) and a server (such as an EC2 instance). This handshake ensures that only trusted users and servers can access or communicate over the connection. It involves the use of key pairs, which play a crucial role in both authentication and encryption during the process. The client uses its private key to authenticate itself to the server, while the server presents its public key to verify its identity.

### Benefits
1. **Security** - The SSH handshake establishes key parameters, such as encryption algorithms, to ensure effective data exchange between the client and the server.
2. **Synchronization** - Ensures that both the client and server are ready to communicate securely, preventing issues such as data being sent too quickly or at an inappropriate time, which can disrupt the connection.
3. **Error Identification** - The handshake detects potential errors before establishing a secure connection, preventing data corruption.
4. **Setting Communication Parameters** - The SSH handshake establishes key parameters, such as encryption algorithms, to ensure effective data exchange.




## 4 Method of Connecting to an Instance
There are 4 ways of connecting to an instance. Amazon EC2 offers various methods for connecting to instances depending on the operating system of the instance and the user's needs. Each of these ways has distinct use cases, security mechanisms, and platform compatibility.
1. **EC2 Instance Connect**
2. **SSH Client**
3. **Remote Desktop Protocol (RDP)**
4. **Session Manager**

In this workshop, let us discuss the first three ways to connect to an instance.

![kio](https://github.com/user-attachments/assets/a623691a-7dc7-428b-9572-a473989a462c)

## Method 1: EC2 Instance Connect
Connecting via **EC2 Instance Connect** is a feature that enables a secure connection to your Linux instances over SSH. EC2 Instance Connect allows you to connect to your instance directly through your browser. It refers to the feature in Amazon Web Services (AWS) that enables users to connect to their EC2 instances using SSH through the AWS Management Console, without the need for a standalone SSH client. It allows you to use AWS Identity and Access Management (IAM) policies and users to control SSH access without needing to share or manage SSH keys. 

![ec2-instance-connect-endpoint drawio-1](https://github.com/user-attachments/assets/1ce280df-e62c-4905-9246-1dd0e492d898)

**Prerequisites for installing and using EC2 Instance Connect:**

1. **EC2 Instance Connect Package**: Ensure the EC2 Instance Connect package is installed on your EC2 instance.
2. **Network Accessibility**: Confirm that your instance is accessible over the network.
3. **SSH Traffic Configuration**: Adjust security group settings to allow incoming SSH traffic (TCP on port 22).
4. **User Permissions**: Make sure your IAM user has the necessary permissions to utilize EC2 Instance Connect.
5. **Correct Username**: Use the appropriate username based on the Linux distribution of your EC2 instance.

**Here are some of the usernames:**
 - **Ubuntu**: ubuntu
 - **Amazon Linux**: ec2-user
 - **CentOS**: root, centos or ec2-user
 - **Debian**: admin
 - **Fedora**: fedora or ec2-user
 - **RHEL (Red Hat Enterprise Linux)**: ec2-user or root
 - **SUSE**: ec2-user or root
 - **Oracle**: ec2-user
 - **Bitnami**: bitnami
 - **Rocky Linux**: rocky
 - **Others**
    
## Method 2: SSH Client
Connecting to an instance through **SSH Client** involves using encryption and key-pair authentication when connectung to EC2 Linux instances. This method enables us to associate with **key pair**.

![ACI4](https://github.com/user-attachments/assets/3a96205e-c757-447f-8668-24887320cb3c)

**Prerequisites for Connecting EC2 Instance Using SSH**

1. **SSH Key (.pem file)**: A private key used for authenticating your identity when connecting to the EC2 instance.
2. **IP Address**: The public address assigned to the EC2 instance, required to direct the SSH client to the correct server.
3. **Username**: The default login name for the specific Linux distribution on the instance, necessary for authentication. 

**Some SSH Usernames:**
 - **Ubuntu**: ubuntu
 - **Amazon Linux**: ec2-user
 - **CentOS**: centos
 - **BitNami**: bitnami
 - **NanoStack**: ubuntu
 - **Others**

## Method 3: Remote Desktop Protocol (RDP)
**Remote Desktop Protocol (RDP)** enables multiple users to connect to a window instances. Users can have separate sessions on the same server, allowing them to run different applications, access different files, and have their own desktop environments without interfering with each other’s work.

![ACI5](https://github.com/user-attachments/assets/cb20efaf-04d7-45a7-b7bd-9a20e49e9b8c)


**Prerequisite for Connecting Instance using RDP**

1. **RDP Client**: Install an RDP client (e.g., mstsc for Windows, Microsoft Remote Desktop for macOS, Remmina for Linux).
2. **Instance Details**: Have the IP address or hostname of the instance.
3. **Network Configuration**: Allow inbound RDP traffic on TCP port 3389 in your firewall/security group.


4. **Instance Status**: Ensure the instance is running and has passed status checks.
5. **Credentials**: Obtain the administrator password or domain credentials.
6. **Public IP Address**: Ensure the instance has a public IP if connecting over the internet.
7. **Authentication**: Set up any required authentication methods (e.g., IAM permissions).

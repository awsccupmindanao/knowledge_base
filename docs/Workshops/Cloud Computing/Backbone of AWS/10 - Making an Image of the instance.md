# What is AMI and Images?

An Amazon Machine Image (AMI) is an image that provides the software that is required to set up and boot an Amazon EC2 instance. Each AMI also contains a block device mapping that specifies the block devices to attach to the instances that you launch. You must specify an AMI when you launch an instance. The AMI must be compatible with the instance type that you chose for your instance. You can use an AMI provided by AWS, a public AMI, an AMI that someone else shared with you, or an AMI that you purchased from the AWS Marketplace.

## An AMI is specific to the following:

- **Region**  
  AMIs are tied to a specific AWS region (ie. ap-southeast-1) and are only available for launching instances in that region. You cannot directly use an AMI from one region in another region without copying it over.

- **Operating system**  
  An AMI is specific to the operating system that is installed on the root volume of the instance. This includes both Linux distributions (e.g., Amazon Linux, Ubuntu, Red Hat Enterprise Linux) and Windows Server AMIs.

- **Processor architecture**  
  AMIs are tied to specific processor architectures, such as x86 (64-bit, Intel/AMD architecture) or ARM (64-bit, AWS Graviton architecture). Instances launched from an AMI must be compatible with the processor architecture of the underlying hardware.

- **Root device type**  
  AMIs are either EBS-backed or instance store-backed, and the type of root device affects how the instance stores and retains data.
  - EBS-backed AMI: The root device is an Amazon EBS volume, which allows for persistent storage, meaning data remains even if the instance is stopped.
  - Instance store-backed AMI: The root device is an instance store volume, which is ephemeral, meaning data is lost when the instance stops or terminates.

- **Virtualization type**  
  AMIs support two types of virtualization: HVM (Hardware Virtual Machine) and PV (Paravirtual).
  - HVM: Instances launched from HVM AMIs are fully virtualized and take advantage of hardware-level features like enhanced networking, GPU access, and more. These instances are compatible with modern EC2 instance types.
  - PV: PV instances use paravirtualization, which is an older virtualization method that has lower performance compared to HVM. PV instances do not have access to the same hardware-level features as HVM.


![](img/AMI/AMI-01.png)

AMIs are the foundation for launching EC2 instances, and they provide a quick and efficient way to launch instances with pre-configured software and settings. This is throua a process called **Image Builder**.
By creating custom AMIs, you can capture the configuration of an instance and use it to launch identical instances in the future.

You can launch multiple instances from a single AMI when you require multiple instances with the same configuration. 

Image Builder is offered at no cost, other than the cost of the underlying AWS resources used to create store ang share the images.

## Creating a Pre-built AMI from an Instance

Now, we will try to create a pre-built AMI with the image captured from our instance. This AMI already had the downloaded web server, static HTML, and any files uploaded in our server.

### Steps to Create an Image of Your Instance

1. Go back to the instance page.
2. Right-click on the instance ID.
3. Navigate to **Image and templates > Create Image**.

![](img/AMI/AMI-02.png)

### Name Your Instance

- Save the image.

![](img/AMI/AMI-03.png)

![](img/AMI/AMI-04.png)

As you save the image, you will see that a snapshot is also made. When you create an AMI from an EC2 instance, AWS takes snapshots of all attached EBS volumes, enabling you to launch new instances with the same configuration and data. These incremental snapshots allow for version control, making it easy to manage changes and revert to previous states as needed.

### Check the State of Your AMI

- Go to AMI then check the state of your AMI by clicking the AMI ID.

![](img/AMI/AMI-05.png)

You have now successfully created an image of your instance. 

### Creating a New Instance from Your Image

Let’s try to create a new instance with our image.

1. Start with clicking **Launch Instance from AMI**.

![](img/AMI/AMI-06.png)

2. Just do **name of instance** - `<AMI1>`. For naming convention sake, this helps to properly track our AMIs.

![](img/AMI/AMI-07.png)

![](img/AMI/AMI-08.png)

As you can see, the AMI is already set from the image we captured from the first instance.

### Assign a Key Pair

![](img/AMI/AMI-09.png)

![](img/AMI/AMI-11.png)

- Select the security group we made from our first instance. This will ensure that the specific inbound rules are made for port 80 (HTTP), which will show our webpage in our public IPv4 address.

### Review the Summary of the Instance

- After all is done, launch the instance.

![](img/AMI/AMI-10.png)

**Congratulations!** You successfully made an instance from a captured image of an instance.

### Testing the Instance Configuration

Let’s test if the instance has the same configuration as the first, including the Apache web server and the static HTML.

1. Copy the IPv4 address.
2. Search in the internet as `http://<your IPv4 address>`.

![](img/AMI/AMI-12.png)

![](img/AMI/AMI-13.png)

As you can see, the webpage is the same as the first instance. This means that the image captured from the first instance was successfully created and launched as a new instance.

## Creating an Image from an Instance using AWS CLI

1. **Show all the instances in the region.**

```bash
aws ec2 describe-instance-status --include-all-instances --output table
```

Copy the instance ID of the instance you want to create an image from.

![](img/AMI/AMI-22.png)

In this case, we will use the instance ID of the first instance we created. Which for mine is `i-0a81ca23862089678`.

2. **Create an image from the instance.**

```bash
aws ec2 create-image \
    --instance-id i-0a81ca23862089678 \
    --name "alc-ec2-workshop-Image" \
    --description "An AMI of my web server instance" 
```

![](img/AMI/AMI-23.png)

3. **List all the images in the region created by you.**

```bash
aws ec2 describe-images --owners self
```

![](img/AMI/AMI-24.png)

4. **Verify the existence of the image on the AWS Console.**

![](img/AMI/AMI-25.png)

5. **Create a new instance from the image.**

- Use the Image ID of the image you created and follow this guide.

[Launch the EC2 Instance](03%20-%20Creating%20an%20ec2%20instance%20using%20aws%20cli.md#step-1-launch-the-ec2-instance)

### Connecting to the Instance

If you want to connect to the instance, you can do so by using the same steps as before.

1. Copy the ssh command from the SSH Client.

![](img/AMI/AMI-14.png)

2. Connect using the terminal. Paste the copied command and press enter.

![](img/AMI/AMI-15.png)

**What seems to be the problem?**  
- An AMI provided by AWS, the Amazon Linux AMI, has a default user of `ec2-user`. When we create an image based on this instance, the new instance will also have the same default user.  
Based on the ssh command we copied:

![](img/AMI/AMI-16.png)

- The username become root, this is because when creating an image from an instance, the default user is not copied over on the console of the SSH Client Connect. This is why we need to change the username to `ec2-user`.

![](img/AMI/AMI-17.png)


**Lets do some minor edits on our Apache webpage.**  

NOTE: This will be useful in the following sections.
\
- Go to the instance and edit the `index.html` file.

```
sudo -i
```

![](img/AMI/AMI-18.png)  

```
vim var/www/html/index.html
```

![](img/AMI/AMI-19.png)


- Let's add new details to the webpage.

![](img/AMI/AMI-20.png):

![](img/AMI/AMI-20-1.png)

save and exit file

```
:wq
```

- Verify the changes by refreshing the webpage.

![](img/AMI/AMI-21.png)

#### Cleanup:
- Remember to remove remove the image and the instances to avoid unnecessary charges.

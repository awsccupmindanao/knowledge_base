# Apache Web Server Setup on EC2 instace

## 1. Install the Apache Web Server
Apache is an open-source web server that processes HTTP requests and serves web content. Run the following command to install Apache:

```
sudo yum install httpd
```

![](img/LGWA/LGWA-01.png)

## 2. Start the HTTPD Service
The following command starts the Apache (`httpd`) service, allowing the web server to handle incoming requests:

```
sudo service httpd start
```

![](img/LGWA/LGWA-02.png)

## 3. Enable Apache to Start on Boot
To ensure Apache starts automatically during system boot, run the following command:

```
sudo chkconfig httpd on
```

![](img/LGWA/LGWA-03.png)

## 4. Switch to Root User
The command `sudo -i` allows a user to switch to the root user (the superuser) with full administrative privileges:

```
sudo -i
```

![](img/LGWA/LGWA-04.png)


## 5. Navigate to the Apache Web Directory
Navigate to the directory where Apache will look for the `index.html` file (the default directory):

```
cd /var/www/html
```

![](img/LGWA/LGWA-05.png)

## 6. Create an `index.html` Page
Create a simple `index.html` file:

```
touch index.html
```

Verify the file exists by listing the directory contents:

```
ls
```

![](img/LGWA/LGWA-06.png)

## 7. Edit the `index.html` File
Use `vim` or `nano` to add content to the `index.html` file:

```
vim index.html
# or
nano index.html
```
For vim: Do press `i` to enter insert mode and enter the following content:
```
Hello World!
```

![](img/LGWA/LGWA-07.png)


Save and exit the editor by pressing `Esc`, typing `:wq`, and pressing `Enter`.




## 8. Find Your Instance Public IPv4 Address
In the AWS EC2 console, click the instance ID to find its details. Copy the Public IPv4 address.

![](img/LGWA/LGWA-09.png)

## 9. Test the Web Server
Open a browser and navigate to:

```
http://<your-public-ipv4-address>
```

![](img/LGWA/LGWA-10.png)

**If the website is not accessible, this means that there is a problem with our security group settings. We need to modify the security group settings to allow incoming traffic on port 80 (HTTP).**

## 10. Modify Security Group Settings
Scroll down to the "Security" section, and click on your security group.

![](img/LGWA/LGWA-11.png)

![](img/LGWA/LGWA-12.png)

## 11. Edit Inbound Rules
Click **Edit Inbound Rules** to control incoming traffic to your server.

![](img/LGWA/LGWA-13.png)

## 12. Allow Incoming Traffic on Port 80
Add a rule to allow incoming traffic on port 80 (HTTP). Ensure that traffic is allowed from any IP address (making it publicly accessible over the web).

![](img/LGWA/LGWA-14.png)

![](img/LGWA/LGWA-15.png)

![](img/LGWA/LGWA-16.png)

Save the changes.

![](img/LGWA/LGWA-17.png)

## 12.1 Configuring Security Group using AWS CLI

1. **Describe the Security Group**:
   - Run the following command to describe the security group:

     ```bash
     aws ec2 describe-security-groups
     ```  
Find the security group ID that you want to modify. In our case, the security group name is `launch-wizard-1`.

![](img/LGWA/LGWA-20.png)

As you can see it already had permission to part 80 and port 22. Those are for HTTP and SSH respectively.

Find its security group ID, which is in my case is `sg-0c1b0b8939dd8ba1a`.

![](img/LGWA/LGWA-21.png)

copy this to a text file for later use.

press `q` to exit the output.

2. **Update the Security Group**:
   - What if we want to add a new inbound rule for HTTPS (port 443)? Run the following command:
  
 ```bash
aws ec2 authorize-security-group-ingress \
  --group-id <your-security-groupID> \
  --protocol tcp \
  --port 443 \
  --cidr 0.0.0.0/0
 ```

![](img/LGWA/LGWA-22.png)

3. **Verify the Changes**:
   - Run the following command to verify the changes:

     ```bash
     aws ec2 describe-security-groups
     ```

![](img/LGWA/LGWA-23.png)

4. **Also check using the AWS console if the changes are reflected.**

![](img/LGWA/LGWA-24.png)

## 13. Revisit the Public IPv4 Address
Visit your public IPv4 address in a browser again. Your Apache web server should now be accessible.

![](img/LGWA/LGWA-18.png)

## 14. Customize Your Website
For funsies, copy-paste your favorite static HTML website into this server and watch it run! Better if it had external pictures or videos to see if it works.

![](img/LGWA/LGWA-19.png)

This is mine, lets watch yours!  

## 15. What if I dont have a static website?
- We will provide you with a simple HTML template that you can use.

Copy paste this to vim


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>EC2 Instance</title>
</head>
<body>
    <h1>Instance 1</h1>
    <img src="path/to/your/image.png" ">
</body>
</html>
```

- Prepare some image for later use of the workshop.

As you can see, pictures and videos wont load. Let's solve that.



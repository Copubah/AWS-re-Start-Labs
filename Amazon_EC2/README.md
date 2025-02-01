# Amazon EC2
- Amazon EC2 (Elastic Compute Cloud) is a cloud-based service that provides scalable computing capacity in AWS. It allows you to launch and manage virtual servers, known as instances, in the AWS cloud. EC2 is commonly used for hosting applications, running workloads, and handling scalable cloud computing needs

## Key features
- Elasticity & Scalability – You can scale your compute capacity up or down based on demand.
- Multiple Instance Types – Offers a variety of instance types optimized for different workloads (e.g., general-purpose, compute-optimized, memory-optimized, storage-optimized).
- Flexible Pricing Models
- Security – Supports IAM roles, security groups, and encryption to protect your data.
- Auto Scaling – Ensures availability by automatically adjusting capacity.
- Elastic Load Balancing (ELB) – Distributes traffic across multiple instances.


## Preview 
- In this task, you will launch an Amazon EC2 instance with termination protection. Termination protection prevents you from accidentally terminating an EC2 instance. You will deploy your instance with a User Data script that will allow you to deploy a simple web server.



## Architecture diagram
![Amazon EC2](https://miro.medium.com/v2/resize:fit:828/format:webp/1*_U11fvM6VmurRCFcKqGSjg.jpeg)


## Steps
1. In the AWS Management Console on the Services menu, choose EC2 name it and launch it
2. Choosing an Amazon Machine Image (AMI),an AMI has different types of Operating systems like Amazon Linux 2 AMI
3. Choosing an instance type and Configure a Key pair
4. Configure the network settings including things like Security group name and a description
5. Under Inbound security groups rules select the "Remove button" (for this lab to disable SSH login )
6. Add storage if need be and configure the advanced details,select the dropdown for Termination protection, then choose Enable.
7. Copy the following commands, and paste them into the User data text box.
- #!/bin/bash
- yum -y install httpd
- systemctl enable httpd
- systemctl start httpd
- echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html

## The script does the following:
- Install an Apache web server (httpd)
- Configure the web server to automatically start on boot
- Activate the Web server
- Create a simple web page
8. Now that you have configured your EC2 instance settings, it is time to launch your instance

## Update Your Security Group and Access the Web Server
- Select the instance by checking the box and select the Details tab.
- Copy the Public IPv4 address of your instance to your clipboard.
- Open a new tab in your web browser, paste the IP address you just copied, then press Enter
- Keep the browser tab open, but return to the EC2 Management Console tab.
- In the left navigation pane, select Security Groups located under Network & Security.
- Select  Web Server security group.
- Select the Inbound rules tab;Select Edit inbound rules then select Add rule and configure the rule with the following settings:
     - Type: HTTP
    - Source: Anywhere-IPv4
    - Select Save rules
- Return to the web server tab that you previously opened and refresh

## Resizing your Instance: Instance Type and EBS Volume
- As your needs change, you might find that your instance is over-utilized (too small) or under-utilized (too large). If so, you can change the instance type. For example, if a t3.micro instance is too small for its workload, you can change it to an m5.medium instance

## Steps
- Stop your instance and wait for it to display "stopped"
- In the Actions  menu, select Instance Settings  Change Instance Type, then configure to your preference

## Resize the EBS Volume
- In the left navigation menu, select Volumes located under Elastic Block Store.
- Select the volume by checking the box, and navigate to the Actions  menu, select Modify Volume
- Start the Resized Instance

## Termination Protection
- In left navigation pane, select Instances.
- Select the Web Server instance by checking the box and navigate to the top and select Instance state  menu, select  Terminate instance.
- In the Actions  menu, select Instance settings  Change termination protection.
- Uncheck  Enable followed by Save,You can now terminate the instance.
- In the Actions  menu, select Instance State  Terminate instance.

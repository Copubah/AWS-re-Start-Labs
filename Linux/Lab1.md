# Use SSH to connect to an Amazon Linux EC2 instance
## Get the Key Pair (.pem file)
When launching an EC2 instance, AWS prompts you to create or select a key pair.
Download the .pem file and keep it secure. You'll need it to authenticate.
2️⃣ Change Key Permissions
Before connecting, set the correct permissions for the private key file:

## bash
Copy
Edit
chmod 400 my-key.pem
This prevents unauthorized access to the key.

3️⃣ Find the Public IP Address
Go to EC2 Dashboard → Instances → Select your instance.
Look for Public IPv4 address (e.g., 3.85.12.34).
4️⃣ SSH into the Instance
Run the following command:

## bash
Copy
Edit
ssh -i my-key.pem ec2-user@<public-ip>
Example:

## bash
Copy
Edit
ssh -i my-key.pem ec2-user@3.85.12.34
Note:

## ec2-user is the default username for Amazon Linux instances.
If using Ubuntu, replace ec2-user with ubuntu.
If using RHEL, use ec2-user or root.
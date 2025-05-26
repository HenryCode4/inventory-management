- aws

    when trying to use the aws services there are steps to follow 
    1 - create your VPC (10.0.0.0/16)
    2 - Create your subnet using the vpc you created (create your public subnet(10.0.1.0/24) and also create your private subnet(10.0.2.0/24))
    3 - Create your internet gateways(this will provide a way to connect to the created public subnet or vpc)
    4 - Attach your gateway to the vpc you created
    5 - we will create a route table and connect it to the public subnet and the private subnet(route table decides what route can connect to which route on the vpc )
    6 - We will create a public route table and a private route table for each subnet
    7 - associate your public route table to the public subnet and the private to the private subnet 
    8 - Connect the public route table to the (click on route) and connect with the public IP(0.0.0.0/0) which means connect with the whole internet (then associate with vpc internet gate way created )
    9 - for the private route table it should remain connect to the local ip, it should not be associated with the internet gate way
    10 - create EC2 (click on lunch instances)
    11 - set up a key pair to connect or choose from an existing key-pair
    12 - Under network settings check the boxes that states (Allow SSH traffic from, Allow HTTPS traffic from the internet, Allow HTTP traffic from the internet)
    13 - make sure you have the 3 boxes checked before clicking edit button on network settings (so as to connect our subnet to the right one )
    14 - make sure your subnet is connected to the public (auto assign public ip: enabled)
    15 - change security group name (sg_public_ec2) add it to the description (after this lunch instance)
    16 - Go back to the list of instance check and click connect ( Amazon Linux 2023 : means it worked using the pem key)


# EC2 Setup Instructions

## 1. Connect to EC2 Instance via EC2 Instance Connect

## 2. Install Node Version Manager (nvm) and Node.js

- **Switch to superuser and install nvm:**

```
sudo su -
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

- **Activate nvm:**

```
. ~/.nvm/nvm.sh
```

- **Install the latest version of Node.js using nvm:**

```
nvm install node
```

- **Verify that Node.js and npm are installed:**

```
node -v
npm -v
```

## 3. Install Git

- **Update the system and install Git:**

```
sudo yum update -y
sudo yum install git -y
```

- **Check Git version:**

```
git --version
```

- **Clone your code repository from GitHub:**

```
git clone [your-github-link]
```

- **Navigate to the directory and install packages:**

```
cd inventory-management
npm i
```

- **Create Env File and Port 80:**

```
echo "PORT=80" > .env
```

- **Start the application:**

```
npm start
```

## 4. Install pm2 (Production Process Manager for Node.js)

- **Install pm2 globally:**

```
npm i pm2 -g
```

- **Create a pm2 ecosystem configuration file (inside server directory):**

```
module.exports = { apps : [{ name: 'inventory-management', script: 'npm', args: 'run dev', env: { NODE_ENV: 'development', ENV_VAR1: 'environment-variable', } }], };
```

- **Modify the ecosystem file if necessary:**

```
nano ecosystem.config.js
```

- **Set pm2 to restart automatically on system reboot:**

```
sudo env PATH=$PATH:$(which node) $(which pm2) startup systemd -u $USER --hp $(eval echo ~$USER)
```

- **Start the application using the pm2 ecosystem configuration:**

```
pm2 start ecosystem.config.js
```

- **Useful pm2 commands:**

  - **Stop all processes:**

  ```
  pm2 stop all
  ```

  - **Delete all processes:**

  ```
  pm2 delete all
  ```

  - **Check status of processes:**

  ```
  pm2 status
  ```

  - **Monitor processes:**

  ```
  pm2 monit
  ```


1 - creating subnet for our database 
2 - we will be creating a private subnet 2 and connect it to the private subnet we initially created  
3 - go to rds and click on subnet group (create subnet group)
rds_inventorymanagement_initial



deploying the frontend to amplify
1 - 




s3 bucket
1 - bucket name 
2 - ACL disabled
3 - Uncheck Block Public Access settings for this bucket
4 - Bucket Versioning (disabled)

5 - Bucket policy 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::s3inventmanagement/*"
        }
    ]
}

# AWS-Server-Based-Architecture
All AWS resources were terminated after project completion to avoid charges (pay-as-you-go model)

This project demonstrates a server-based architecture on AWS, where a web application is deployed using manually configured cloud infrastructure.
The setup includes a secure and scalable environment with public and private subnets, load balancing, and database integration.

### Tech Stack / Services

- Compute: EC2 (Ubuntu Servers)
- Networking: VPC, Subnets, Internet Gateway, NAT Gateway, Route Tables
- Storage: S3
- Database: RDS (SQL), DynamoDB (NoSQL)
- Security: IAM, Security Groups
- Scalability: Load Balancer, Target Groups

### Architecture Highlights

- Custom VPC with 3 subnets (2 Public + 1 Private)
- Load Balancer distributing traffic across public servers
- Private subnet used for secure database handling
- NAT Gateway for controlled outbound access
- IAM roles for secure service permissions

### Steps 
1. Create VPC
   Create a Custom VPC
   Enable DNS support
   This will act as the base network for all resources

2. Create Subnets
   Create 2 Public Subnets and 1 Private Subnet inside the VPC
   Assign all subnets to your custom VPC

3. Setup Internet Gateway
   Create an Internet Gateway
   Attach it to your custom VPC

4. Configure Route Tables
   Create Public Route Table
   Add route to Internet Gateway
   Assign it to Public Subnets

5. Create Private Route Table
   Keep it internal (no direct internet)
   Assign it to Private Subnet

6. Create Security Group
   Create a Security Group inside VPC
   Allow: HTTP/HTTPS (Web access)

   SSH (Port 22)
   Assign this Security Group to all EC2 instances

7. Launch EC2 Instances
   Create 3 EC2 instances (Ubuntu)
   Assign: 2 instances → Public Subnets

   1 instance → Private Subnet
   Attach Security Group and Key Pair

8. Setup S3 Storage
   Create an S3 Bucket
   Use it for storing application data/files

9. Setup Database (RDS)
   Create RDS instance (MySQL)
   Assign it to your custom VPC
   Use Private Subnet for security

10. Setup DynamoDB
   Create DynamoDB table
   Use it for NoSQL data storage

11. Create Load Balancer
    Create Application Load Balancer
    Assign it to Public Subnets
    Link it with EC2 instances using Target Group

12. Create NAT Gateway
    Create NAT Gateway in Public Subnet
    Attach Elastic IP
    Link it to Private Route Table
    This allows private server to access internet securely

13. Setup IAM Role
    Create IAM Role with permissions (S3, RDS, DynamoDB)
    Assign this role to EC2 instances

14. Deploy Application
    Connect to EC2 using SSH
    Install Python, Flask, dependencies
    Run your web application

15. Connect Database
    Connect your app to RDS endpoint
    Create tables and verify data storage

16. Access Application via the Web Brouser or CMD.

Copy Load Balancer DNS
👉 Open in browser to access your website

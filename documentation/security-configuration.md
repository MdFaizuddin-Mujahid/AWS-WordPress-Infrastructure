# AWS Security Configuration

## 1. Overview

Configured AWS networking and access controls to protect the WordPress infrastructure and restrict unnecessary access between application and database components.

## 2. Amazon VPC

- Deployed infrastructure inside a dedicated Amazon VPC.
- Used multiple Availability Zones for application availability.
- Configured subnets for the application infrastructure.
- Kept the database within the same VPC as the application.

## 3. Security Groups

Configured Security Groups to control inbound and outbound traffic.

### Application Load Balancer Security Group
- Allowed HTTP traffic on port 80 from users.
- Forwarded application traffic to the target group.

### EC2 Security Group
- Allowed HTTP traffic on port 80 from the ALB Security Group.
- SSH access was used for server administration.

### RDS Security Group
- Allowed MySQL traffic on port 3306 from the EC2 Security Group.
- Restricted database access to the application layer.

## 4. IAM

- Used AWS IAM to manage access to AWS resources.
- Followed the principle of least privilege where applicable.
- Avoided embedding AWS credentials in application files or GitHub repositories.

## 5. Network Traffic Flow

Users → Application Load Balancer → EC2 WordPress Instances → Amazon RDS MySQL

Database access is restricted through Security Group rules.

## 6. Security Best Practices

- Avoid exposing database ports publicly.
- Restrict SSH access to trusted IP addresses.
- Use IAM roles and policies instead of hardcoded credentials.
- Never upload access keys, passwords, private keys or database credentials to GitHub.
- Review Security Group rules regularly.

## 7. Key Learnings

- Amazon VPC networking.
- Security Group configuration.
- IAM access management.
- Application-to-database traffic restrictions.
- AWS infrastructure security fundamentals.

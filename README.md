# AWS WordPress Infrastructure

## Project Overview
Designed and deployed a WordPress application on AWS using a LAMP stack, Application Load Balancer, Auto Scaling Group, and Amazon RDS. Implemented an RDS Blue/Green deployment to upgrade the MySQL database engine.

## Architecture
**Request flow:**

Users → Application Load Balancer → Target Group → EC2 WordPress Instances → Amazon RDS MySQL

The application instances are managed by an Auto Scaling Group across multiple Availability Zones.

## AWS Services Used
- **Amazon EC2:** Hosts the WordPress application.
- **Application Load Balancer:** Distributes incoming HTTP traffic.
- **EC2 Auto Scaling Group:** Maintains and scales EC2 capacity.
- **Amazon RDS for MySQL:** Managed relational database.
- **RDS Blue/Green Deployments:** Performs database engine upgrades.
- **Amazon VPC:** Provides network isolation and subnets.
- **AWS IAM:** Manages access and permissions.

## Auto Scaling Configuration
- Minimum capacity: 2
- Desired capacity: 2
- Maximum capacity: 6
- Scaling policy: Target tracking
- Target CPU utilization: 50%

## Database Upgrade
Performed an RDS Blue/Green deployment:

- Original MySQL version: 8.4.7
- Target MySQL version: 8.4.11
- Created a Green database environment.
- Upgraded the Green database.
- Verified replication before switchover.
- Completed the Blue/Green switchover.
- Verified the upgraded database and WordPress application.

## Screenshots

Project screenshots are available in the [`screenshots`](screenshots/) directory.

## Key Learnings
- AWS EC2 deployment and configuration
- LAMP stack setup
- Application Load Balancer and target groups
- Auto Scaling Groups and scaling policies
- Amazon RDS database management
- Blue/Green database deployments and upgrades
- AWS networking and IAM fundamentals


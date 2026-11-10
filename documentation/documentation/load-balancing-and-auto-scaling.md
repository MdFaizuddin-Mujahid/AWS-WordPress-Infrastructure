# AWS Load Balancing and Auto Scaling

## 1. Overview

Configured an Application Load Balancer (ALB) and EC2 Auto Scaling Group to improve the availability and scalability of the WordPress application.

## 2. Application Load Balancer

Created an Application Load Balancer named `wordpress-alb`.

- Listener protocol: HTTP
- Listener port: 80
- Target Group: `wordpress-tg`
- Health check protocol: HTTP
- Health check path: `/`
- Success codes: 200

The ALB distributes incoming application traffic across registered EC2 instances.

## 3. Target Group Health Checks

Configured health checks to monitor application instance availability.

- Protocol: HTTP
- Port: 80
- Path: `/`
- Interval: 30 seconds
- Timeout: 5 seconds
- Healthy threshold: 5
- Unhealthy threshold: 2

Unhealthy targets can be removed from traffic routing while the Auto Scaling Group manages instance replacement.

## 4. EC2 Auto Scaling Group

Created an Auto Scaling Group named `wordpress-asg`.

### Capacity Configuration

| Setting | Value |
|---|---:|
| Minimum capacity | 2 |
| Desired capacity | 2 |
| Maximum capacity | 6 |
| Instance type | t3.micro |
| Availability Zones | ap-south-1a, ap-south-1b |

## 5. Scaling Policy

Configured a target tracking scaling policy.

- Metric: Average CPU utilization
- Target value: 50%
- Instance warm-up: 300 seconds

The Auto Scaling Group adjusts the number of EC2 instances according to the configured scaling policy and capacity limits.

## 6. High Availability

- Distributed application instances across two Availability Zones.
- Used an Application Load Balancer to distribute incoming requests.
- Configured health checks to monitor registered targets.
- Used Auto Scaling to maintain the desired instance capacity.

## 7. Key Learnings

- Application Load Balancer configuration.
- Target Group registration and health checks.
- EC2 Auto Scaling Group management.
- Target tracking scaling policies.
- High availability across Availability Zones.

# Amazon RDS Blue/Green Deployment – MySQL Upgrade

## 1. Overview

Implemented an Amazon RDS Blue/Green Deployment to upgrade the WordPress application's MySQL database from version 8.4.7 to 8.4.11.

The objective was to perform a controlled database engine upgrade while minimizing application downtime.

## 2. Initial Configuration

| Component | Configuration |
|---|---|
| Database Engine | MySQL Community |
| Original Database | mysqlwp |
| Original Engine Version | 8.4.7 |
| DB Instance Class | db.t3.micro |
| AWS Region | ap-south-1 |

## 3. Blue/Green Deployment Process

### Step 1: Create Green Environment
- Created a Blue/Green deployment from the existing production database.
- Blue environment continued running MySQL 8.4.7.
- Green environment was created as a separate database.

### Step 2: Upgrade Green Database
- Upgraded the Green database to MySQL 8.4.11.
- Waited for the database upgrade to complete.
- Verified the new engine version.

### Step 3: Verify Replication
- Confirmed that Blue/Green replication was active.
- Verified replication lag before switchover.

### Step 4: Switchover
- Initiated the RDS Blue/Green switchover.
- AWS switched the database roles.
- The upgraded database became the production database.

## 4. Final Configuration

| Component | Engine Version |
|---|---|
| Production database (mysqlwp) | **8.4.11** |
| Previous database (mysqlwp-old1) | 8.4.7 |

## 5. Validation

- Verified that the production database was running MySQL 8.4.11.
- Accessed the WordPress application after switchover.
- Confirmed that the application was functioning correctly.

## 6. Key Learnings

- Amazon RDS Blue/Green Deployments.
- MySQL engine version upgrades.
- Database replication monitoring.
- Controlled database switchover.
- Post-upgrade application validation.

## 7. Conclusion

Successfully upgraded the WordPress application's Amazon RDS MySQL database from 8.4.7 to 8.4.11 using Blue/Green Deployment and verified application functionality after switchover.

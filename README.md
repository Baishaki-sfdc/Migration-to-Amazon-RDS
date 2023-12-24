# Migration-to-Amazon-RDS

## Overview:
 migrate the café web application to use a fully managed Amazon Relational Database Service (Amazon RDS) database (DB) instance instead of a local database instance.<br>
 During the migration process, you build the required components, including two private subnets in different Availability Zones, a security group for the database instance, and the RDS DB instance itself. After the database has been migrated, reconfigure the café application to use the Amazon RDS instance instead of a local database.

Create an Amazon RDS MariaDB instance by using the AWS CLI.

Migrate data from a MariaDB database on an EC2 instance to an Amazon RDS MariaDB instance.

Monitor the Amazon RDS instance by using Amazon CloudWatch metrics.

Steps:
Task 1: Generating order data on the café website
## Creating an Amazon RDS instance by using the AWS CLI


Create the following prerequisite components required to build the Amazon RDS instance:

A security group firewall for the Amazon RDS instance

Two private subnets and a database subnet group

Create the Amazon RDS MariaDB instance.<br>

## Task2:
Creating prerequisite components
CafeDatabaseSG (Security group for the Amazon RDS database)

CafeDB Private Subnet 1

CafeDB Private Subnet 2

CafeDB Subnet Group (Database subnet group)CafeDatabaseSG (Security group for the Amazon RDS database)

Creating the Amazon RDS MariaDB instance
specify the following:DB instance identifier: CafeDBInstance

Engine option: MariaDB

DB engine version: 10.5.13

DB instance class: db.t3.micro

Allocated storage: 20 GB

Availability Zone: CafeInstanceAZ

DB Subnet group: CafeDB Subnet Group

VPC security groups: CafeDatabaseSG

Public accessibility: No

Username: root

Password

## Task3:
 Migrating application data to the Amazon RDS instance
  migrate the data from the existing local database to the newly created Amazon RDS database. Specifically, you do the following:

Connect to the CafeInstance by using EC2 Instance Connect.

Use the mysqldump utility to create a backup of the local database.

Restore the backup to the Amazon RDS database.

## Task 4: Configuring the website to use the Amazon RDS instance using AWS Systems Manager:
In this task, change the database URL parameter of the café application to point to the endpoint address of the RDS instance.

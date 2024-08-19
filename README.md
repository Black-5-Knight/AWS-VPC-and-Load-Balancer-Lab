# AWS VPC and Load Balancer Lab

## Overview

This lab demonstrates the setup of a Virtual Private Cloud (VPC) on AWS, including creating subnets, configuring an internet gateway, and deploying instances with a load balancer. The lab consists of the following stages:

1. **Stage 1**: Set up a VPC with public subnets, configure internet access, and deploy instances with Nginx and a load balancer.
2. **Stage 2**: Create private subnets that access the internet through public subnets.

## Prerequisites

To follow this lab, you will need:

- An AWS account.
- Basic knowledge of AWS services such as VPC, EC2, and Load Balancer.
- AWS CLI installed and configured (optional, for command-line operations).

## Installation and Setup

### Stage 1: Initial Setup

#### 1. Create a VPC

1. Sign in to the AWS Management Console.
2. Navigate to the VPC Dashboard.
3. Create a new VPC with the CIDR block `192.168.0.0/16`.

#### 2. Create Subnets

1. In the VPC Dashboard, go to the "Subnets" section.
2. Create the first subnet with CIDR block `192.168.1.0/24`.
3. Create the second subnet with CIDR block `192.168.2.0/24`.

#### 3. Configure Internet Access

1. Navigate to the "Internet Gateways" section in the VPC Dashboard.
2. Create a new Internet Gateway and attach it to your VPC.
3. Update the route table associated with your VPC to route traffic to the internet gateway.

#### 4. Launch EC2 Instances

1. **Instance 1**:
   - Launch an EC2 instance in the subnet `192.168.1.0/24`.
   - Install Nginx and set up a small website.

2. **Instance 2**:
   - Launch an EC2 instance in the subnet `192.168.2.0/24`.
   - Install Nginx and set up a small website.

3. **Instance 3 (Load Balancer)**:
   - Launch an EC2 instance in either subnet.
   - Configure this instance as a load balancer to distribute traffic between the two Nginx instances.

#### 5. Configure Nginx

On each Nginx instance, you can use the following commands to install and configure Nginx:

```bash
# Update package lists
sudo apt-get update

# Install Nginx
sudo apt-get install -y nginx

# Create a simple HTML file
echo "<html><body><h1>Welcome to Instance 1</h1></body></html>" | sudo tee /var/www/html/index.html

# Start Nginx service
sudo systemctl start nginx

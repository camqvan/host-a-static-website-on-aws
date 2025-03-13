## Host a Static Website on AWS

📌 Project Overview

This project demonstrates how to deploy a static HTML web application on AWS using various AWS services to ensure security, scalability, and fault tolerance. The deployment is fully automated using a shell script and managed via a GitHub repository for version control.

🏗️ Architecture

The architecture of this deployment includes:

🔹 Virtual Private Cloud (VPC): Configured with both public and private subnets across two different Availability Zones.

🔹 Internet Gateway: Enables connectivity between the VPC and the wider Internet.

🔹 Security Groups: Used as a firewall mechanism to control traffic to and from EC2 instances.

🔹 Availability Zones: Leveraged to enhance system reliability and fault tolerance.

🔹 Public Subnets: Utilized for infrastructure components like the NAT Gateway and Application Load Balancer.

🔹 EC2 Instance Connect Endpoint: Securely connects to assets within both public and private subnets.

🔹 Private Subnets: Hosts the web servers (EC2 instances) to enhance security.

🔹 NAT Gateway: Allows instances in private subnets to access the Internet securely.

🔹 EC2 Instances: Hosts the static website.

🔹 Application Load Balancer: Distributes web traffic evenly across an Auto Scaling Group of EC2 instances in multiple Availability Zones.

🔹 Auto Scaling Group: Ensures high availability, scalability, fault tolerance, and elasticity.

🔹 GitHub Integration: Stores web files for version control and collaboration.

🔹 AWS Certificate Manager: Secures application communications.

🔹 Simple Notification Service (SNS): Sends alerts regarding Auto Scaling Group activities.

🔹 Route 53: Manages the domain name and DNS record setup.

🚀 Deployment Steps:
#!/bin/bash
# Switch to the root user for administrative privileges
sudo su

# Update installed packages to their latest versions
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change the working directory to the Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project GitHub repository
git clone https://github.com/camqvan/host-a-static-website-on-aws.git

# Copy all files from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws

# Enable Apache HTTP Server to start automatically at system boot
systemctl enable httpd  

# Start Apache HTTP Server
systemctl start httpd  

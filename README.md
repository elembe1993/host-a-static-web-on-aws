![Alt text](/Host_a_Static_Website_on_AWS.png)

# Host a Static Website on AWS

This project demonstrates the deployment of a static HTML web application on AWS using various services and configurations. Below is an overview of the setup along with the deployment script and other relevant information.

## Project Overview:

The project utilizes the following AWS resources and configurations:

1. **Virtual Private Cloud (VPC)**:
   - Configured with public and private subnets across two availability zones for enhanced fault tolerance.

2. **Internet Gateway**:
   - Deployed to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Groups**:
   - Used as a network firewall mechanism to control inbound and outbound traffic.

4. **Availability Zones**:
   - Leveraged to enhance system reliability and fault tolerance.

5. **Subnets**:
   - Public subnets for infrastructure components like NAT Gateway and Application Load Balancer.
   - Private subnets for enhanced security, where web servers (EC2 instances) are positioned.

6. **EC2 Instance Connect Endpoint**:
   - Implemented for secure connections to assets within both public and private subnets.

7. **NAT Gateway**:
   - Enabled instances in private subnets to access the Internet.

8. **Web Servers (EC2 Instances)**:
   - Hosted the website on EC2 instances within private subnets.

9. **Application Load Balancer (ALB)**:
   - Utilized for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.

10. **Auto Scaling Group**:
    - Automatically manages EC2 instances to ensure website availability, scalability, fault tolerance, and elasticity.

11. **Version Control**:
    - Web files are stored on GitHub for version control and collaboration.

12. **Certificate Manager**:
    - Used for securing application communications.

13. **Simple Notification Service (SNS)**:
    - Configured to alert about activities within the Auto Scaling Group.

14. **Domain Name System (DNS)**:
    - Registered the domain name and set up a DNS record using Route 53.

## Deployment Script:

```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su
# Update all installed packages to their latest versions
yum update -y
# Install Apache HTTP Server
yum install -y httpd
# Change the current working directory to the Apache web root
cd /var/www/html
# Install Git
yum install git -y
# Clone the project GitHub repository to the current directory
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/
# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws
# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd 
# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

## Additional Notes:

- Ensure that appropriate IAM roles and policies are configured to grant necessary permissions to resources.
- Regularly monitor the system for security vulnerabilities and apply updates as needed.
- Consider implementing additional security measures such as WAF (Web Application Firewall) for enhanced protection against web-based attacks.

For detailed setup instructions and further customization, refer to the documentation and comments within the provided scripts and configuration files.

**Author:** Alex Elembe




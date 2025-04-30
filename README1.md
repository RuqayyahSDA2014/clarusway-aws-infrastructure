# AWS Web Application Deployment - Clarusway Bootcamp

## Overview

This project demonstrates how to deploy a highly available web application using AWS services including S3, Auto Scaling Group (ASG), and Application Load Balancer (ALB). The deployment is based on a static index.html file and logo images provided as part of the assignment.

---

## Part 1: S3 Setup for Static Assets

### Steps:

1. Created an S3 bucket named: sda2014 in the eu-north-1 region.
2. Uploaded the following files to the bucket:
   - index.html
   - logo.png
   - sda.png
3. Enabled *Static Website Hosting* in the bucket settings.
4. Configured the bucket policy to allow public read access using this JSON:
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Effect": "Allow",
       "Principal": "*",
       "Action": "s3:GetObject",
       "Resource": "arn:aws:s3:::sda2014/*"
     }]
   }
5.	Verified the static website is accessible via the S3 endpoint.




Part 2: Auto Scaling Group (ASG)

Steps:

	1.	Created a Launch Template using Amazon Linux 2 with the following user data:

#!/bin/bash
yum update -y
yum install nginx -y
systemctl start nginx
systemctl enable nginx
aws s3 cp s3://sda2014/index.html /usr/share/nginx/html/


	2.	Created an Auto Scaling Group with the following configuration:
	•	Min capacity: 1
	•	Desired capacity: 2
	•	Max capacity: 3
	•	Health checks: EC2 + ELB
	•	Attached to the target group used by the ALB


Part 3: Application Load Balancer (ALB)

Steps:

	1.	Created an Internet-facing ALB with:
	•	Listener on port 80 (HTTP)
	2.	Created a Target Group with:
	•	Protocol: HTTP
	•	Port: 80
	•	Health check path: /
	3.	Attached the ASG to the target group.
	4.	Verified round-robin load balancing 


Deliverables:

	•	Screenshot showing the ALB DNS name working in the browser.
	•	curl output showing responses from different EC2 instances.


Cleanup


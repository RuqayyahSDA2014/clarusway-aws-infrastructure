## Part 2: Auto Scaling Group with ALB

### Overview
This part demonstrates deploying NGINX web servers using Auto Scaling Group behind an Application Load Balancer.
The HTML content is pulled from an S3 bucket at boot time.

### Architecture
- Launch Template installs and configures NGINX
- EC2 pulls index.html from S3 bucket (sda2014)
- ALB distributes traffic across instances

### Screenshots
- Running Instances
- Auto Scaling Group settings
- ALB DNS access result
# Clarusway Bootcamp - AWS S3 Static Website

## Part 1: S3 Setup (Static Website Hosting)

### Bucket Name:
sda2014  
(Region: eu-north-1)

---

### Files Uploaded:
- index.html  
- logo.png  
- sda.png  

---

### Static Website Hosting:
Enabled  
*Website URL:*  
http://sda2014.s3-website.eu-north-1.amazonaws.com/
---

### Bucket Policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::sda2014/*"
    }
  ]
}
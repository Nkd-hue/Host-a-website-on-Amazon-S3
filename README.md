Hosting a Static Website on Amazon S3

Overview
This project demonstrates how to **host and manage a static website using Amazon S3**, one of the most reliable and scalable cloud storage services.  
I created an S3 bucket, configured it for static website hosting, uploaded web files, and applied a secure bucket policy to protect the content from accidental deletion or unauthorized access.



 AWS Services Used
- **Amazon S3** – for static website hosting and file storage  
- **AWS Identity and Access Management (IAM)** – for managing permissions  
- **AWS Management Console** – to configure the bucket and website settings  



1. **Created an S3 Bucket**  
   - Named the bucket with a globally unique name.  
   - Chose the region closest to my users for faster access.  

2. **Uploaded Website Files**  
   - Added `index.html` as the homepage and `error.html` for invalid URLs.  

3. **Configured Static Website Hosting**  
   - Enabled static web hosting from the S3 console.  
   - Selected “Host a static website.”  
   - Set `index.html` as the **Index Document** and `error.html` as the **Error Document**.  

4. **Set Permissions**  
   - Configured **Block Public Access** settings to allow public reads for website access.  
   - Applied a **bucket policy** that denies file deletion to ensure data protection.

5. **Tested the Website**  
   - Accessed the website using the generated **S3 website endpoint URL** to confirm functionality.



## Bucket Policy Example
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyDeleteAccess",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:DeleteObject",
      "Resource": "arn:aws:s3:::my-website-bucket/*"
    }
  ]
}

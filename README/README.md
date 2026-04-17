# Project Title
Scalable Static Website Hosting on AWS (S3 + CloudFront + Route 53 + Security Hardening)

---

# Project Scenario
You have been contracted as a Cloud Engineer by a fast-growing personal brand looking to launch a high-performance global portfolio website with:
•	Ultra-fast global delivery
•	Strong security (no public S3 exposure)
•	Custom domain with HTTPS
•	Scalable, serverless architecture
•	Cost-efficient infrastructure

Design and deploy a secure, scalable, enterprise-ready static hosting architecture using AWS.

---

# Solution Overview
Implemented a serverless, globally distributed architecture using:
•	Amazon S3 → Private static file storage  
•	Amazon CloudFront → CDN for caching + HTTPS  
•	Third Party Domain name management  
•	AWS Certificate Manager (ACM) → Free SSL/TLS certificates  
•	AWS IAM → Secure access control  

---

# Skills Demonstrated
•	Cloud Architecture Design  
•	AWS S3 (Advanced Configuration)  
•	CloudFront CDN (Production Setup)  
•	Route 53 DNS Management  
•	SSL/TLS Configuration (ACM)  
•	IAM & Security Best Practices  
•	Serverless Infrastructure  
•	Performance Optimization  
•	Real-world deployment strategy  

---

# Architecture Overview
1.	User enters: https://www.myportfolio.com  
2.	Route 53 resolves domain to CloudFront  
3.	CloudFront CDN:  
   o	Serves cached content globally  
   o	Enforces HTTPS  
4.	If not cached → CloudFront fetches from private S3 bucket  
5.	S3 returns static files securely  
6.	User receives fast, secure content

<img width="1536" height="1024" alt="Architecture Diagram 2" src="https://github.com/user-attachments/assets/67454394-5ae1-4f7d-8936-ebe25492eba5" />

   

<img width="1408" height="768" alt="Architectural Diagram" src="https://github.com/user-attachments/assets/45ab36c0-29b3-4ad8-ac24-0a53660de72a" />


---

# Architecture Principle (What Makes This Stand Out)

• S3 bucket is completely private  
• Only CloudFront can access S3 (via Origin Access Control)  
• HTTPS enforced globally  
• Edge caching reduces latency  
• No direct public exposure  

---

# Step-by-Step Implementation

---

## 1. Create S3 Bucket (Private Storage)
•	Bucket name: myportfolio-static-site  
•	Region: North Virginia  
•	Block Public Access = ON  
 
 <img width="973" height="362" alt="image" src="https://github.com/user-attachments/assets/d11cf19d-cb2d-445a-8b2d-bca5d266e88d" />
<img width="975" height="298" alt="image" src="https://github.com/user-attachments/assets/f3704882-42ac-4c3b-9727-0acbfda7b90d" />


---

## 2. Upload Website Files into S3 Bucket

Structure:
index.html
error.html
style.css
script.js
<img width="974" height="514" alt="image" src="https://github.com/user-attachments/assets/a632bcc6-cd3e-4b76-8e36-8a20369f4324" />
 
---

## 3. Configure S3 for Static Hosting (Backend Only)
•	Enable static website hosting  
•	Index: index.html  
•	Error: error.html  

This allows you to use S3 only as storage/origin, not as the public-facing website  
 <img width="975" height="375" alt="image" src="https://github.com/user-attachments/assets/5a49b9f6-4f1e-4fc1-8290-6c6d06574989" />

---

## 4. Create CloudFront Distribution

Origin Configuration:
•	Origin: Amazon S3  
•	Allow private S3 bucket access to CloudFront  
•	Enable OAC  
•	Redirect HTTP → HTTPS  

Default Root Object: index.html
 <img width="974" height="284" alt="image" src="https://github.com/user-attachments/assets/54354cfc-3cc7-473b-a499-691bf3545504" />
<img width="975" height="349" alt="image" src="https://github.com/user-attachments/assets/16e39d73-e49a-4a14-839c-f14a65a31d14" />
<img width="974" height="279" alt="image" src="https://github.com/user-attachments/assets/c49b8c92-09e8-4155-866a-8dc6234e0f44" />


---

## 5. Attach S3 Bucket Policy (Secure Access Only)
<img width="975" height="484" alt="image" src="https://github.com/user-attachments/assets/aff6b457-061f-47e2-b86c-a6cb18e8edad" />

 
---

## 6. Test CloudFront URL on a Web Browser
 <img width="975" height="409" alt="image" src="https://github.com/user-attachments/assets/5dd6fbe4-8866-4076-b716-c39fe0f0d914" />

________________________________________
## 7. Request SSL Certificate (ACM)
• Request a public certificate
• Domain: blog.gosam.world
• Validation: DNS (via Route 53, GoDaddy, or any other 3rd party domain name provider)
• Region: us-east-1 (N. Virginia)
 <img width="974" height="531" alt="image" src="https://github.com/user-attachments/assets/d9a5545f-5259-414d-b4ba-00902275f133" />

<img width="974" height="175" alt="image" src="https://github.com/user-attachments/assets/4e57ee20-e304-481f-a066-76733a2105f8" />

 
________________________________________
8. Setup Custom Domain (Via GoDaddy)
• CNAME = blog
• Value = d2iwd3hi54yrab.cloudfront.net.
<img width="975" height="96" alt="image" src="https://github.com/user-attachments/assets/d2d12ea4-2924-4f69-b93b-bc2918eba833" />

 
________________________________________
9. Connect Domain to CloudFront
• Add Alternate Domain Name (CNAME)
• Attach domain name
• Attach ACM SSL Certificate
<img width="975" height="275" alt="image" src="https://github.com/user-attachments/assets/dc347781-2540-41a0-8fc4-33bd7c87a188" />

 
________________________________________
10. Testing & Validation
• Access via:
o CloudFront URL
o Custom domain
<img width="975" height="399" alt="image" src="https://github.com/user-attachments/assets/c770f302-8af1-4242-bb2e-dce7cf04453d" />

<img width="975" height="403" alt="image" src="https://github.com/user-attachments/assets/7abfcc27-59e8-4cca-9c61-8898d6aa2f90" />
 


 

---


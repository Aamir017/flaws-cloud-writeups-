**Category:** Cloud Security (S3 Bucket Access with AWS Credentials)  
**Difficulty:** Beginner  
**Platform:** Flaws.Cloud  
**Date:** 2025-05-14  

---

## Challenge Overview

Level 2 of Flaws.Cloud involves accessing a **private S3 bucket** using valid AWS credentials. This challenge introduces how improper IAM configurations can lead to sensitive bucket exposure.

---

## Tools Used

- AWS CLI
    
- AWS Console (IAM)
    
- Browser
    

---

## Thought Process

1. The URL indicated it’s still S3-based, but public access didn’t work.
    
2. Realized that AWS credentials may be required to access the content.
    
3. Created a new IAM user with limited privileges for safer practice.
    
4. Used AWS CLI to interact with the private bucket after configuring credentials.
    

---

## Exploitation Steps

1. **Logged in to AWS Console** and navigated to **IAM** → **Users**.
    
2. **Created a new user** with programmatic access (e.g., `s3labuser`).
    
3. **Attached policy**: `AmazonS3FullAccess` for the purpose of the lab.
    
4. Downloaded the **Access Key ID** and **Secret Access Key**.
    
5. **Configured AWS CLI** locally with this user:
    
    bash
    
    CopyEdit
    
    `aws configure --profile s3labuser`
    
    Entered:
    
    - Access Key ID
        
    - Secret Access Key
        
    - Region: `us-west-2`
        
    - Output: `json`
        
6. **Accessed the S3 bucket** with:
    
    bash
    
    CopyEdit
    
    `aws s3 --profile s3labuser ls s3://level2-c8b217a33fcf1f839f6f1f73a00a9ae7.flaws.cloud`
    
7. **Found a file** (e.g., `secret-abc123.html`).
    
8. **Opened it in the browser**:
    
    bash
    
    CopyEdit
    
    `http://level2-c8b217a33fcf1f839f6f1f73a00a9ae7.flaws.cloud/secret-abc123.html`
    
9. **Discovered the flag** inside the HTML file.
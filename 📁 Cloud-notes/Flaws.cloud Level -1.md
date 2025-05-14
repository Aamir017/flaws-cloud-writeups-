# Level 1 Write-up 

**Category:** Cloud Security (S3 Bucket Enumeration)  
**Difficulty:** Beginner  
**Platform:** Flaws.Cloud  
**Date:** 2025-05-14  
**Author:** Batman

---

## Challenge Overview

Level 1 of Flaws.Cloud introduces basic **S3 bucket enumeration**. The goal is to discover an accessible file hidden inside a public S3 bucket.

---

## Tools Used

- AWS CLI
    
- Browser
    
- Gobuster (optional, but didn’t help here)
    

---

## Thought Process

1. Since it's about AWS, I suspected S3 buckets were being used.
    
2. I attempted using `gobuster` for directory brute-forcing but didn't get any useful results.
    
3. I recalled that AWS allows public access to buckets via unauthenticated requests.
    

---

## Exploitation Steps

1. Ran the following command to list objects in the public bucket:
    
    bash
    
    CopyEdit
    
    `aws s3 ls s3://flaws.cloud/ --no-sign-request --region us-west-2`
    2. Found a file named:
    
    CopyEdit
    
    `secret-dd02c7c.html`
    
2. Accessed it in the browser via:
    
    arduino
    
    CopyEdit
    
    `http://flaws.cloud/secret-dd02c7c.html`
    
3. Found the flag inside the HTML page.



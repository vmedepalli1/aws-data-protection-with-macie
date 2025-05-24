# 🔐 AWS Cloud Data Protection with Macie, KMS, and S3

## 📘 Project Summary

This project demonstrates how to implement a secure, scalable data protection pipeline in AWS. It protects sensitive data such as Personally Identifiable Information (PII) and Protected Health Information (PHI) by encrypting S3 objects with AWS KMS, scanning them with Amazon Macie, and routing classification findings to security teams using SNS and EventBridge.


---

## 🧰 AWS Services Used

- **Amazon S3** – Stores sensitive data and discovery results
- **AWS KMS** – Provides encryption using Customer Managed Keys (CMK)
- **Amazon Macie** – Scans and classifies sensitive data in S3 buckets
- **IAM** – Enforces least-privilege access through policies
- **Amazon SNS** – Sends email notifications for classified findings
- **Amazon EventBridge** – Triggers alerts based on Macie findings

---

## 🚀 Key Features

- Encrypts all sensitive data using SSE-KMS with a CMK
- Automatically classifies files using Amazon Macie’s managed data identifiers
- Sends high-severity findings to email via SNS and EventBridge
- Stores all Macie findings in a dedicated results S3 bucket
- Uses realistic test data to simulate PII and PHI
- Provides reusable policies and walkthrough documentation

---

## 📁 Directory Structure

aws-data-protection-project/
1-README.md                           # Project overview
2-docs/
   -project-walkthrough.md           # Step-by-step implementation guide
3-policies/                           # bucket polices and KMS policies in json format
   -source-bucket-policy.json
   -discovery-results-bucket-policy.json
   -kms-policy.json
4-s3-data/
   -sample PII and PHI data files         # Mock sensitive data files
5-macie-classification-jobs.
   -macie-job-setup.md                    # macie job creation 
   -job-screenshots
6-sns-eventbridge/
   -sns-setup.md
   -eventbridge-rule-pattern.json
7-findings-samples/
   -findings screenshots
   
---

## 🧪 How to Test

1. Create two S3 buckets: one for sensitive data, one for Macie discovery results
2. Create a KMS CMK and configure it for SSE-KMS encryption
3. Apply secure bucket policies and a key policy granting access to Macie
4. Upload test files containing mock PII and PHI to the data bucket
5. Enable Amazon Macie and configure Discovery Result Export
6. Create and run a classification job with managed data identifiers
7. Set up an SNS topic and email subscription
8. Create an EventBridge rule to trigger alerts on Macie findings
9. Validate:
   - Findings appear in the Macie console
   - Findings are exported to your results S3 bucket
   - You receive email alerts from SNS

---

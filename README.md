# 🔐 AWS Privileged Access Management (PAM) Simulation
![Terraform Validation](https://github.com/your-username/aws-pam-simulation/actions/workflows/terraform.yml/badge.svg)


## 📌 Overview
This project simulates a Just-in-Time (JIT) Privileged Access Management (PAM) system using native AWS services. It demonstrates how to securely grant and monitor temporary elevated access to sensitive resources — a key principle in Zero Trust and cloud security engineering.

## 🎯 Objective
Implement and document a PAM workflow using:
- IAM roles with limited, scoped permissions
- IAM users without direct privileged access
- STS AssumeRole for temporary elevation
- CloudTrail for audit logging
- (Optional) Terraform or AWS CLI

## 🧱 Architecture
- **IAM Role**: `BackupAdminRole` – grants scoped S3 access
- **IAM User**: `caroline_user` – no direct access to sensitive resources
- **STS**: Enables `caroline_user` to assume the role temporarily
- **CloudTrail**: Captures all AssumeRole activity

## 🛠 Technologies Used
- AWS IAM, STS, S3, CloudTrail
- AWS CLI (optional)
- Terraform (optional)
- Markdown (for documentation)

## 🔐 Security Concepts Demonstrated
- Least Privilege Access
- Role-Based Access Control (RBAC)
- Temporary Elevation via STS
- Auditing with CloudTrail
- IAM Trust Policies

## 🚀 How It Works
1. Create a private S3 bucket: `confidential-backups-bucket`
2. Create IAM Role: `BackupAdminRole` with access only to that bucket
3. Create IAM User: `caroline_user` with no direct S3 permissions
4. Attach a policy to `caroline_user` that allows `sts:AssumeRole`
5. Use AWS CLI to assume the role temporarily
6. Verify access and capture CloudTrail logs

## 🧪 Sample AssumeRole Command
```bash
aws sts assume-role \
  --role-arn arn:aws:iam::<account_id>:role/BackupAdminRole \
  --role-session-name "CarolinePAMSession"
```

## 📂 Screenshots to Include
- IAM Role permission screenshot
- Trust relationship policy view
- IAM User policy with sts:AssumeRole
- CloudTrail log showing `AssumeRole` event

## 📘 What I Learned
- How to enforce PAM in AWS using native IAM
- Temporary privilege elevation using STS
- Monitoring elevated access with CloudTrail
- How to document access policies clearly

## 📄 License
MIT License
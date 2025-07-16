🛡️ AWS Project: Configure VPC Flow Logs and Store Logs in S3 Using IAM Role
📘 Overview
This project demonstrates how to enable VPC Flow Logs to capture detailed information about the IP traffic going to and from network interfaces in an AWS VPC. These logs are then delivered securely to an Amazon S3 bucket using a custom IAM role with appropriate permissions.

This setup enables long-term storage, centralized logging, and network traffic monitoring — which is essential for security auditing, performance analysis, and compliance.

🎯 Objective
✅ Enable VPC Flow Logs for a selected VPC.
✅ Store the logs in an Amazon S3 bucket.
✅ Use an IAM role to manage secure access between the VPC Flow Logs service and the bucket.
✅ Analyze and understand the log data structure

📌 Real-World Use Case
Imagine you run a company hosting applications inside a private network (VPC). To secure and audit your infrastructure, you want to track all incoming and outgoing network traffic. With VPC Flow Logs, you can now record every interaction in and out of your network. These logs are then sent to an S3 bucket where they are archived and available for analysis later.

🛠️ Step-by-Step Implementation
🔹 Step 1: Create a VPC
Created a VPC (vpc-flowlog-demo) in the N. Virginia region.
Subnets and default components were auto-generated.
🧠 Think of this as building a secure office building.

🔹 Step 2: Create an S3 Bucket
Bucket Name: vpc-flow-logs-bucket-rushikesh123
Disabled public access.
Enabled versioning (optional).
Folder structure auto-created by AWS Flow Logs: AWSLogs//vpcflowlogs/////
yaml Copy Edit

🧠 Think of this as a digital locker that stores CCTV recordings.  

🔹 Step 3: Create IAM Role for VPC Flow Logs
Trusted entity: vpc-flow-logs.amazonaws.com
IAM role name: vpc-flowlogs-to-s3-role
Purpose: Allow AWS to assume this role and write logs into the S3 bucket.

💡 What I Learned
1.How to capture and store network-level logs using VPC Flow Logs

2.How to secure S3 access using IAM roles and permissions

3.How AWS services interact through roles and policies

4.Importance of logging for security, troubleshooting, and auditing


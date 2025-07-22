 Configure VPC Flow Logs and Store Logs in S3 Using IAM Role

This project demonstrates how to configure **Amazon VPC Flow Logs** to monitor network traffic within a VPC and store the logs in an **Amazon S3 bucket** using an **IAM role** with appropriate permissions.

---

## 🧩 Project Objective

Enable flow logging on a VPC to capture IP traffic and deliver logs to an S3 bucket securely via IAM roles. This helps in network troubleshooting, auditing, and security analysis.

---

## ✅ Key Components

- 🛡️ **VPC Flow Logs**: Captures IP traffic data in your VPC
- 📦 **S3 Bucket**: Stores the generated flow log files
- 🔐 **IAM Role**: Grants VPC service permission to write logs to S3

---

## 🛠️ Prerequisites

- AWS account with admin or appropriate IAM permissions
- An existing VPC in your region
- AWS CLI configured OR AWS Console access

---

## 📁 Project Structure

```

vpc-flowlogs-s3/
├── create\_s3\_bucket.sh      # Script to create the S3 bucket
├── create\_iam\_role.sh       # Script to create IAM Role and attach policies
├── enable\_flow\_logs.sh      # Script to enable flow logs for a VPC
└── README.md                # Project documentation

````

---

## 🔧 Step-by-Step Setup

### 1️⃣ Create an S3 Bucket

Use the script or AWS Console to create a bucket:

```bash
bash create_s3_bucket.sh
````

Or manually:

* Go to S3 → Create bucket
* Name: `vpc-flow-logs-<your-unique-id>`
* Enable versioning (optional)
* Block all public access: ✅

---

### 2️⃣ Create IAM Role for Flow Logs

```bash
bash create_iam_role.sh
```

This script:

* Creates an IAM role with a trust policy for `vpc-flow-logs.amazonaws.com`
* Attaches `AmazonS3FullAccess` or a scoped custom policy

---

### 3️⃣ Enable VPC Flow Logs

```bash
bash enable_flow_logs.sh
```

Or from Console:

* Navigate to VPC → Your VPC → **Flow Logs** → Create Flow Log
* Destination: **Send to S3**
* IAM Role: Select the role you created
* Log Format: Default or custom
* Log Group: Optional (if using CloudWatch instead)

---

## 📂 S3 Log Output

Logs will be stored in the S3 bucket with a folder structure like:

```
s3://vpc-flow-logs-<id>/AWSLogs/<account-id>/vpcflowlogs/<region>/<year>/<month>/<day>/
```

Each file contains flow log records in plain text format.

---

## 🔍 Sample Flow Log Entry

```
version account-id interface-id srcaddr dstaddr srcport dstport protocol packets bytes start end action log-status
2       123456789012 eni-abc123  10.0.0.1  10.0.0.2  443     1024     6        5       2000   1594736400 1594736460 ACCEPT OK
```

```

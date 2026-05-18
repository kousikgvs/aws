# AWS with Python (boto3)

A hands-on project for interacting with AWS services — **EC2** and **S3** — using Python's `boto3` SDK and Jupyter Notebooks.

---

## Getting Started

### 1. Set Up the Virtual Environment

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

### 2. AWS Prerequisites

Before running any notebooks, make sure you've completed the following steps:

1. **Install boto3 and AWS CLI** — both are listed in `requirements.txt` and will be installed automatically.
2. **Create an IAM User** — go to the AWS Console and create a user with **Administrator Access**, or at minimum grant permissions for EC2 and S3.
3. **Generate Access Keys** — in the IAM user settings, create an **Access Key** for CLI usage. You'll get an *Access Key ID* and a *Secret Access Key* — keep these safe.
4. **Store credentials as environment variables** — never hardcode them in your code.
5. **Configure the AWS CLI** — run `aws configure` and provide your Access Key ID, Secret Access Key, and default region. This writes the credentials to `~/.aws/credentials`.

> **Note:** The `.pem` file is used for SSH access to EC2 instances. Your Access Key and Secret Key are what authenticate API calls for creating instances, S3 buckets, etc.

---

## EC2 — Elastic Compute Cloud

All EC2 code lives in [`AWS_EC2/code.ipynb`](AWS_EC2/code.ipynb).

The notebook walks through the full EC2 instance lifecycle:

- **Create a Key Pair** — generates an SSH key pair and saves the `.pem` file locally
- **Create an EC2 Instance** — launches a new instance with a specified AMI, instance type, and tags
- **Wait Until Running** — polls AWS until the instance reaches the `running` state and prints its public IP
- **Create a Security Group** — sets up a virtual firewall with custom inbound rules (e.g., SSH on port 22)
- **Attach a Security Group** — adds an existing security group to a running instance
- **Detach a Security Group** — removes a security group while keeping at least one attached
- **Check Instance Status** — fetches the current state and health checks for an instance
- **Start / Stop / Terminate** — full lifecycle control: resume billing, pause it, or permanently delete it

---

## S3 — Simple Storage Service

All S3 code lives in [`AWS_S3/code.ipynb`](AWS_S3/code.ipynb).

A local folder [`Sample/`](Sample/) is used as the test directory for all upload and download operations. It contains three sub-folders (`folder1`, `folder2`, `folder3`) with sample files.

The notebook covers:

1. **Create a Bucket** — creates a new globally unique S3 bucket in a specified region
2. **Upload a File** — uploads a single local file to the bucket with a custom S3 key
3. **List Objects** — lists all objects in the bucket along with their size and last modified date
4. **Download a File** — downloads a single S3 object back to your local machine
5. **Upload a Full Directory** — recursively uploads every file in `Sample/`, preserving the folder structure as S3 keys
6. **Download a Full Directory** — downloads all objects from the bucket and recreates the folder structure locally
7. **Delete All Files** — cleans up the bucket by removing all stored objects

---

## Project Structure

```
aws/
├── AWS_EC2/
│   └── code.ipynb        # EC2 operations notebook
├── AWS_S3/
│   └── code.ipynb        # S3 operations notebook
├── Sample/               # Test files used for S3 uploads/downloads
│   ├── file4
│   ├── folder1/file1
│   ├── folder2/file2
│   └── folder3/file3
├── notes/                # Setup notes and reference material
├── stop_all_services.py  # Utility to stop running AWS services
├── requirements.txt      # Python dependencies
└── README.md
```


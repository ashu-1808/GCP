# GCP Instance (Google Compute Engine) – Full Notes

## 1) Introduction

A GCP Instance is a Virtual Machine (VM) created using Google Compute Engine in Google Cloud.

It is an Infrastructure as a Service (IaaS) offering where you can create and manage virtual servers in Google’s data centers.

Similar Service in AWS: EC2
Similar Service in Azure: Virtual Machines

---

## 2) What is a GCP Instance?

A GCP instance is:

1. A virtual server running on Google Cloud
2. Used to host applications, websites, APIs, databases
3. Fully customizable (CPU, RAM, Disk, OS, Network)
4. Billed per second

---

## 3) Basic Architecture

```
Project
   └── VPC Network
        └── Subnet
             └── VM Instance
                  ├── Machine Type (CPU + RAM)
                  ├── Boot Disk
                  ├── Additional Disk
                  ├── Network Interface
                  ├── Public / Private IP
                  └── Firewall Rules
```

Everything in GCP runs inside a **Project**.
Each instance must belong to a **VPC network** and **Subnet**.

---

## 4) Components of a GCP Instance

### 1. Machine Type

Defines CPU and RAM.

Examples:

1. e2-medium
2. n2-standard-2
3. c2-standard-4
4. m1-ultramem

---

### 2. Boot Disk

Contains Operating System.

Supported OS:
1. Linux (Ubuntu, CentOS, Debian, RHEL)
2. Windows Server

Disk Types:
1. Standard Persistent Disk (HDD)
2. Balanced Persistent Disk
3. SSD Persistent Disk
4. Local SSD

---

### 3. Region and Zone

Region → Geographical area (e.g., asia-south1)
Zone → Data center inside region (e.g., asia-south1-a)

Important:

1. Instance is created in a specific zone.
2. High availability achieved by using multiple zones.

---

### 4. Networking

Each instance gets:
1. Internal IP (Private IP)
2. Optional External IP (Public IP)

Firewall rules are required to allow:

1. SSH (port 22)
2. HTTP (port 80)
3. HTTPS (port 443)
4. nfs (port 2049)
5. MySQL (port 3306)
---

### 5. Service Account

Used to allow VM to access other GCP services securely.
Example:
1. Access Cloud Storage
2. Access Cloud SQL
3. Access Pub/Sub

---

## 5) Types of Machine Families

### 1. General Purpose

Balanced CPU and memory
Use case: Web servers, application servers
Examples:
1. E2
2. N2
3. N1

---

### 2. Compute Optimized

High CPU
Use case: High-performance computing, gaming

Example:
- C2

---

### 3. Memory Optimized
High RAM
Use case: Databases, in-memory caching

Example:
- M1, M2

---

### 4. Shared Core
Low cost
Use case: Dev/Test, small apps

Example:
- e2-micro (Free tier eligible)

---

## 6) Instance Lifecycle
1. Provisioning
2. Running
3. Stopping
4. Terminated

Key Points:
1. Stop → No CPU billing (disk billing continues)
2. Delete → Instance removed permanently
3. You can resize machine type after stopping

---

## 7) Managed Instance Groups (MIG)
Used for:
1. Auto Scaling
2. High Availability
3. Load Balancing

Features:
1. Automatic scaling based on CPU
2. Health checks
3. Auto healing

---

## 8) GCP Instance Pricing
Billing is based on:
1. Machine type (CPU + RAM)
2. Disk type and size
3. Network usage
4. Region

Discounts available:
1. Sustained Use Discount
2. Committed Use Discount
3. Spot VM (low cost, can be terminated anytime)

---

## 9) Security Best Practices
1. Do not use default service account with full access
2. Use IAM roles properly
3. Enable OS Login
4. Restrict firewall rules
5. Use private IP when possible
6. Enable Shielded VM

---

## 10) How to Create GCP Instance (Console Steps)

![Image](https://docs.cloud.google.com/static/architecture/images/vpc-bps-native-firewall-rules.svg)

![Image](https://d33wubrfki0l68.cloudfront.net/57750035ef2c7221ce9bdece3154ff503d5fdc9c/a0271/gcpimages/02-architecture/00-public-private-subnet.png)

![Image](https://docs.cloud.google.com/static/architecture/images/vpc-bps-multi-nic-shared-vpc.png)

![Image](https://miro.medium.com/1%2A6HWT7WGREFABwDf8poEqCQ.jpeg)
1. Go to Compute Engine
2. Click Create Instance
3. Select Name
4. Select Region & Zone
5. Choose Machine Type
6. Select Boot Disk
7. Configure Firewall
8. Click Create

---

## 11) CLI Command Example
Create instance using gcloud:

```
gcloud compute instances create my-vm \
  --zone=asia-south1-a \
  --machine-type=e2-medium \
  --image-family=ubuntu-2204-lts \
  --image-project=ubuntu-os-cloud
```

---

## 12) Real-Time DevOps Example
Frontend VM → Nginx
Backend VM → Tomcat
Database → Cloud SQL
Load Balancer → HTTP Load Balancer
Auto Scaling → Managed Instance Group

---

## 13) Interview Important Points (Quick Revision)
1. GCP instance is a VM created using Compute Engine.
2. It runs inside a VPC network and subnet.
3. Billing is per second.
4. Supports auto scaling using Managed Instance Groups.
5. Machine type defines CPU and RAM.
6. Boot disk stores OS.
7. Region and Zone define location.
8. Can attach additional disks.
9. Stop instance to save compute cost.

---



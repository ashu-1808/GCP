# ☁️ GCP VPC (Virtual Private Cloud)

## 1) Introduction
Google Cloud VPC is a virtual network service provided by Google Cloud.

1. It allows you to create a private network in GCP.
2. All VM instances run inside a VPC.
3. It controls IP addressing, routing, and firewall rules.
4. It is a global resource (unlike AWS VPC which is regional).

---

## 2) What is VPC?
1. VPC stands for Virtual Private Cloud.
2. It is an isolated network environment in the cloud.
3. It allows secure communication between resources.
4. It provides control over networking and security.

---

## 3) Key Components of GCP VPC
### 1. Subnets
1. Subnets divide a VPC into smaller networks.
2. Subnets are regional.
3. Each subnet has a CIDR range (e.g., 10.0.0.0/24).

---

### 2. IP Addresses
1. Internal IP – Private communication inside VPC.
2. External IP – Public internet access.

---

### 3. Rout
1. Routes define how traffic moves inside the network.
2. Default route sends internet traffic to the internet gateway.

---

### 4. Firewall Rules
1. Control inbound and outbound traffic.
2. Stateful rules (return traffic automatically allowed).
3. Can allow ports like 22 (SSH), 80 (HTTP), 443 (HTTPS).

---

## 4) Types of VPC in GCP
### 1. Default VPC
1. Automatically created when project is created.
2. Has predefined subnets in each region.
3. Has default firewall rules.

---

### 2. Custom VPC
1. Manually created by user.
2. User defines subnets and IP ranges.
3. More secure and recommended for production.

---

## 5) Important Features
1. Global VPC architecture.
2. Automatic and custom subnet modes.
3. Private Google Access.
4. VPC Peering.
5. Shared VPC.
6. Cloud NAT for internet access without public IP.

---

## 6) VPC Peering
1. Connects two VPC networks privately.
2. Traffic does not go through the public internet.
3. Used for multi-project communication.

---

## 7) Shared VPC
1. One project hosts the VPC network.
2. Other projects use the same VPC.
3. Useful for large organizations.

---

## 8) Real-Time DevOps Example

1. Create Custom VPC.
2. Create subnet in asia-south1.
3. Deploy frontend VM in public subnet.
4. Deploy backend VM in private subnet.
5. Use Cloud SQL in private network.
6. Apply firewall rules to allow only required ports.

---

## 9) Interview Important Points

1. GCP VPC is global.
2. Subnets are regional.
3. Firewall rules are stateful.
4. Supports VPC peering and Shared VPC.
5. Every VM must be part of a VPC.

---

## 10) 1-Minute Interview Answer

GCP VPC is a global virtual network that allows us to securely connect resources like VM instances. It contains subnets, routes, firewall rules, and IP addresses. 
Subnets are regional, and firewall rules are stateful. It supports features like VPC peering, Shared VPC, and Cloud NAT for secure internet access.

---

# Steps to Create a VPS in GCP
In GCP, a VPS (Virtual Private Server) is created using Google Compute Engine inside Google Cloud.

---

## Method 1: Create VPS Using GCP Console (GUI)

![Image](https://docs.cloud.google.com/static/architecture/images/vpc-bps-native-firewall-rules.svg)

![Image](https://d33wubrfki0l68.cloudfront.net/57750035ef2c7221ce9bdece3154ff503d5fdc9c/a0271/gcpimages/02-architecture/00-public-private-subnet.png)

![Image](https://docs.cloud.google.com/static/architecture/images/vpc-bps-multi-nic-shared-vpc.png)

![Image](https://miro.medium.com/1%2A6HWT7WGREFABwDf8poEqCQ.jpeg)

### Step 1: Login
1. Go to Google Cloud Console.
2. Select or create a Project.

### Step 2: Enable Compute Engine
3. Go to Compute Engine → VM Instances.
4. Click “Enable API” if not already enabled.

### Step 3: Create VM Instance
5. Click “Create Instance”.
6. Enter instance name (e.g., my-vps).
7. Select Region and Zone.

### Step 4: Choose Configuration
8. Select Machine Type (e.g., e2-medium).
9. Choose Boot Disk (Ubuntu / Debian / CentOS).
10. Select disk size (e.g., 20GB).

### Step 5: Configure Networking
11. Select VPC network.
12. Allow HTTP/HTTPS traffic if needed.
13. Assign External IP (for public access).

### Step 6: Create
14. Click “Create”.
15. Wait for VM to start.

### Step 7: Connect
16. Click “SSH” to connect to your VPS.

---

## Method 2: Create VPS Using gcloud CLI

Run this command:

```bash
gcloud compute instances create my-vps \
  --zone=asia-south1-a \
  --machine-type=e2-medium \
  --image-family=ubuntu-2204-lts \
  --image-project=ubuntu-os-cloud \
  --boot-disk-size=20GB
```

After creation:

```bash
gcloud compute ssh my-vps --zone=asia-south1-a
```

---

## Important Points for Interview

1. VPS in GCP is a VM created using Compute Engine.
2. It must be created inside a VPC network.
3. Choose correct machine type based on workload.
4. Attach external IP for internet access.
5. Configure firewall rules for ports (22, 80, 443).

---

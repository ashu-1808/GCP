# GCP Filestore – Complete Notes

## 1) Introduction
1. Google Cloud Filestore is a fully managed NFS (Network File System) service provided by Google Cloud.
2. It provides shared file storage for applications running on Google Compute Engine, Google Kubernetes Engine, and other GCP services.
3. It is similar to AWS EFS.

---

## 2) What is Filestore?
1. Managed file storage service.
2. Uses NFS protocol.
3. Provides shared storage across multiple VMs.
4. Fully managed by Google with no hardware management.

---

## 3) Why We Use Filestore?
1. Multiple VMs need access to the same files.
2. Applications require shared storage.
3. CMS applications such as WordPress and Drupal.
4. Media rendering workloads.
5. Machine learning workloads.
6. Example: Frontend VMs need access to the same uploaded images, so Filestore is used.

---

## 4) How Filestore Works

```id="k3m2sa"
VPC Network
   ├── VM Instance 1
   ├── VM Instance 2
   └── Filestore (NFS Server)
           └── Shared File System
```

1. Filestore creates a managed NFS server.
2. VMs mount the Filestore using a private IP.
3. Data is stored centrally and shared across instances.

---

## 5) Filestore Service Tiers

1. Basic HDD

   1. Low cost.
   2. Suitable for development and low IOPS workloads.

2. Basic SSD

   1. Higher performance than HDD.
   2. Suitable for general production workloads.

3. Enterprise

   1. High availability.
   2. Regional storage.
   3. Automatic failover.

4. High Scale SSD

   1. Very high performance.
   2. Suitable for large workloads and analytics.

---

## 6) Key Features
1. Fully managed NFS service.
2. High performance.
3. Automatic scaling depending on tier.
4. Integrated with VPC.
5. Backup support.
6. Snapshot support.

---

## 7) Networking in Filestore
1. Filestore gets a private IP.
2. Must be in the same VPC as VM.
3. Access via NFS on port 2049.
4. Firewall must allow NFS traffic.

---

## 8) Mounting Filestore on Linux VM
1. Install NFS client.

```id="c9sd20"
sudo apt update
sudo apt install nfs-common -y
```

2. Create mount directory.

```id="c7ks82"
sudo mkdir /mnt/filestore
```

3. Mount Filestore.

```id="a2jd91"
sudo mount <FILESTORE_IP>:/<SHARE_NAME> /mnt/filestore
```

4. Verify mount.

```id="l2hs88"
df -h
```

---

## 9) Filestore vs Persistent Disk
1. Filestore is shared across multiple VMs.
2. Filestore uses NFS protocol.
3. Filestore is a managed service.
4. Persistent Disk is attached to a single VM by default.
5. Persistent Disk is block storage.
6. Persistent Disk is not easily shared.

---

## 10) Pricing Factors
1. Storage capacity (GB or TB).
2. Service tier.
3. Region.
4. Backup storage.
5. Enterprise tier costs more due to high availability.

---

## 11) Security Best Practices
1. Use private IP only.
2. Restrict firewall rules.
3. Use IAM properly.
4. Enable backups.
5. Monitor usage.

---

## 12) Real-Time DevOps Example
1. Three web servers in a Managed Instance Group.
2. Shared media files stored in Filestore.
3. Load Balancer in front.
4. Cloud SQL used as database.
5. If one VM fails, others still access shared files.

---

## 13) Interview Important Points
1. Filestore is a managed NFS service in GCP.
2. Used for shared file storage.
3. Works inside VPC network.
4. Supports multiple service tiers.
5. Used with Compute Engine and GKE.
6. Accessible via private IP using NFS.

---


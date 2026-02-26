# 📦 Cloud Storage – GCP Detailed Notes (DevOps + Interview Focus)

## 📌 What is Cloud Storage?

**Cloud Storage** in **Google Cloud Platform** is a **scalable, durable, and highly available object storage service**.

It is used to store:

* Images
* Videos
* Backups
* Logs
* Static website files
* Big data files

---

# 🗂 1️⃣ Cloud Storage Basics

### 🔹 Object Storage Model

Cloud Storage stores data as:

```id="obj123"
Bucket → Object → Data
```

* **Bucket** = Container
* **Object** = File stored inside bucket
* **Data** = Actual file content

Example:

```id="obj456"
Bucket: dev-backup-bucket
Object: database-backup.sql
```

---

# 🏷 2️⃣ Buckets

### 📌 Bucket Features

* Globally unique name
* Created in specific region
* No folders (uses object prefix like folder structure)
* Cannot rename bucket (must recreate)

---

## 🌍 Bucket Location Types

| Type         | Description      | Example              |
| ------------ | ---------------- | -------------------- |
| Region       | Single region    | Mumbai (asia-south1) |
| Dual-Region  | Two regions      | Mumbai + Delhi       |
| Multi-Region | Multiple regions | Asia                 |

---

# 💾 3️⃣ Storage Classes

Different storage classes based on access frequency:

| Storage Class | Access Frequency | Storage Cost | Retrieval Cost | Minimum Duration | Use Case               |
| ------------- | ---------------- | ------------ | -------------- | ---------------- | ---------------------- |
| Standard      | Frequent         | High         | No             | None             | Active data            |
| Nearline      | Monthly          | Lower        | Yes            | 30 days          | Backup                 |
| Coldline      | Quarterly        | Very Low     | Higher         | 90 days          | Disaster Recovery (DR) |
| Archive       | Yearly           | Lowest       | Highest        | 365 days         | Long-term archive      |



👉 More access = Higher cost
👉 Less access = Lower storage cost but retrieval cost applies

---

# 🔐 4️⃣ Access Control (IAM + ACL)

Cloud Storage uses:

* IAM Roles (recommended)
* Access Control Lists (legacy)

### Common IAM Roles for Storage:

* `roles/storage.admin`
* `roles/storage.objectAdmin`
* `roles/storage.objectViewer`
* `roles/storage.objectCreator`

---

# 🏢 5️⃣ Cloud Storage Architecture

![Image](https://www.researchgate.net/publication/282952784/figure/fig1/AS%3A798945747951616%401567494918015/Generic-cloud-storage-architecture.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/GCS_Folders_Product_Slides.max-2200x2200.jpg)

![Image](https://docs.cloud.google.com/static/solutions/images/best-practices-compute-engine-region-selection-5multiparallel.svg)

![Image](https://docs.cloud.google.com/static/docs/images/overview/regions-zones.svg)

---

# 🔄 6️⃣ Object Versioning

### 📌 What is Versioning?

Allows multiple versions of the same object.

If file is overwritten:

* Old version is retained
* Can restore previous version

Enable versioning:

```id="v1cmd"
gsutil versioning set on gs://bucket-name
```

---

# ⏳ 7️⃣ Lifecycle Management

Automatically move or delete objects.

Example Rules:

* Move from Standard → Nearline after 30 days
* Delete object after 365 days

Used for:

* Cost optimization
* Backup retention policies

---

# 🔐 8️⃣ Security Features

✔ IAM integration
✔ Uniform bucket-level access
✔ Encryption at rest (default)
✔ Customer-managed encryption keys (CMEK)
✔ Signed URLs (temporary access)

---

# 🔎 9️⃣ Common gsutil Commands

### Create bucket:

```id="cmd1"
gsutil mb -l asia-south1 gs://my-bucket-name
```

### Upload file:

```id="cmd2"
gsutil cp file.txt gs://my-bucket-name
```

### Download file:

```id="cmd3"
gsutil cp gs://my-bucket-name/file.txt .
```

### List objects:

```id="cmd4"
gsutil ls gs://my-bucket-name
```

---

# 🌐 1️⃣0️⃣ Hosting Static Website

Cloud Storage can host:

* HTML
* CSS
* JS files

Steps:

1. Create bucket
2. Make bucket public
3. Upload index.html
4. Enable website configuration

---

# 🔄 1️⃣1️⃣ Data Transfer Options

* gsutil
* Console upload
* Storage Transfer Service
* Transfer Appliance (large data migration)
* S3 interoperability

---

# 🏗 1️⃣2️⃣ Real-Time DevOps Use Cases

Since you’re preparing for DevOps:

| Use Case       | Example                |
| -------------- | ---------------------- |
| Backup         | Store DB backups       |
| CI/CD          | Store build artifacts  |
| Logs           | Store application logs |
| Static Website | Host frontend          |
| Data Lake      | Store big data files   |

Example:
Jenkins pipeline uploads build artifacts to Cloud Storage bucket.

---

# 💰 1️⃣3️⃣ Pricing Factors

Cost depends on:

* Storage class
* Data retrieval
* Network egress
* Operations (PUT, GET)

---

# ⚔ Cloud Storage vs AWS S3

| Feature         | GCP Cloud Storage | AWS S3         |
| --------------- | ----------------- | -------------- |
| Storage Type    | Object storage    | Object storage |
| IAM Control     | IAM-based         | IAM-based      |
| Lifecycle Rules | Yes               | Yes            |
| Versioning      | Yes               | Yes            |

---

# 🎯 Important Interview Points

* Cloud Storage is object storage.
* Data stored as bucket → object.
* 4 Storage classes.
* IAM controls access.
* Versioning prevents accidental deletion.
* Lifecycle rules optimize cost.
* Highly durable (11 9’s durability).

---

If you want next:

* 📘 Cloud Storage Interview Questions
* 🔥 Hands-on Lab steps
* 📊 Comparison: Persistent Disk vs Cloud Storage
* ⚙ Cloud Storage architecture deep explanation

Tell me 👍

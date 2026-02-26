# 📘 IAM in GCP – Full Detailed Notes (Complete Revision Guide)

## 🔐 What is IAM in GCP?

In Google Cloud Platform,
IAM (Identity and Access Management) is used to control Who (Identity) can do What (Role/Permission) on Which Resource
IAM is a policy-based access control system.

---

# 🎯 Why IAM is Important?
1. Secure cloud resources
2. Control user access
3. Follow Least Privilege principle
4. Enable compliance & auditing
5. Prevent unauthorized changes

---

# 🧩 1️⃣ Core Components of IAM
IAM has 3 main components:

---

## 1️⃣ Identity (Who?)
An Identity is a user or system that needs access.

### Types of Identities:
1. Google Account ([user@gmail.com](mailto:user@gmail.com))
2. Service Account (used by applications/VMs)
3. Google Group
4. Cloud Identity domain

---

## 2️⃣ Role (What can they do?)

### 📌 Role = Collection of Permissions

### 📌 Permission = Single Action

Permission format:

```
service.resource.verb
```

Examples:

1. `compute.instances.create`
2. `storage.objects.delete`
3. `bigquery.tables.get`

Instead of assigning permissions individually, we assign a Role.

---

### 🔹 Types of Roles in GCP
### 1️⃣ Basic Roles (Primitive Roles)
| Role   | Access Level             |
| ------ | ------------------------ |
| Owner  | Full access + manage IAM |
| Editor | Modify resources         |
| Viewer | Read-only access         |

⚠ Not recommended in production (too broad access)

---

### 2️⃣ Predefined Roles (Most Used)
Google-created roles for specific services.
Examples:
1. `roles/compute.admin`
2. `roles/storage.admin`
3. `roles/container.admin`
4. `roles/iam.serviceAccountUser`
5. `roles/viewer`

✅ Best practice: Use predefined roles.

---

### 3️⃣ Custom Roles
User-created roles with selected permissions.

Used when:
1. Predefined roles give too many permissions
2. You need strict least-privilege access

Example:
Custom role allowing:
a. Start VM
b. Stop VM
  But not delete VM.

---

## 3️⃣ Resource (On what?)

GCP resources follow a hierarchy:

![Image](https://d33wubrfki0l68.cloudfront.net/eaddeba5e864fe63444fe247f7a7277b427e42c2/ed88b/gcpimages/02-architecture/resource-hierarchy-overview.png)

![Image](https://docs.cloud.google.com/static/iam/img/policy-inheritance.svg)

### Hierarchy Structure:
```
Organization
   ↓
Folder
   ↓
Project
   ↓
Resources (VM, Storage, DB, etc.)
```

🔽 Permissions inherit downward.
If a role is assigned at:
1. Organization → Applies to all projects
2. Project → Applies to all resources inside project

---

#  2️⃣ IAM Policy Structure
IAM Policy consists of:
```
Member + Role + Resource
```

Example:
```
Member: user:dev@gmail.com
Role: roles/compute.viewer
Resource: Project-Dev
```

Meaning: User can view compute resources in Project-Dev.

---

#  3️⃣ Service Accounts (Very Important)
### What is Service Account?

A Service Account is used by applications or services to interact with GCP.

Examples:
1. VM accessing Cloud Storage
2. Cloud Function accessing BigQuery
3 CI/CD pipeline deploying to GKE

Important Points:
1. Has email format
2. Assigned IAM roles
3. Should follow least privilege
4. Avoid long-lived service account keys
5. Prefer Workload Identity (more secure)

---

#  4️⃣ IAM Conditions (Advanced Concept)

IAM allows conditional access.
Example:
1. Allow access only during business hours
2. Allow access from specific IP range

This adds extra security layer.

---

#  5️⃣ Policy Inheritance Model
If role assigned at higher level:
| Level        | Effect                                  |
| ------------ | --------------------------------------- |
| Organization | Applies to all folders & projects       |
| Folder       | Applies to all projects inside folder   |
| Project      | Applies to all resources inside project |

Access always flows downward.

---

#  6️⃣ Principle of Least Privilege
Give only necessary permissions.
❌ Don’t assign Owner role unnecessarily
✅ Assign specific service roles

Example:
Instead of Owner → use `roles/compute.instanceAdmin`

---

#  7️⃣ Common GCP IAM Commands
### View IAM policy:
```
gcloud projects get-iam-policy PROJECT_ID
```

### Add IAM binding:
```
gcloud projects add-iam-policy-binding PROJECT_ID \
  --member="user:abc@gmail.com" \
  --role="roles/viewer"
```

### List roles:
```
gcloud iam roles list
```

### Describe role:
```
gcloud iam roles describe roles/compute.admin
```
---

# 🏢 8️⃣ Real-Time DevOps Example
Since you are preparing for DevOps roles, remember this:
| Role                 | Assigned To     |
| -------------------- | --------------- |
| Viewer               | Developer       |
| Compute Admin        | DevOps Engineer |
| Storage Object Admin | Backup system   |
| Service Account User | CI/CD pipeline  |

Example:
Jenkins service account → `roles/container.developer` for GKE deployment.

---

# 📋 9️⃣ IAM Best Practices
1.✔ Use predefined roles
2.✔ Avoid basic roles in production
3.✔ Enable Audit Logs
4.✔ Rotate service account keys
5.✔ Use IAM Recommender
6.✔ Implement least privilege
7.✔ Use groups instead of individual users

---

# ⚔ 1️⃣0️⃣ GCP IAM vs AWS IAM (Quick Comparison)
| Feature         | GCP IAM                         | AWS IAM              |
| --------------- | ------------------------------- | -------------------- |
| Structure       | Organization → Folder → Project | Account based        |
| Role Assignment | Direct binding                  | Attach to user/group |
| Policy Type     | JSON-based                      | JSON-based           |

---

# 🎯 Important Interview Points
1. IAM = Who + What + Resource
2. Role = Group of permissions
3. Permission = Single action
4. 3 Types of roles: Basic, Predefined, Custom
5. Inheritance works top-down
6. Service Accounts are used for workloads
7. Follow least privilege

---


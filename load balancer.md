# ☁️ GCP Load Balancer – Complete Notes

## 1) Introduction

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/GCLB_3.max-1400x1400.png)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/ui-11tt7v.max-700x700.PNG)

![Image](https://cdn.qwiklabs.com/k3u04mphJhk%2F2yM84NjgPiZHrbCuzbdwAQ98vnaoHQo%3D)

![Image](https://storage.googleapis.com/gweb-cloudblog-publish/images/image001rx5.max-700x700.PNG)

Cloud Load Balancing is a fully managed load balancing service provided by Google Cloud.

1. It distributes traffic across multiple backend instances.
2. It improves availability and reliability.
3. It supports global and regional load balancing.
4. It automatically scales based on traffic.

---

## 2) Why We Use Load Balancer
1. To distribute traffic across multiple servers.
2. To avoid single point of failure.
3. To increase application availability.
4. To improve performance and scalability.

Example:
If 3 VM instances are running a website, load balancer distributes user traffic equally among them.

---

## 3) Types of GCP Load Balancers
### 1️⃣ HTTP(S) Load Balancer (Global)
1. Layer 7 load balancer.
2. Supports URL-based routing.
3. Supports SSL termination.
4. Used for web applications.

---

### 2️⃣ TCP/SSL Load Balancer
1. Layer 4 load balancer.
2. Used for non-HTTP traffic.
3. Supports SSL proxy.

---

### 3️⃣ Internal Load Balancer
1. Used for private communication inside VPC.
2. Not accessible from the internet.
3. Used for backend microservices.

---

### 4️⃣ Network Load Balancer
1. Regional.
2. Pass-through load balancing.
3. Used for high-performance TCP/UDP traffic.

---

## 4) How GCP Load Balancer Works
1. User sends request to public IP of Load Balancer.
2. Load Balancer forwards traffic to backend service.
3. Backend service contains instance group.
4. Health checks monitor instance health.
5. Unhealthy instances are automatically removed.

---

## 5) Components of Load Balancer
1. Frontend Configuration (IP + Port).
2. Backend Service (VM instances or instance group).
3. Health Check.
4. URL Map (for HTTP load balancer).
5. Target Proxy.
6. Forwarding Rule.

---

## 6) Real-Time DevOps Example
1. Create Managed Instance Group with 3 VMs.
2. Install Nginx on each VM.
3. Create HTTP Load Balancer.
4. Configure health check on port 80.
5. Attach instance group to backend service.
6. Access website using Load Balancer public IP.

If one VM fails → traffic automatically shifts to healthy VMs.

---

## 7) Key Features

1. Global load balancing (unique feature).
2. Auto-scaling integration.
3. SSL certificate support.
4. CDN integration.
5. DDoS protection via Google’s global network.

---

## 8) Interview Important Points
1. GCP Load Balancer is fully managed.
2. HTTP(S) Load Balancer is global and Layer 7.
3. Network Load Balancer is Layer 4.
4. Health checks remove unhealthy instances.
5. Works with Managed Instance Groups.

---

## 9) 1-Minute Interview Answer

GCP Load Balancer is a fully managed service that distributes incoming traffic across multiple backend instances.
It supports global HTTP(S) load balancing at Layer 7 and TCP/UDP load balancing at Layer 4. It integrates with Managed Instance Groups and performs health checks to ensure high availability. 
It automatically scales and improves application reliability.

---



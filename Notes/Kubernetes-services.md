
### 📘 Kubernetes: Deployments & Services

## 🔹 Deployments in Kubernetes

* In **production scenarios**, a **Deployment** is typically used instead of creating Pods directly.
* A Deployment can manage **multiple replicas of a Pod** to handle large numbers of concurrent users.
* The **number of replicas** depends on:

  * Number of users
  * Number of requests a single Pod can handle
* **Auto-healing:**
  If a Pod goes down, Kubernetes automatically creates a new one.
* **Problem:** New Pods may get different IP addresses → causing issues for users accessing the app.

---

## 🔹 Services in Kubernetes

* **Solution:** A **Service** is created on top of a Deployment.
* Provides:

  * **Stable IP address** for access
  * **Load balancing** across Pods
  * **Service discovery** using labels & selectors instead of Pod IPs

### ⚙️ How Services Work

* Uses **kube-proxy** to forward requests to available Pods.
* Users can access the application with a stable DNS-like name, e.g.,

  ```
  payment.default.svc
  ```
* **Benefits:**

  * Load balancing
  * Service discovery (no need to track changing Pod IPs)
  * External access (expose apps outside the cluster)

---

## 🔹 Types of Kubernetes Services

### 1. **ClusterIP (default)**

* Provides access **within the cluster only**.
* Used for internal communication between services.
* Offers **service discovery** + **load balancing**.

### 2. **NodePort**

* Exposes the service on a **port of each node** in the cluster.
* Can be accessed from **outside the cluster**, but usually within a **VPC** or restricted network.

### 3. **LoadBalancer**

* Creates a **public IP** accessible from **anywhere on the internet**.
* Ideal for production-grade, internet-facing applications.
* Works only with supported **cloud providers** (e.g., AWS, GCP, Azure).
* Example: a service accessible like a public website (`amazon.com`).

| Concept                  | Real-life Analogy                                      | Role                                                 |
| ------------------------ | ------------------------------------------------------ | ---------------------------------------------------- |
| **Pod**                  | Employee in a department                               | Does the actual work                                 |
| **Service**              | Department front desk                                  | Keeps the same contact info even if employees change |
| **ClusterIP Service**    | Internal extension (used only inside the office)       |                                                      |
| **NodePort Service**     | Public phone number (can be reached from outside)      |                                                      |
| **LoadBalancer Service** | External receptionist (uses an external load balancer) |                                                      |

---

## ✅ Summary

* **Deployment** = Manages Pods + replicas + auto-healing.
* **Service** = Provides stable access, load balancing, and discovery.
* **Service Types:**

  * ClusterIP → Internal access
  * NodePort → Restricted external access
  * LoadBalancer → Public external access

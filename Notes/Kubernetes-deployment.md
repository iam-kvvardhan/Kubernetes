### 📌 Kubernetes: Pods, Deployments & ReplicaSets

### 🔹 Pods

- A Pod is the smallest deployable unit in Kubernetes.
- It can run one or multiple containers together.
- Containers in a Pod share:

    - Networking (same IP address, localhost communication).
    - Storage (shared volumes).
- Limitations of Pods:
    - No auto-healing → if a pod fails, it won’t restart automatically.
    - No auto-scaling → cannot handle varying workloads automatically.

  ---

### 🔹 Deployments

- A Deployment is a higher-level Kubernetes resource used to manage Pods.

- Features:

    - Auto-healing → if a pod crashes, it is automatically recreated.
    - Auto-scaling (with HPA – Horizontal Pod Autoscaler).
    - Ensures the desired number of replicas are always running.- 
- Best practice: Always use Deployments instead of creating Pods directly.
- Deployments create and manage ReplicaSets in the background.
### IMP COMMANDS
- kubectl apply -f deploymentfilename.yml
- kubectl get deployments
- kubectl get pods
- kubectl scale deployment/filename --replicas=5
- kubectl exec -it podname -- /bin/bash/  - To login to POD
---

### 🔹 ReplicaSets

- A ReplicaSet is a Kubernetes controller that ensures a specified number of Pod replicas are running.

Responsibilities:

    - Maintain the desired state → if a pod is deleted, a new one is created.
    - Implement auto-healing by recreating missing pods.
A Deployment automatically creates a ReplicaSet, which in turn manages Pods.

---

### 🔹 How They Work Together

1. You create a Deployment (e.g., for an Nginx app).
2. The Deployment creates a ReplicaSet.
3. The ReplicaSet ensures the desired number of Pods are running.
4. If a Pod is deleted → ReplicaSet recreates it.
5. If you scale replicas up or down in the Deployment, → ReplicaSet adjusts Pods accordingly.

---

### 🔹 Practical Example

- Define a Deployment YAML with 3 replicas of Nginx.

Kubernetes will:
    - Create a ReplicaSet.
    - ReplicaSet ensures 3 Pods are always running.

- If one Pod crashes → ReplicaSet replaces it.

- If replicas are increased to 5 → ReplicaSet creates 2 more Pods.
---
### ✅ Summary:

- Pod → Smallest unit, runs containers, but no healing/scaling.

- ReplicaSet → Ensures the desired number of Pods, handles healing.

Deployment → Manages ReplicaSets, provides updates, scaling, and rollback.

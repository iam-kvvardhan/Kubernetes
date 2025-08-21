### 🧠 Master Node (Control Plane)
- **API Server**: Entry point for all REST commands to control the cluster.
- **Scheduler**: Assigns work to nodes based on resources.
- **etcd**: A consistent and highly available key-value store for cluster data.
- **Controller Manager**: Ensures the desired state of the cluster matches the current state.
- **Cloud Controller Manager**: Manages cloud-specific control logic (e.g., load balancers, volumes).

---

### 💪 Worker Node
- **Kubelet**: Agent that ensures containers are running.
- **Kube Proxy**: Handles networking and load balancing.
- **Container Runtime**: Software used to run containers (e.g., containerd, Docker).

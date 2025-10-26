🏙️ Imagine Kubernetes as a big company (organization)

This company runs many projects (applications).
To manage everything smoothly, it has two main parts:

🧠 The Management Team (Control Plane)
🏭 The Workers (Worker Nodes)

### 🧠 Master Node (Control Plane):

This team doesn’t do the work itself — it just decides what should happen, monitors progress, and makes sure everything is running correctly.

| Component              | Real-Life Role                 | What It Does                                                                                                                                      |
| ---------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **API Server**         | 🧑‍💼 The **Reception Desk**   | The main entry point — everyone (including you!) talks to Kubernetes through this. It receives orders (“Deploy this app!”) and passes them along. Entry point for all REST commands to control the cluster|
| **Scheduler**          | 🧭 The **HR Manager**          | Decides which worker (node) should handle which job (Pod). Assigns work to nodes based on resources..                                                                                        |
| **Controller Manager** | 🕹️ The **Operations Manager** | Constantly checks if everything is as planned (“Do we still have 3 Pods running?”). If not, it fixes things automatically. Ensures the desired state of the cluster matches the current state.                       |
| **etcd**               | 📚 The **Records Department**  | Stores all company data — apps, users, configurations, etc. It’s like the company’s brain/memory. A consistent and highly available key-value store for cluster data.                                                 |



---

### 💪 Worker Node
- **Kubelet**: Agent that ensures containers are running.
- **Kube Proxy**: Handles networking and load balancing.
- **Container Runtime**: Software used to run containers (e.g., containerd, Docker).

<img width="567" height="529" alt="image" src="https://github.com/user-attachments/assets/06a662ca-34a6-4288-9744-9085c980ee26" /><img width="977" height="409" alt="image" src="https://github.com/user-attachments/assets/da6bf022-8ebd-44a6-a04c-9a3c4e8549e6" />🏙️ Imagine Kubernetes as a big company (organization)

This company runs many projects (applications).
To manage everything smoothly, it has two main parts:

🧠 The Management Team (Control Plane)
🏭 The Workers (Worker Nodes)

### 🧠 Master Node (Control Plane):

This team doesn’t do the work itself — it just decides what should happen, monitors progress, and makes sure everything is running correctly.


Component	Real-Life Role	What It Does
API Server	🧑‍💼 The Reception Desk	The main entry point — everyone (including you!) talks to Kubernetes through this. It receives orders (“Deploy this app!”) and passes them along.
Scheduler	🧭 The HR Manager	Decides which worker (node) should handle which job (Pod).
Controller Manager	🕹️ The Operations Manager	Constantly checks if everything is as planned (“Do we still have 3 Pods running?”). If not, it fixes things automatically.
etcd	📚 The Records Department	Stores all company data — apps, users, configurations, etc. It’s like the company’s brain/memory.
<img width="376" height="529" alt="image" src="https://github.com/user-attachments/assets/4b7d1cc9-4e5e-43a3-9c26-62e5ac8f7d11" />


---

### 💪 Worker Node
- **Kubelet**: Agent that ensures containers are running.
- **Kube Proxy**: Handles networking and load balancing.
- **Container Runtime**: Software used to run containers (e.g., containerd, Docker).

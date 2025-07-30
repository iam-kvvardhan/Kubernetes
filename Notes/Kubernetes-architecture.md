**Master Node:**

**API Server**: It is used to accept the request from the user and store the request in ETCD.
**ETCD**: It is like a database for our k8s. It is used to store the requests from the API Server in
the KEY-VALUE format.
**Scheduler**: It is used to search pending tasks that are present in ETCD. If any pending
tasks are found in ETCD, they will be scheduled on the worker node. It will decide in which worker node
our task should be executed. It will be decided by communication with the kubelet on the worker
node.
**Controllers**: They are used to perform the operations which is scheduled by the scheduler. It
will control the containers creation in worker nodes.
**Cloud Controller Manager**: interacts with cloud provider APIs

**Worker Node:**

**kubelet**: Agent ensures that the pod is running or not.
**kube-proxy**: It is used to maintain a network connection between worker and manager
nodes.
**Container Runtime**: runs the actual containers (e.g., Docker, containerd)
**pod**: A group of one or more containers.
**container**: It is a virtual machine that does not have an OS. It is used to run the
applications in worker nodes.




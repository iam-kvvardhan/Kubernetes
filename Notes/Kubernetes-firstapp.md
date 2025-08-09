Install kubectl CLT (command line tool) and provide permission to the kubectl file - sudo chmod +x /usr/local/bin/kubectl

Install minikube - http://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download

After installing, create a pod.yaml file and copy the sample NGINX yaml code and paste it into that file - https://kubernetes.io/docs/concepts/workloads/pods/

Now start the minikube using the command **minikube start**

Check the node is in ready status using the command **kubectl get nodes**

Create the POD using the command **kubectl create -f pod.yml**

After creating, check the status information of the POD using the command **kubectl get pods -o wide**

Now we can login to the minikube by using **minikube ssh**

Inside that, using the command **curl IPaddress**, we can see the display Welcome to NGINX.

To check the full status of the POD, we can use **kubectl describe pod nginx** 

To check logs, **kubectl logs nginx**

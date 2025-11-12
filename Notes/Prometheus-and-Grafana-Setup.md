### 📊 Prometheus and Grafana Setup on Kubernetes
🧭 Objective

To monitor the Kubernetes cluster and visualize metrics using Prometheus and Grafana.

Monitoring is a critical part of DevOps. In this setup, we’ll deploy **Prometheus** and **Grafana** on a Kubernetes cluster using **Helm**, visualize cluster metrics, and access the dashboards.

---

**🧱 Step 1: Install Helm**

Helm is used to install Prometheus and Grafana easily through predefined charts.
```
sudo snap install helm --classic
```
💡 If you face a warning about “classic confinement,” adding --classic is safe here because Helm requires full system access to manage Kubernetes resources.

**🧩 Step 2: Add Prometheus Helm Repository**
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```
**🚀 Step 3: Install Prometheus**

helm install prometheus prometheus-community/prometheus
```
helm install prometheus prometheus-community/prometheus
```
Once installed, check all Prometheus resources:
```
kubectl get all
```

You’ll see pods, services, configmaps, and deployments related to Prometheus.


**🔍 Step 4: Access Prometheus Dashboard**

Port-forward the Prometheus server service to your local machine:
```
kubectl port-forward svc/prometheus-server 9090:80
```

Now, visit your browser at
👉 http://localhost:9090

If you see an error like
`Error listen tcp4 127.0.0.1:9090: bind: address already in use,`
it means the port is already occupied. Try forwarding to a different port, for example:
```
kubectl port-forward svc/prometheus-server 9091:80
```

**⚙️ Step 5: Install Grafana**

Grafana will be used to visualize the Prometheus data.
```
helm install grafana prometheus-community/grafana
```

Check Grafana’s resources:
```
kubectl get all
```

**🌐 Step 6: Access Grafana Dashboard**

Port-forward Grafana service to your local port:
```
kubectl port-forward svc/grafana 3000:80
```

Now open your browser at
👉 http://localhost:3000

**🔑 Step 7: Get Grafana Admin Password**

Retrieve the default admin password from the Grafana secret:
```
kubectl get secret grafana -o jsonpath="{.data.admin-password}" | base64 --decode
```

Default username: admin


**🧮 Step 8: Add Prometheus as a Data Source in Grafana**

Go to Grafana → Connections → Data sources

Click Add data source → Select Prometheus

In the URL field, enter:

`http://prometheus-server`


Click Save & Test

You should see a success message confirming Grafana can communicate with Prometheus.


**📈 Step 9: Import Kubernetes Dashboard**

Grafana provides pre-built dashboards for monitoring clusters.

Go to Dashboards → Import

Enter dashboard ID: 3226

Choose Prometheus as the data source

Click Import

✅ You’ll now see live visualizations of Kubernetes metrics such as:

1. Node CPU and Memory usage

2. Pod-level metrics

3. Cluster health overview

4. Resource consumption trends

**⚠️ Step 10: Common Errors & Fixes**
Error	Reason	Fix
address already in use	Port 9090/3000 is occupied	Use a different local port (9091/3001)
connection refused	Prometheus not running or port-forward stopped	Restart port-forward command
Grafana “no data”	Data source misconfigured	Recheck Prometheus URL in Grafana settings

🎯 Outcome

1. Successfully deployed Prometheus and Grafana using Helm

2. Visualized Kubernetes metrics through Grafana Dashboard ID 3226

3. Gained observability into nodes, pods, and cluster health

🖼️ Visualization Example

Diagrams/Prometheus-Grafana-dashboard.png

🧠 Key Takeaways

1. Prometheus handles metrics scraping and storage

2. Grafana visualizes the data using dashboards

3. Helm simplifies installation and upgrades

4. Always verify services using kubectl get svc before port-forwarding


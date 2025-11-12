### 📊 Prometheus and Grafana Setup on Kubernetes
🧭 Objective

To monitor the Kubernetes cluster and visualize metrics using Prometheus and Grafana.

### 🧱 Step 1: Install Helm

Helm is used to install Prometheus and Grafana easily through predefined charts.
# 📊 Monitoring Kubernetes with Prometheus & Grafana

Monitoring is a critical part of DevOps. In this setup, we’ll deploy **Prometheus** and **Grafana** on a Kubernetes cluster using **Helm**, visualize cluster metrics, and access the dashboards.

---

## 🚀 Step 1: Add and Update Helm Repositories

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
⚙️ Step 2: Install Prometheus
helm install prometheus prometheus-community/prometheus


Once installed, verify Prometheus services:

kubectl get svc

🌐 Step 3: Expose Prometheus

By default, Prometheus runs as a ClusterIP service (internal access only).
To access it externally, expose it as a NodePort service:

kubectl expose service prometheus-server \
  --type=NodePort \
  --target-port=80 \
  --name=prometheus-server-ext


Check the NodePort:

kubectl get svc


If you’re using Minikube, get its IP:

minikube ip


Then try accessing Prometheus using:

http://<minikube-ip>:<node-port>


If it doesn’t load, you can use port-forwarding (recommended for Docker driver users):

kubectl port-forward svc/prometheus-server 9090:80


Now open your browser:

http://localhost:9090


🎉 You should now see the Prometheus UI!

📈 Step 4: Install Grafana

Install Grafana using Helm:

helm install grafana grafana/grafana


Get Grafana service details:

kubectl get svc


Then forward the port:

kubectl port-forward svc/grafana 3000:80


Now open Grafana at:

http://localhost:3000


Default login:

Username: admin

Password: (retrieve via command below)

kubectl get secret grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

🧠 Step 5: Connect Prometheus as a Data Source in Grafana

Log in to Grafana → Go to Settings → Data Sources → Add new data source

Choose Prometheus

URL: http://prometheus-server

Click Save & Test

📊 Step 6: Import a Dashboard

You can import prebuilt dashboards.
Try this one (ID: 3226) for Kubernetes cluster monitoring.

In Grafana → Dashboards → Import → Enter ID 3226 → Load → Select Prometheus → Import.

🖼 Example Visualization

(You can add your Prometheus-Grafana dashboard screenshot here)

![Prometheus Grafana Dashboard](../images/prometheus-grafana-dashboard.png)

✅ Summary

You have successfully:

Installed Prometheus & Grafana using Helm

Exposed Prometheus to access metrics

Forwarded ports to access dashboards

Imported a visualization to monitor Kubernetes metrics

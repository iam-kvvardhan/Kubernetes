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

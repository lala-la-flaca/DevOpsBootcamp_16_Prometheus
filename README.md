# <img width="80" height="80" alt="image" src="![1a4f23660b53de848a6a721e3719b077](https://github.com/user-attachments/assets/ba580607-939c-4bb7-9649-4fa154865482)"/> Module 16 – Monitoring with Prometheus

This exercise is part of Module 16 from the TWN DevOps Bootcamp. In Module 16, we learn how to monitor applications and infrastructure with Prometheus. This module covers everything from installing the Prometheus and Grafana stack on Kubernetes to setting up alerting and visual dashboards. We also learn how to monitor third-party apps such as Redis and collect custom metrics from your own applications. By the end of this module, you know how to build a complete monitoring solution that detects issues early, sends alerts, and visualizes performance data in real time.

---
<a id="demo1"></a>
# 📦Demo 1 –  Install Prometheus Stack in Kubernetes
# 📌 Objective
Set up the Prometheus monitoring stack (Prometheus, Alertmanager, and Grafana) in a Kubernetes cluster using a Helm chart.

# 🚀 Technologies Used
* Prometheus: Metrics collection and monitoring system.
* Grafana: Visualization and dashbaord tool.
* Linux: OS.
* Kubernetes: Container Orchestrtion platform.
* Helm: Package Manager for Kuebrnetes.
* AWS EKS: Managed Kubernetes Cluster.
* Terraform: To deploy K8 infrastructure.

# 🎯 Features
  ✅ Installs Prometheus Operator with Helm.<br>
  📁 Includes Grafana dashboards and Alertmanager.<br>
  ⚙️ Deployed on an EKS cluster created with terraform.<br>
  

# Prerequisites
* AWS account with valid keys.
* EKS demo from terraform module.
* Microoservices Demo from kubernetes module.
  
# 🏗 Project Architecture
<img src=""/>

# ⚙️ Project Configuration
## Setup EKS Cluster
1. Use the Terraform files from EKS module.
   ```
   terraform init
   terraform plan
   terraform apply --auto-approve
   ```
   <img src="" width=800/>
   
2. Generate Kubeconfig file
   ```bash
   ```
    <img src="" width=800/>
   
3. Configure access to the EKS cluster
   ```
   export KUBECONFIG=path/to/kubeconfig
   ```
    <img src="" width=800/>
   
4. Apply the microoservices configuration file from the kubernetes module.
   ```bash
   kubectl apply -f config-microoservices.yaml
   ```
    <img src="" width=800/>
5. Verify that all pods are running as expected.
   ```
   kubectl get pods
   ```
   <img src="" width=800/>
  

## Deploy Prometheus
6. Add the Prometheus Helm repository
   ```bash
   helm pero add prometheus-community https://prometheus-community.github.io/helm-charts
   ```
    <img src="" width=800/>
7. Update the Helm repositories
   ```
   helm repo update
   ```
    <img src="" width=800/>
8. Create a monitoring namespace.
    ```bash
    kubectl create namespace monitoring
    ```
     <img src="" width=800/>
     
9. Install the Prometheus chart in the monitoring namespace.
    ```bash
    helm install monitoring prometheus-community/kube-prometheus-stack -n monitoring
    ```
     <img src="" width=800/>
     
10. Verify that the Prometheus pods are running.
    ```bash
    kubectl get pods -n monitoring
    ```
     <img src="" width=800/>
     
11. Verify that all Promtheus components are working correctly.
    ```bash
    kubectl get all -n monitoring
    ```
     <img src="" width=800/>
   


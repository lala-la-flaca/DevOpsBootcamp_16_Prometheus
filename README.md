# <img width="100" height="100" alt="image" src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/1a4f23660b53de848a6a721e3719b077.jpg"/> Module 16 – Monitoring with Prometheus

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
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/1%20deploy%20EKS%20using%20terraform.PNG" width=800/>
   
2. Generate Kubeconfig file
   ```bash
   ```
    <img src="" width=800/>
   
3. Configure access to the EKS cluster
   ```
   export KUBECONFIG=path/to/kubeconfig
   ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/2%20use%20kubeconfig%20to%20access%20cluster%20using%20kubectl.PNG" width=800/>
   
4. Apply the microoservices configuration file from the kubernetes module.
   ```bash
   kubectl apply -f config-microoservices.yaml
   ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/3%20apply%20conif%20microoservies%20from%20kubernetes%20module%205.PNG" width=800/>
    
5. Verify that all pods are running as expected.
   ```
   kubectl get pods
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/4%20pods%20up.png" width=800/>
  

## Deploy Prometheus
6. Add the Prometheus Helm repository
   ```bash
   helm pero add prometheus-community https://prometheus-community.github.io/helm-charts
   ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/5%20add%20the%20helm%20repository%20prometehus%20community.png" width=800/>
    
7. Update the Helm repositories
   ```
   helm repo update
   ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/6%20checking%20for%20helm%20repo%20updates.png" width=800/>
    
8. Create a monitoring namespace.
    ```bash
    kubectl create namespace monitoring
    ```
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/7%20create%20a%20namespae%20to%20separe%20monitoing%20pods.png" width=800/>
     
9. Install the Prometheus chart in the monitoring namespace.
    ```bash
    helm install monitoring prometheus-community/kube-prometheus-stack -n monitoring
    ```
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/9%20chart%20installed.PNG" width=800/>
     
10. Verify that the Prometheus pods are running.
    ```bash
    kubectl get pods -n monitoring
    ```
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/10%20checking%20prometehus%20pods.PNG" width=800/>
     
11. Verify that all Promtheus components are working correctly.
    ```bash
    kubectl get all -n monitoring
    ```
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_16_Prometheus/blob/main/Img/11%20checking%20all%20prometehus%20components.png" width=800/>
   


# Kubernetes
Kubernetes-complete-architecture

Pod - A Kubernetes pod is a collection of one or more containers, and is the smallest unit of a Kubernetes application

# **k8s architecture**

# Control plane (master node)
  api server - core component of k8s, accepts all incoming  reqs, exposes k8s to external world. 
  
  etcd - key value store, cluster related infos.
  
  scheduler - scheduling pods or resources on k8s, receives info from api server & acts on it
  
  controller manager - ensures controllers like replica set are running
  
  cloud controller manager - like terraform - configuring cloud environments - EKS,AKS,GKE

# Data plane (worker node)
  kubelet - creates pod, ensures pod is always running 
  
  kube proxy - provides networking like Docker0, default load balancing. It uses IP Tables on your linux system for assigning networking.
  
  container runtime - runs container inside pod

- Data plane (Worker Node) → 3 components:
1) Kubelet (Creating and managing  pod)
2) Kube Proxy (uses iptables in Linux machine)
3) Container Runtime (enviornment)
- Control Plane (Master Node) → 
1) API Server (exposes to external world)
2) Scheduler (Scheduling pods or resources in K8s)
Receives information from API server
3) etcd: Backup service (key value store)
4) Controller Manager 
Example: Replica Set
5) CCM (Cloud Controller Manager)
    - No need for on-premice

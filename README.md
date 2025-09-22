# Kubernetes
Kubernetes-complete-architecture

Pod - A Kubernetes pod is a collection of one or more containers, and is the smallest unit of a Kubernetes application

# **k8s architecture**

<img width="1241" height="701" alt="kubernetes-architecture" src="https://github.com/user-attachments/assets/4ec8651b-6c99-4405-8861-ef61d00a14bf" />


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
    - No need for on-premise
  


## ** K8s Deployment - Replica set **

The main work of controller is watching the POD is running in desired state or not. 

-> If not it sends the message to scheduler to create a new resource to achieve the desired state. 

-> One of the controller is called "Deployment".

->  "Deployment" first creates "replica set(actual controller)" managed by "deployment" and replica set creates and manages the POD. 


        +-----------------------------+
        |      Deployment       |
        | (desired state: 3)   |
        +-----------------------------+
                     |
                     | creates or updates
                     |
        +----------------------------+
        |      ReplicaSet        |
        | (desired state: 3)  | 
        +----------------------------+
                     |
                     | creates or updates
                     |
        +----------------------+
        |         Pod          |  (POD -> execution environment for the containers) 
        +----------------------+
                     |
                     | runs the containers
                     |
        +----------------------+
        |       Container  |
        +----------------------+

# Kubernets
# Kubernetes YAML Files Repository

## Author

**Sambhu**

## Repository URL

https://github.com/rahulselokar27-collab/Kubernets.git

---

# Overview

This repository contains Kubernetes manifest files for creating and managing Kubernetes resources such as Pods, Deployments, ReplicaSets, Services, Persistent Volumes, Persistent Volume Claims, ConfigMaps, Secrets, Namespaces, StatefulSets, DaemonSets, and Storage Classes.

These YAML files help understand the core Kubernetes concepts and resource management.

---

# Prerequisites

Before using these files, ensure the following tools are installed:

* Kubernetes Cluster (Minikube, EKS, AKS, GKE, etc.)
* kubectl
* Docker

Verify Cluster Connectivity:

```bash
kubectl cluster-info
kubectl get nodes
```

---

# Repository Structure

```text
Kubernets/
│
├── pod.yaml
├── deployment.yaml
├── replicaset.yaml
├── rc.yaml
├── service.yaml
├── namespace.yaml
├── configmap.yaml
├── secret.yaml
├── pv.yaml
├── pvc.yaml
├── storageclass.yaml
├── deamonset.yaml
├── ststefulset.yaml
├── intra.yaml
└── README.md
```

---

# Step 1: Create Namespace

Create a namespace for resource isolation.

```bash
kubectl apply -f namespace.yaml
```

Verify:

```bash
kubectl get ns
```

---

# Step 2: Create a Pod

Deploy a basic Pod.

```bash
kubectl apply -f pod.yaml
```

Verify:

```bash
kubectl get pods
```

Describe Pod:

```bash
kubectl describe pod <pod-name>
```

---

# Step 3: Intra Pod Communication

Deploy multiple containers inside a single Pod.

```bash
kubectl apply -f intra.yaml
```

Check logs:

```bash
kubectl logs intrapod-demo -c alpine-container
```

Enter container:

```bash
kubectl exec -it intrapod-demo -c alpine-container -- sh
```

Test communication:

```bash
wget -qO- http://localhost:80
```

---

# Step 4: Replication Controller

Create a Replication Controller.

```bash
kubectl apply -f rc.yaml
```

Verify:

```bash
kubectl get rc
```

---

# Step 5: ReplicaSet

Create ReplicaSet for maintaining Pod replicas.

```bash
kubectl apply -f replicaset.yaml
```

Verify:

```bash
kubectl get rs
```

---

# Step 6: Deployment

Deploy application using Deployment.

```bash
kubectl apply -f deployment.yaml
```

Verify:

```bash
kubectl get deployments
```

Scale Deployment:

```bash
kubectl scale deployment nginx-deployment --replicas=5
```

---

# Step 7: Service

Expose Pods using Service.

```bash
kubectl apply -f service.yaml
```

Verify:

```bash
kubectl get svc
```

---

# Step 8: ConfigMap

Create ConfigMap for application configuration.

```bash
kubectl apply -f configmap.yaml
```

Verify:

```bash
kubectl get configmap
```

---

# Step 9: Secret

Create Secret for sensitive information.

```bash
kubectl apply -f secret.yaml
```

Verify:

```bash
kubectl get secret
```

---

# Step 10: Persistent Volume

Create Persistent Volume.

```bash
kubectl apply -f pv.yaml
```

Verify:

```bash
kubectl get pv
```

---

# Step 11: Persistent Volume Claim

Create Persistent Volume Claim.

```bash
kubectl apply -f pvc.yaml
```

Verify:

```bash
kubectl get pvc
```

---

# Step 12: Storage Class

Create StorageClass for dynamic provisioning.

```bash
kubectl apply -f storageclass.yaml
```

Verify:

```bash
kubectl get storageclass
```

---

# Step 13: DaemonSet

Deploy DaemonSet to run one Pod per node.

```bash
kubectl apply -f deamonset.yaml
```

Verify:

```bash
kubectl get daemonset
```

---

# Step 14: StatefulSet

Deploy StatefulSet for stateful applications.

```bash
kubectl apply -f ststefulset.yaml
```

Verify:

```bash
kubectl get statefulset
```

---

# Useful Commands

Check all resources:

```bash
kubectl get all
```

Describe resource:

```bash
kubectl describe <resource-type> <resource-name>
```

View logs:

```bash
kubectl logs <pod-name>
```

Execute inside Pod:

```bash
kubectl exec -it <pod-name> -- sh
```

Delete resource:

```bash
kubectl delete -f <file-name>.yaml
```

Delete all resources:

```bash
kubectl delete -f .
```

---

# Kubernetes Resource Flow

```text
Namespace
    │
    ▼
Pod
    │
    ▼
ReplicaSet / ReplicationController
    │
    ▼
Deployment
    │
    ▼
Service
    │
    ▼
External Access

Storage Flow

StorageClass
      │
      ▼
PersistentVolume (PV)
      │
      ▼
PersistentVolumeClaim (PVC)
      │
      ▼
Pod

Configuration Flow

ConfigMap
     │
     ▼
Pod

Secret
    │
    ▼
Pod
```

---

# Conclusion

This repository demonstrates the fundamental Kubernetes resources and their relationships. It can be used for learning Kubernetes concepts, interview preparation, and hands-on practice in any Kubernetes environment.

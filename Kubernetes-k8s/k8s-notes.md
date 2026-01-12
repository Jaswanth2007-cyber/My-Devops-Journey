# Kubernetes (K8s) Learning Notes 🚀

This repository documents my hands-on learning of **Kubernetes fundamentals**, focusing on architecture, core components, namespaces, commands, and basic YAML configurations.

---

## 📌 What is Kubernetes?

Kubernetes is a **container orchestration platform** used to deploy, manage, scale, and maintain containerized applications efficiently.

Instead of managing containers manually, Kubernetes automates:
- Deployment
- Scaling
- Self-healing
- Networking

---

## 🧠 Kubernetes Architecture Overview

### Main Components:
- **Master Node (Control Plane)**
  - API Server
  - Scheduler
  - Controller Manager
  - etcd (cluster state storage)

- **Worker Nodes**
  - kubelet
  - Container Runtime (Docker / containerd)
  - kube-proxy

---

## 🔁 Kubernetes Workflow (High-Level)
```
Docker Image
↓
Pod
↓
Deployment
↓
Service
↓
User
```


### Explanation:
- **Docker Image** → Blueprint of the application
- **Pod** → Smallest deployable unit in Kubernetes (contains one or more containers)
- **Deployment** → Manages replicas and updates of Pods
- **Service** → Exposes Pods to internal/external users
- **User** → Accesses the application via Service

✅ When a container crashes, Kubernetes recreates it while keeping the rest of the system stable.

---

## 📂 Namespaces in Kubernetes

Namespaces help in:
- Logical separation of resources
- Resource isolation
- Managing multiple environments (dev, test, prod)

### Default Namespace
If no namespace is specified, Kubernetes uses the **default** namespace.

---

## 🔧 Basic kubectl Commands Learned

### Get Pods
```bash
kubectl get pods
```

Get Pods from a Specific Namespace
```
kubectl get pods -n <namespace-name>
```
Delete a Pod
```
kubectl delete pod <pod-name> -n <namespace-name>
```
Run a Pod in a Namespace
```
kubectl run <pod-name> --image=<image-name> -n <namespace-name>
```
Execute into a Pod (Interactive Shell)
```
kubectl exec -it <pod-name> -n <namespace-name> -- bash
```
📝 Writing YAML Files
Pod YAML Example
```
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  namespace: dev
spec:
  containers:
    - name: nginx-container
      image: nginx
      ports:
        - containerPort: 80
```
📝 Pod YAML – Brief Explanation

The Pod YAML defines the smallest unit in Kubernetes.

apiVersion: v1 → Uses core Kubernetes API

kind: Pod → Tells Kubernetes to create a Pod

metadata → Pod name and namespace

spec → What runs inside the Pod

containers → Defines the container image and exposed port

👉 Purpose:
Runs one instance of a container. If the pod crashes, it must be recreated manually.

Deployment YAML Example
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  namespace: dev
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
```
📝 Deployment YAML – Brief Explanation

The Deployment YAML manages multiple Pods automatically.

apiVersion: apps/v1 → Deployment API

kind: Deployment → Creates a Deployment object

replicas → Number of pod copies to run

selector → Connects Deployment to Pods

template → Pod blueprint used by Deployment

👉 Purpose:
Ensures high availability, auto-restarts pods, and supports scaling & updates.

🔑 In One Line Difference

Pod YAML → Runs a single container instance

Deployment YAML → Manages and maintains multiple Pods automatically.

▶️ How to Run (Apply) YAML Files
Apply Pod YAML
```
kubectl apply -f pod.yml
```
If the pod is in a specific namespace (defined in YAML):
```
kubectl apply -f pod.yml -n <namespace-name>
```
Apply Deployment YAML
```
kubectl apply -f deployment.yml
```
Or with namespace:
```
kubectl apply -f deployment.yml -n <namespace-name>
```
👀 How to Verify (Check Status)
Check Pods
```
kubectl get pods
```
With namespace:
```
kubectl get pods -n <namespace-name>
```
Check Deployments
```
kubectl get deployments
```
With namespace:
```
kubectl get deployments -n <namespace-name>
```
❌ How to Delete Resources

Delete Pod using YAML
```
kubectl delete -f pod.yml
```
Delete Deployment using YAML
```
kubectl delete -f deployment.yml
```
🔁 How to Replicate / Scale Pods (Deployment Only)

👉 Pods cannot be replicated directly
👉 Deployments handle replication

Scale Deployment to 3 Replicas
```
kubectl scale deployment <deployment-name> --replicas=3 -n <namespace-name>
```
Verify Replicas
```
kubectl get pods -n <namespace-name>
```
🔄 Update Deployment (Recreate Pods Automatically)

Edit deployment:
```
kubectl edit deployment <deployment-name> -n <namespace-name>
```
Or re-apply updated YAML:
```
kubectl apply -f deployment.yml
```
Kubernetes will:

Create new pods

Delete old pods gradually

Keep the app running (rolling update)

⚠️ Important Note

Pod → One-time, no auto-healing

Deployment → Auto-healing, scaling, rolling updates

That’s why production always uses Deployments, not raw Pods.

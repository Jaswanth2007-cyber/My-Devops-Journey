# Kubernetes Deployment & Service YAML Skeleton

This document provides **clean skeleton templates** for Kubernetes `Deployment` and `Service` manifests, useful for **learning, revision, interviews, and real projects**.

---

## 📦 Deployment YAML — Skeleton

```yaml
apiVersion: apps/v1        # API version for Deployment
kind: Deployment           # Resource type

metadata:
  name: <deployment-name> # Name of the deployment
  namespace: <namespace>  # Namespace (optional but recommended)

spec:
  replicas: <number>      # Number of pod replicas

  selector:
    matchLabels:
      app: <label-name>   # Must match pod labels

  template:
    metadata:
      labels:
        app: <label-name>

    spec:
      containers:
        - name: <container-name>
          image: <image-name:tag>
          imagePullPolicy: <Always | IfNotPresent | Never>
          ports:
            - containerPort: <port>
```
# Deployment Key Fields
```
| Field      | Description              |
| ---------- | ------------------------ |
| apiVersion | Kubernetes API version   |
| kind       | Type of resource         |
| metadata   | Name, namespace, labels  |
| replicas   | Number of pod instances  |
| selector   | Matches pods with labels |
| template   | Pod blueprint            |
| containers | Container configuration  |
```

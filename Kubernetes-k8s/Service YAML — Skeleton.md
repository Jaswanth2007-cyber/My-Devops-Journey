# Kubernetes Service YAML Skeleton

This document provides **clean skeleton templates** for Kubernetes `Service` manifests, useful for **learning, revision, interviews, and real projects**.

---
```
apiVersion: v1             # API version for Service
kind: Service              # Resource type

metadata:
  name: <service-name>     # Name of the service
  namespace: <namespace>   # Namespace

spec:
  type: <ClusterIP | NodePort | LoadBalancer>

  selector:
    app: <label-name>      # Must match pod label

  ports:
    - port: <service-port>
      targetPort: <container-port>
      nodePort: <node-port>   # Only for NodePort
```
# Service Types Fields 
```
| Type         | Purpose                               |
| ------------ | ------------------------------------- |
| ClusterIP    | Internal communication inside cluster |
| NodePort     | External access (testing / dev)       |
| LoadBalancer | External access (cloud production)    |
```

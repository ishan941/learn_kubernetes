# 📦 Day 4 — ConfigMaps & Secrets in Kubernetes

## 🧠 Concepts Covered

- 🔧 ConfigMap: Store environment variables (non-sensitive)
- 🔐 Secret: Store sensitive credentials (e.g., password, API key)
- 🧪 Inject them into Pods as:
  - Environment variables (`envFrom`)
  - Mounted files (not covered today)

---

## 📄 Files in This Folder

| File                 | Description                                 |
| -------------------- | ------------------------------------------- |
| `configmap.yaml`     | Defines a ConfigMap with sample app config  |
| `secret.yaml`        | Defines a Secret with base64-encoded values |
| `pod-configmap.yaml` | Pod that reads from ConfigMap               |
| `pod-secret.yaml`    | Pod that reads from Secret                  |

---

## ▶️ Commands to Run

```bash
kubectl apply -f configmap.yaml
kubectl apply -f secret.yaml
kubectl apply -f pod-configmap.yaml
kubectl apply -f pod-secret.yaml
```

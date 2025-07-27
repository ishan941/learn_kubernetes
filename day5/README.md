# 📦 Day 5 — Persistent Storage in Kubernetes

## 🧠 Concepts

In Kubernetes, data stored inside a container is **ephemeral** (it disappears when the pod is deleted or restarted).

To persist data beyond pod life cycles, we use:

- `PersistentVolume (PV)` – actual physical or virtual storage
- `PersistentVolumeClaim (PVC)` – a request for storage by a user
- `VolumeMount` – allows your container to use that storage path

---

## 📂 Files

| File       | Purpose                                   |
| ---------- | ----------------------------------------- |
| `pv.yaml`  | Defines the Persistent Volume (PV)        |
| `pvc.yaml` | Defines the Persistent Volume Claim (PVC) |
| `pod.yaml` | Pod that writes data to the volume        |

---

## ▶️ Commands

```bash
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f pod.yaml
```

# 📦 Day 6 — StatefulSets in Kubernetes

On Day 6, we explored how Kubernetes **StatefulSets** help manage stateful applications by assigning **stable identities** and **persistent storage** to pods. We used `nginx` as an example.

---

## 🧠 Why StatefulSets?

- Maintains **stable network identity** (`web-0`, `web-1`)
- Maintains **stable storage** for each pod
- Ideal for **stateful apps** like databases, queues, etc.

---

## 📌 Objective

- Deploy a StatefulSet with an Nginx container
- Attach a Persistent Volume to each pod
- Create a file inside a volume
- Delete pod and ensure the data remains after restart

---

## 📁 Folder Structure

````bash
day6/
├── README.md
├── service.yaml
└── statefulset.yaml


## 📂 Files

| File               | Purpose                           |
| ------------------ | --------------------------------- |
| `statefulset.yaml` | Defines StatefulSet with storage  |
| `service.yaml`     | Headless service for DNS identity |

---

## ▶️ Commands

```bash
kubectl apply -f service.yaml
kubectl apply -f statefulset.yaml
kubectl get pods -w
kubectl exec -it web-0 -- sh
````

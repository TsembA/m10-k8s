# 📊 MongoDB ReplicaSet with Mongo Express on Linode Kubernetes Engine (LKE)

This project sets up a **MongoDB ReplicaSet** with persistent volumes and a **Mongo Express UI** inside a Linode Kubernetes Engine (LKE) cluster.
---

## 🧱 Architecture Overview

- **MongoDB** is deployed as a 3-node **ReplicaSet** using the Bitnami Helm chart
- **Linode Block Storage** is used for persistent volume claims
- A Kubernetes **Secret** is used for authentication
- **Mongo Express** provides a web interface to the database and is exposed via **Ingress**

---

## 🗂 Project Files Used

- `mongodb-values.yaml` – Helm config for MongoDB
- `mongo-express.yaml` – Deployment and Service for Mongo Express
- `mongo-express-ingress.yaml` – Ingress resource for public access

---

## 🔗 Visit: [http://172-233-134-200.ip.linodeusercontent.com](http://172-233-134-200.ip.linodeusercontent.com) You can find this adress on Linode website in NodeBalancer tab

---

## 🚀 Deployment Steps

1. **Add Bitnami Helm repo (only once):**

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
```

2. **Install MongoDB using your custom values:**

```bash
helm install mongodb bitnami/mongodb -f mongodb-values.yaml
```

3. **Apply Mongo Express Deployment & Service:**

```bash
kubectl apply -f mongo-express.yaml
```

4. **Apply Ingress configuration:**

```bash
kubectl apply -f mongo-express-ingress.yaml
```

---

## ✅ Result

- MongoDB ReplicaSet with persistent Linode block storage is running
- Mongo Express UI is accessible via the Ingress host
- Everything is modular, Kubernetes-native, and suitable for production-grade LKE setups


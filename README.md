# 🚀 Kubernetes

Kubernetes (K8s) is a powerful container orchestration platform designed to deploy, scale, and manage modern applications. It is ideal for:

* Microservices architecture 🧩
* Monolith applications 🏗️ (yes, even those!)

## ✅ Key Benefits

* 🟢 High Availability (No Downtime)
* 📈 Scalability and Performance
* 💾 Disaster Recovery / Backup and Restore

---

## 🔧 Core Kubernetes Components

* **Node**: Physical or virtual machine (e.g., AWS EC2) that can be a **worker** or **master**.
* **Pod**: Smallest deployable unit that abstracts a container. Each gets a unique internal IP.
* **Service**: Provides a stable endpoint (IP) and load balances across Pods.
* **Ingress**: Handles external access to Services via routing rules.
* **ConfigMap**: Stores external configuration data.
* **Secret**: Securely stores sensitive data (Base64 encoded).
* **Volumes**: Used to persist data.
* **Deployment**: Blueprint for managing Pods and their replicas.
* **StatefulSet**: Like Deployment, but for stateful apps like databases.
* **ReplicaSet**: Ensures a specified number of pod replicas are running.
* **DaemonSet**: Runs a Pod on every (or specific) Node.
* **CRD (Custom Resource Definition)**: Extend K8s API with your own resource types.

---

## 🔧 Common K8s Commands

* `minikube start / stop`: Launch or shut down a local K8s cluster for testing.
* `kubectl`: Command line tool to manage K8s.

  * `kubectl get nodes`
  * `kubectl get pods`
  * `kubectl get pods -o wide`
  * `kubectl get deployments`
  * `kubectl get services`
  * `kubectl create deployment NAME --image=image`
  * `kubectl edit deployment NAME`
  * `kubectl logs NAME`
  * `kubectl describe pod NAME`
  * `kubectl exec -it NAME -- /bin/bash`
  * `kubectl delete deployment NAME`
  * `kubectl apply -f filename.yaml`

---

## 🗂️ Namespaces

Built-in namespaces:

* `kube-system`: System components
* `kube-public`: Cluster info (readable by all)
* `kube-node-lease`: Node heartbeat tracking
* `default`: Where resources go if no namespace specified

👨‍💻 **Best Practices:**

* Use namespaces for **team isolation** and **environment separation** (dev/prod)
* Set **resource limits** (CPU, RAM, storage)

---

## 🌐 Services in Detail

A Service abstracts access to a group of Pods and maintains a stable IP:

* **ClusterIP** (default): Internal-only access
* **Headless**: No stable IP; talks directly to Pods (for apps needing Pod-specific behavior)
* **NodePort**: Exposes service on static port (range 30000-32767) on each node
* **LoadBalancer**: Cloud-native option for exposing services externally
* **Ingress**: Handles routing using host/path rules. Can also handle TLS (via secrets)

---

## 💾 Volumes & Persistent Storage

* Used for data persistence across Pod restarts.
* Not namespaced: accessible anywhere in the cluster.
* Types:

  * `PersistentVolume` (PV): Admin provisioned
  * `PersistentVolumeClaim` (PVC): App requests storage
  * `StorageClass`: Dynamically provision PVs
  * ConfigMap / Secret as volume types

👨‍🏫 **Note:** Master Pod usually writes; replicas are read-only. Data can sync automatically.

---

## ☁️ Managed Kubernetes Services

Providers automate K8s cluster setup (e.g., AWS EKS, GKE, AKS). You define:

* Node count and size
* Auto-scaling groups

You can also use Terraform to provision infrastructure 🌱

---

## 📦 Helm

Helm is the **package manager** for Kubernetes 🧰

* **Helm Charts**: Package of YAML templates
* **Helm Hub**: Browse/search public/private charts

🛠️ Commands:

* `helm search repo`
* `helm repo add`
* `helm install <name> --values values.yaml <chart>`
* `helm uninstall <chart>`

### 📜 Helmfile

Define the whole cluster config in a single YAML file.

* `brew install helmfile`
* `helmfile sync`
* `helmfile list`
* `helmfile destroy`

---

## ⚙️ Operators

Custom control loops for managing stateful applications 🔁

* Handle full app lifecycle automatically

---

## 🔐 RBAC (Role-Based Access Control)

Controls WHO can do WHAT:

* **Role**: Defines what resources and actions are allowed
* **RoleBinding**: Assigns Role to a user or group
* **ClusterRole / ClusterRoleBinding**: For cluster-wide access

Authentication handled externally (token, cert, LDAP, etc.)

---

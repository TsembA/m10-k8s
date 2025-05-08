# 🐝 Mosquitto MQTT Broker Deployment on Kubernetes

This project deploys the [Eclipse Mosquitto](https://mosquitto.org/) MQTT broker (`v2.0`) to a Kubernetes cluster using a `Deployment` resource with mounted configuration and secret volumes.

---

## 📦 Features

- 🔁 Single-instance MQTT broker (`replicas: 1`)
- 🔐 Secure secret mounting for sensitive files (e.g., credentials, TLS)
- ⚙️ Configurable via mounted `ConfigMap` (e.g., `mosquitto.conf`)
- 📡 Listens on default MQTT port `1883`
- 🔄 Ideal for IoT or lightweight messaging in Kubernetes

---

## 📁 Project Structure

```text
.
├── mosquitto-deployment.yaml   # Deployment definition with volumeMounts
├── mosquitto-config-file.yaml  # ConfigMap with broker config
├── secret-file.yaml            # Secret with credentials or certs
└── README.md                   # This file
```

---

## 🔧 Prerequisites

- Kubernetes cluster (e.g., Minikube, Kind, or cloud provider)
- `kubectl` CLI installed and configured
- Valid `mosquitto.conf` and secret file (base64-encoded)

---

## 🚀 Deployment Steps

```bash
kubectl apply -f secret-file.yaml
kubectl apply -f mosquitto-config-file.yaml
kubectl apply -f mosquitto-deployment.yaml
```

To verify:

```bash
kubectl get pods
kubectl logs <mosquitto-pod-name>
```

---

## 🧪 Testing

Use an MQTT client (like `mosquitto_pub` or `MQTT Explorer`) to publish and subscribe:

```bash
mosquitto_pub -h <mosquitto-pod-ip> -t test/topic -m "hello"
mosquitto_sub -h <mosquitto-pod-ip> -t test/topic
```


---

## 🧹 Cleanup

```bash
kubectl delete -f mosquitto-deployment.yaml
kubectl delete -f mosquitto-config-file.yaml
kubectl delete -f secret-file.yaml
```

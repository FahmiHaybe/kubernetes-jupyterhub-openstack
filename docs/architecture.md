# Architecture and Cluster Design

## Configuration Management

Ansible is the primary configuration management tool in this project,
chosen for its simplicity, agentless architecture, and strong
integration with Kubernetes tooling.

Terraform provisions the OpenStack infrastructure, while Kubespray
installs and configures the Kubernetes cluster.

## Namespaces

The cluster uses logical namespace separation:

- default
- ingress-nginx
- jhub
- kube-system
- kube-public
- kube-node-lease
- local-path-storage
- monitoring
- minio
- velero

Namespaces help scope access, resources, and responsibilities.

## Kubernetes Workloads

### Deployments
Key deployments include:

- JupyterHub: hub, proxy, and user-scheduler
- CoreDNS, Calico controllers, Kubernetes Dashboard
- Prometheus and Grafana (via Helm)
- Velero controller

### DaemonSets
DaemonSets ensure node-level services run on each node:

- ingress-nginx controller
- calico-node
- kube-proxy
- node-local-dns
- Prometheus node exporter (via Helm)
- Loki promtail (via Helm)

### StatefulSets
StatefulSets provide stable identities and persistent storage:

- Prometheus
- Alertmanager
- Loki

> Note: JupyterHub user pods are dynamically spawned Deployments, not StatefulSets.

## Persistent Storage

PersistentVolumes and PersistentVolumeClaims are dynamically provisioned
using the Rancher Local Path Provisioner.

Each JupyterHub user receives:

- A dedicated 10Gi PVC
- Mounted at `/home/jovyan/`

This ensures data isolation and persistence across pod restarts.
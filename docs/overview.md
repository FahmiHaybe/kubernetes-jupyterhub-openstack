# Project Overview

This project automates the deployment of a reproducible Kubernetes
environment on OpenStack, designed for a multi-user data science
development platform. It focuses on enabling collaborative, self-service
workflows for data scientists.

The deployed platform provides:

- **Multi-user JupyterHub** for interactive data science notebooks
- **Centralized monitoring** with Prometheus and Grafana
- **Centralized logging** with Loki and Promtail
- **Backup and restore** using Velero with MinIO object storage
- **Infrastructure-as-Code** using Terraform, Ansible, Kubespray, and Helm

The deployment is fully automated, ensuring the cluster and all
components can be reproduced reliably with minimal manual intervention,
while providing per-user isolation and secure access controls.

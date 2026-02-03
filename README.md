# Kubernetes-based Data Science Platform on OpenStack

This project demonstrates a fully automated, repeatable kubernetes environment deployed on Openstack, designed for a multi-user data science team.

It provides:
- JupyterHub for multi-user notebook access
- Prometheus & Grafana for monitoring
- Loki & Promtail for centralized logging
- Velero & MinIO for backups
- Infrastructure-as-Code usign Terraform, Ansible, Kubespray and Helm

## Architecture Overview
- Openstack VMs provisioned via Terraform
- Kubernetes cluster deployed using Kubespray
- Applications installed via Helm charts
- Persistent storage via Rancher Local Path Provisioner


## Technologies Used
- Terraform
- Ansible
- Kubespray
- Kubernetes
- Helm
- JupyterHub
- Prometheus / Grafana
- Loki / Promtail
- Velero / MinIO


## Deployment Workflow
1. Provision infrastructure with Terraform
2. Deploy Kubernetes using Kubespray
3. Configure SSH access nodes
4. Install cluster services via Helm
5. Configure backup with Velero & MinIO


## Known Limitations
- Limited retry logic in Ansible playbooks
- Backup automation partially manual
- MinIO stores backups locally (no external replication)


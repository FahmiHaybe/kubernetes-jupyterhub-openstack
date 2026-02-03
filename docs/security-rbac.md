# Security, RBAC and Service Accounts

RBAC is used to enforce least-privilege access within Kubernetes. The playbooks explicitly manage RBAC for **JupyterHub**:
- Custom Role for spawning and managing user pods
- RoleBinding scoped to the `jhub` namespace

For other components (e.g., Prometheus, Grafana, Loki), RBAC is provided by the **Helm charts’ default ServiceAccounts**. The playbooks do not manually configure roles or bindings for monitoring, so RBAC beyond JupyterHub relies on chart defaults.

## Service Accounts
**A dedicated ServiceAccount is created explicitly for JupyterHub**, ensuring that pods authenticate securely to the Kubernetes API with only the permissions they require.

Other components, including monitoring and backup tools (Prometheus, Grafana, Loki, Velero), use ServiceAccounts provisioned automatically by their Helm charts. These defaults provide basic access controls, but the playbooks do not manage them directly.
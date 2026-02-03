# Deployment Workflow

The deployment workflow was designed to be repeatable, mostly automated, and accessible to users with limited experience.

## High-Level Steps

1. **Provision OpenStack infrastructure** using Terraform  
2. **Deploy Kubernetes** using Kubespray  
3. **Configure SSH keys** across all nodes  
4. **Install cluster services** using Helm  
5. **Deploy monitoring, logging, and backup services**  

Each step is documented clearly to ensure consistent results and reduce the risk of errors.

## Workflow Tooling

- The workflow was tracked and organized using a **Trello board**, providing step-by-step guidance.  
- Other students in the project acted as **junior sysadmins**, responsible for executing the workflow. This setup ensured that even participants with minimal prior experience could reliably deploy the cluster.  
- Initial testing was performed on a single developer laptop due to **hardcoded local paths**, but the workflow itself is repeatable and portable once paths are updated.

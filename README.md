# Kubernetes HA Reboot Playbook

This Ansible playbook is designed to safely reboot nodes in a Kubernetes cluster. Rebooting in this fashion will not have an outage as long as you have multiple primary nodes (3 or more). It performs the following tasks:

1. Pauses alerts in monitoring solution
2. Drains the node to ensure that all pods are safely evicted.
3. Reboots the node.
4. Waits for SSH to come back up on the node.
5. Uncordons the node to allow new pods to be scheduled.
6. Resumes alerts

## Usage

To run this playbook, use the following command:

```bash
ansible-playbook k8reboot.yml
```


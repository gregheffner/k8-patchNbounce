# Kubernetes Reboot Playbook

This Ansible playbook is designed to safely reboot nodes in a Kubernetes cluster. It performs the following tasks:

1. Drains the node to ensure that all pods are safely evicted.
2. Reboots the node.
3. Waits for SSH to come back up on the node.
4. Uncordons the node to allow new pods to be scheduled.

Additionally, it waits for the Kubernetes master node to restart and then runs the `cloudflared` tunnel.

## Usage

To run this playbook, use the following command:

```bash
ansible-playbook k8reboot.yml
```

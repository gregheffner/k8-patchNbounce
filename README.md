# Kubernetes HA Reboot Playbook

![Ansible](https://img.shields.io/badge/Ansible-2.9.10-blue)
![Kubernetes](https://img.shields.io/badge/Kubernetes-1.18-blue)

This Ansible playbook is designed to safely reboot nodes in a Kubernetes cluster. Rebooting in this fashion will not cause an outage. It performs the following tasks:

1. Drains the node to ensure that all pods are safely evicted.
2. Reboots the node.
3. Waits for SSH to come back up on the node.
4. Uncordons the node to allow new pods to be scheduled.

Additionally, it waits for the Kubernetes master node to restart and then runs the `cloudflared` tunnel.

## Blog:
Check out the blog about this at [Nerdsense Blog](https://greg.heffner.live/image/pages/2024/Aug/ansible.html)

## Prerequisites

- Ansible 2.9.10 or higher
- Kubernetes 1.18 or higher
- SSH access to all nodes in the cluster
- Properly configured Ansible inventory file

## Usage

To run this playbook, use the following command:

```bash
ansible-playbook k8reboot.yml
```
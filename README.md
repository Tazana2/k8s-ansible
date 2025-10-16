# Kubernetes Cluster Deployment

Automated Kubernetes cluster deployment using Ansible on AWS EC2 instances.

## Quick Start

### 1. Install Prerequisites
```bash
ansible-playbook -i inventory.ini prerequisites.yml
```

### 2. Start the cluster
```bash
ansible-playbook -i inventory.ini start-cluster.yml
```

### 3. Deploy Sample Application
```bash
ansible-playbook -i inventory.ini deploy-k8s.yml
```
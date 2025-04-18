Here's the updated `README.md` based on your Vagrantfile configuration:

```markdown
# Telcocloud.pro Kubernetes Lab Environment

![Kubernetes Logo](https://upload.wikimedia.org/wikipedia/commons/6/67/Kubernetes_logo.svg)
![Ubuntu Logo](https://upload.wikimedia.org/wikipedia/commons/a/ab/Logo-ubuntu_cof-orange-hex.svg)

## Overview
A production-like Kubernetes cluster environment built with Vagrant, featuring a 3-node setup with Ubuntu 22.04 (Jammy Jellyfish) and Kubernetes v1.32.3.

## Key Features

- **Cluster Architecture**:
  - 1 Control Plane (tcp-master)
  - 2 Worker Nodes (tcp-node1, tcp-node2)
  - Private network: 192.168.56.0/24

- **Technical Specifications**:
  - Each VM: 2 vCPUs, 2GB RAM
  - Container Runtime: containerd (optimized for Kubernetes)
  - CNI Plugin: Calico v3.27.0
  - Pod Network CIDR: 192.168.0.0/16

- **Pre-installed Components**:
  - Kubernetes v1.32.3 (kubeadm, kubelet, kubectl)
  - Helm-ready environment
  - Systemd-cgroup enabled containerd
  - Essential tools: curl, jq, gnupg, lsb-release

## Requirements

### Host System
| Component       | Minimum          | Recommended      |
|-----------------|------------------|------------------|
| CPU Cores       | 4 (with VT-x/AMD-v) | 6+            |
| RAM             | 8GB              | 16GB             |
| Disk Space      | 20GB             | 40GB             |
| OS              | Windows 10+, macOS 10.15+, Linux |

### Software Dependencies
| Software        | Version          | Purpose          |
|-----------------|------------------|------------------|
| Vagrant         | ≥ 2.3            | VM orchestration |
| VirtualBox      | ≥ 6.1            | Hypervisor       |
| kubectl         | ≥ 1.28           | Cluster CLI      |

## Quick Start Guide

1. **Clone and initialize**:
   ```bash
   git clone git@github.com:dipakvwarade/Telcocloud.pro_Cka_lab.git
   cd Telcocloud.pro_Cka_lab-main
   ```

2. **Start the cluster** (takes 10-15 minutes):
   ```bash
   vagrant up
   ```

3. **Access the cluster**:
   ```bash
   vagrant ssh tcp-master
   kubectl get nodes  # Verify all nodes show 'Ready'
   ```

## Network Configuration

| Node          | IP Address      | Hostname    |
|---------------|-----------------|-------------|
| Control Plane | 192.168.56.10   | tcp-master  |
| Worker 1      | 192.168.56.11   | tcp-node1   |
| Worker 2      | 192.168.56.12   | tcp-node2   |

## Included Optimizations

- **Kernel Tuning**:
  - Enabled IP forwarding
  - Bridge netfilter
  - Disabled swap

- **Container Runtime**:
  - Systemd cgroups enabled
  - Optimized containerd configuration

- **Security**:
  - UFW firewall disabled
  - SSH key-based authentication

## Common Operations

### Cluster Management
```bash
# Restart the cluster
vagrant halt && vagrant up

# Rebuild from scratch
vagrant destroy -f && vagrant up

# SSH to nodes
vagrant ssh tcp-master
vagrant ssh tcp-node1
```

### Kubernetes Tools
```bash
# Check cluster status
kubectl get nodes -o wide

# View system pods
kubectl get pods -n kube-system

# Access cluster info
kubectl cluster-info
```

## Customization Options

Edit `Vagrantfile` to modify:
```ruby
# Hardware allocation
memory: 2048  # MB
cpus: 2       # vCPUs

# Network settings
ip: "192.168.56.10"  # Master node IP
```

## Troubleshooting

- I have to say vagrant + virtualbox is buggy setup but its the most easiest way to build the lab using what you have - Windows !
- When anything fails, just try to redo it and before that please clean - C:\Users\PC\VirtualBox VMs 

## Support

For assistance, contact:
https://www.linkedin.com/in/dipakwarade

For updates, subscribe: 
https://www.linkedin.com/newsletters/7162546832793927680

## Whats comming ?
- Grading
- CKA schenarios
- 4g and 5g deployment labs 
```
Would you like me to add any additional sections about:
- Specific lab exercises?
- Backup/restore procedures?
- Security best practices for the environment?
- Monitoring setup instructions?

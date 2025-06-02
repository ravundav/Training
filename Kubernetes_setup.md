# Kubernetes Setup

## Master Node

```bash
# Disable swap
swapoff -a

# Update package lists
apt-get update

# Remove old containerd config
rm /etc/containerd/config.toml

# Restart services
systemctl restart docker kubelet containerd

# Reset kubeadm
kubeadm reset -f

# Reload sysctl settings
sysctl --system

# Generate new containerd config
sh -c "containerd config default > /etc/containerd/config.toml"

# Enable SystemdCgroup in containerd config
sed -i 's/ SystemdCgroup = false/ SystemdCgroup = true/' /etc/containerd/config.toml

# Restart containerd and kubelet
systemctl restart containerd.service kubelet.service

# Enable kubelet to start on boot
systemctl enable kubelet.service

# Pull Kubernetes images
kubeadm config images pull

# Initialize the cluster
kubeadm init

# Set kubeconfig for kubectl
export KUBECONFIG=/etc/kubernetes/admin.conf

# Check system pods
kubectl get po -n kube-system

# Verify all cluster component health status
kubectl get --raw='/readyz?verbose'

# Verify cluster info
kubectl cluster-info

# Install Calico network plugin
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml

# Check system pods again
kubectl get po -n kube-system
```

---

## Worker Node

```bash
# Disable swap
swapoff -a

# Update package lists
apt-get update

# Remove old containerd config
rm /etc/containerd/config.toml

# Restart services
systemctl restart docker kubelet containerd

# Reset kubeadm
kubeadm reset -f

# Join the cluster (replace <key> with your actual join command)
kubeadm join <key>
```

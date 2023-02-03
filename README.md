# kind-cluster
creating cluster with kind
#!/bin/bash

# Update the package index
sudo apt-get update

# Install Docker
sudo apt-get install -y docker.io

# Add the Kubernetes repository
sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

# Update the package index
sudo apt-get update

# Install Kubernetes components
sudo apt-get install -y kubelet kubeadm kubectl

# Enable Docker and Kubernetes services
sudo systemctl enable docker
sudo systemctl enable kubelet

# Initialize the Kubernetes cluster
sudo kubeadm init

# Kubernetes Installation Steps

These steps will guide you through the process of installing Kubernetes on both the master and slave nodes.

## Step 1: Prepare the Environment (Master and Slave)

1. Update the package list and install Docker:
   ```bash
   sudo apt-get update -y
   sudo apt-get install docker.io -y
   sudo service docker restart
   ```

2. Add the Kubernetes apt repository and update the package list:
   ```bash
   curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo "deb http://apt.kubernetes.io/kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
   sudo apt-get update
   ```

3. Install Kubernetes components:
   ```bash
   sudo apt-get install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
   ```

## Step 2: Initialize Kubernetes on Master Node

1. On the Master node, run the following command to initialize Kubernetes with the desired Pod Network CIDR (replace `192.168.0.0/16` with your preferred CIDR range):
   ```bash
   sudo kubeadm init --pod-network-cidr=192.168.0.0/16
   ```

## Step 3: Configure Kubeconfig (On Master Node)

1. Create a directory and copy the Kubernetes admin config to your user's `.kube` directory:
   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

## Step 4: Deploy Network and Ingress Controllers (On Master Node)

1. Deploy the Calico network plugin for pod networking:
   ```bash
   kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.1/manifests/calico.yaml
   ```

2. Deploy the Ingress-Nginx controller for managing ingress resources:
   ```bash
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.49.0/deploy/static/provider/baremetal/deploy.yaml
   ```

---

Please make sure to adjust any specific configurations or settings according to your requirements. These steps outline the process for setting up Kubernetes on both the master and slave nodes, including initializing the cluster, configuring the kubeconfig, and deploying essential network and ingress controllers.

---
title: Install Kubernetes on Ubuntu Jammy 22.04 using Flannel
date: 2023-05-20 12:00:00 +0800
categories: [Devops]
tags: [git, cloud, devops, kubernetes, ubuntu, flannel, linux]     # TAG names should always be lowercase
---
# Install Kubernetes on Ubuntu Jammy 22.04 using Flannel

## Challenge during installation

Error during kubeadmin init

```
E0714 01:32:54.309894    2800 request.go:1092] Unexpected error when reading response body: net/http: request canceled (Client.Timeout or context cancellation while reading body)
error execution phase addon/coredns: unable to create a new DNS service: unexpected error when reading response body. Please retry. Original error: net/http: request canceled (Client.Timeout or context cancellation while reading body)
To see the stack trace of this error execute with --v=5 or higher
```


## Steps taken to configure Kubernetes 1.27 on Ubuntu 22.04 using Flannel without any error.

Update Ubuntu packages to the latest version

```bash
sudo apt-get update
```

Install apt-transport-https and curl packages

```bash
sudo apt install apt-transport-https curl -y
```

Install containerd (reference: https://docs.docker.com/engine/install/ubuntu/)

```bash
sudo mkdir -p /etc/apt/keyrings
```

```shell
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```shell
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```shell
sudo apt update
```

```shell
sudo apt install containerd.io -y
```

Create containerd configuration

```shell
sudo mkdir -p /etc/containerd
```

```shell
sudo containerd config default | sudo tee /etc/containerd/config.toml
```

Edit /etc/containerd/config.toml. Set SystemdCgroup = true

```
sudo sed -i "s/SystemdCgroup = false/SystemdCgroup = true/g" /etc/containerd/config.toml
```

Verify SystemCgroup change to true

```shell
grep -i SystemdCgroup /etc/containerd/config.toml
```

Output


```shell
            SystemdCgroup = true
```
Restart containerd

```
sudo systemctl restart containerd
```

Install Kubernetes

```shell
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
```

```shell
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"
```

```shell
sudo apt install kubeadm kubelet kubectl kubernetes-cni -y
```

Disable swap

```shell
sudo swapoff -a
```

Check and disable any swap entry if exists
<!-- sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab -->
```shell
sudo vim /etc/fstab
```

Example

```shell
# /swap.img      none    swap    sw      0       0
```

Avoid error "/proc/sys/net/bridge/bridge-nf-call-iptables does not exist" on kubeinit 

```shell
sudo modprobe br_netfilter
```

```shell
sudo sysctl -w net.ipv4.ip_forward=1
```

Initialize Kubernetes on Master Node

```shell
sudo kubeadm init --pod-network-cidr=10.244.0.0/16
```

Output

```shell
Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.0.124:6443 --token 1wr5h3.g83f7lmcaw63nx3y \
	--discovery-token-ca-cert-hash sha256:bb713ae7c7070443de1893a03430c1222da7ff51339ecf033a7188045ac0471f
```

Copy to config as kubadm command

```shell
mkdir -p $HOME/.kube
```

```shell
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
```

```shell
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

Deploy Flannel pod network to the cluster (reference https://github.com/flannel-io/flannel)

```shell
kubectl apply -f https://raw.githubusercontent.com/flannel-io/flannel/v0.20.2/Documentation/kube-flannel.yml
```



All should be running now by checking all the namespaces

```shell
kubectl get all -A
```

Output

```shell
NAMESPACE      NAME                                   READY   STATUS    RESTARTS   AGE
kube-flannel   pod/kube-flannel-ds-9w8nb              1/1     Running   0          65s
kube-system    pod/coredns-5d78c9869d-5kkpt           1/1     Running   0          6m23s
kube-system    pod/coredns-5d78c9869d-h4lk2           1/1     Running   0          6m23s
kube-system    pod/etcd-ubuntu04                      1/1     Running   0          6m35s
kube-system    pod/kube-apiserver-ubuntu04            1/1     Running   0          6m35s
kube-system    pod/kube-controller-manager-ubuntu04   1/1     Running   0          6m35s
kube-system    pod/kube-proxy-42sqn                   1/1     Running   0          6m24s
kube-system    pod/kube-scheduler-ubuntu04            1/1     Running   0          6m35s

NAMESPACE     NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)                  AGE
default       service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP                  6m38s
kube-system   service/kube-dns     ClusterIP   10.96.0.10   <none>        53/UDP,53/TCP,9153/TCP   6m36s

NAMESPACE      NAME                             DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
kube-flannel   daemonset.apps/kube-flannel-ds   1         1         1       1            1           <none>                   65s
kube-system    daemonset.apps/kube-proxy        1         1         1       1            1           kubernetes.io/os=linux   6m35s

NAMESPACE     NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
kube-system   deployment.apps/coredns   2/2     2            2           6m36s

NAMESPACE     NAME                                 DESIRED   CURRENT   READY   AGE
kube-system   replicaset.apps/coredns-5d78c9869d   2         2         2       6m24s
```

Then you can join any number of worker nodes by running the following on each as root:

Example

```shell
kubeadm join 192.168.0.124:6443 --token 1wr5h3.g83f7lmcaw63nx3y \
	--discovery-token-ca-cert-hash sha256:bb713ae7c7070443de1893a03430c1222da7ff51339ecf033a7188045ac0471f
```
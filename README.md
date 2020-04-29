# Recipe to Install Kubernetes cluster on your windows local machine


## Prerequisites
Before you begin, you should check if virtualization is supported on your windows. See [this link](https://www.shaileshjha.com/how-to-find-out-if-intel-vt-x-or-amd-v-virtualization-technology-is-supported-in-windows-10-windows-8-windows-vista-or-windows-7-machine/) to do that.

### 1. Oracle VirtualBox
Use [this link](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0) to download Oracle VirtualBox if it is not already installed on your machine.

> Note: To ensure compatibility with the rest of the prerequisites, make sure that the version is 6.0.x or older.

### 2. Vagrant
Use [this link](https://www.vagrantup.com/downloads.html) to download Vagrant if it is not already installed.
> Note: You should  restart the computer after downloading Vagrant.


## Creating  Kubernetes cluster
Performe the following steps with powershell :
1. Download or clone this repository `git clone https://github.com/ahmadehab/Kubernetes-minikube-local.git`
2. Navigate to Kubernetes-minikube-local directory `cd Kubernetes-minikube-local`
3. Run this command `vagrant up` to start the VM
4. Run this command `vagrant ssh` to connect to the VM

## Starting The Minikube Service
1. Start the *minikube* service by running `sudo minikube start --vm-driver=none`

## Change The Permission For Kube Configs
To change the permission for kube configs run,
```
sudo chown -R $USER $HOME/.kube
sudo chgrp -R $USER $HOME/.kube
#change permission for minikube configs
sudo chown -R $USER $HOME/.minikube
sudo chgrp -R $USER $HOME/.minikube
```

After you have done all the above steps, you should now be able to work with kubernetes cluster from your vm terminal. To confirm this, the output from `kubectl get nodes` should be similar to:

```console
NAME       STATUS   ROLES    AGE   VERSION
minikube   Ready    master   10m   v1.18.0
```
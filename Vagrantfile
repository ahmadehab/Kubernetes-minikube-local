# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.define "minikube" do |kube|
    kube.vm.hostname = "minikube"
    kube.vm.network "private_network", ip: "192.168.12.25"
    config.vm.provider :virtualbox do |vb|
       vb.customize ["modifyvm", :id, "--memory", "4096"]
       vb.customize ["modifyvm", :id, "--cpus", "2"]
    end
    kube.vm.provision "shell", inline: $script
  end

$script = <<SCRIPT
echo Updating your VM...
sudo apt-get update
echo Installing Minikube...
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
echo Installing Kubectl...
curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
echo Installing Docker...
wget -qO- get.docker.com | bash

sudo apt-get install nfs-common -y

SCRIPT

end

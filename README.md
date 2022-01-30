# How to Install Kubernetes(k8s) with Minikube on CentOS 8/ Redhat8

# Prerequisites of MiniKube

# What you’ll need
  # . 2 CPUs or more
  # . 2GB of free memory

  # . 20GB of free disk space

  # . Internet connection
  # Container or virtual machine manager, such as: 
    
    Docker, Hyperkit, Hyper-V, KVM, Parallels, Podman, VirtualBox, or VMware Fusion/Workstation
# step by step installation proccess
# step1: 
    setenforce 
# step2: 
    sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
# step3:
    dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
# step4:
    dnf install docker-ce --nobest -y

# step5:
    systemctl start docker

# step6:
    systemctl enable docker

# step7:
    firewall-cmd --zone=public --add-masquerade --permanent
    firewall-cmd --reload
# step8: 
    dnf install conntrack -y
# step9:
    curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

 # step10:
    chmod +x ./kubectl
# step11:
    mv ./kubectl /usr/local/bin/kubectl
# step12:
    kubectl version --client
# step13:
    curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
# step14:
    chmod +x minikube
# step15:
    mkdir -p /usr/local/bin/
# step16:
    install minikube /usr/local/bin/
# step17:
    minikube start --driver=none
# step18:
    minikube status
# step19:
    minikube ip
# step 20:
    kubectl cluster-info
# step21:
    kubectl get nodes
# step22:
    kubectl create deployment test-minikube --image=k8s.gcr.io/echoserver:1.10
# step23:
    kubectl expose deployment test-minikube --type=NodePort --port=8080
# step24:
    kubectl get pod
# step25:
    minikube service test-minikube --url
# step26:
    minikube addons list
# step27:
    minikube dashboard --url

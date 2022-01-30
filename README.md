# How to Install Kubernetes(k8s) with Minikube on CentOS 8/ Redhat8

# Prerequisites of MiniKube

# What you’ll need
  # . 2 CPUs or more
  # . 2GB of free memory

  # . 20GB of free disk space

  # . Internet connection
  # Container or virtual machine manager, such as: 
    
    Docker, Hyperkit, Hyper-V, KVM, Parallels, Podman, VirtualBox, or VMware Fusion/Workstation
    
   ![image](https://user-images.githubusercontent.com/64592542/151698831-71022b7d-46b2-4e47-a83b-88a997444ce2.png)

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
    systemctl status docker
   ![image](https://user-images.githubusercontent.com/64592542/151698887-eb2355c1-a08b-47bf-b6d2-8844383f7e42.png)

    


# step7:
    firewall-cmd --zone=public --add-masquerade --permanent
    firewall-cmd --reload
# step8: 
    dnf install conntrack -y
   ![image](https://user-images.githubusercontent.com/64592542/151698929-669bf50b-6720-48f0-a9ac-ba71bdf2bf81.png)

    
# step9:
    curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
   ![Screenshot (878)](https://user-images.githubusercontent.com/64592542/151698993-d6597b17-f91b-479a-aa1e-2e338b048018.png)


 # step10:
    chmod +x ./kubectl
    
# step11:
    mv ./kubectl /usr/local/bin/kubectl
# step12:
    kubectl version --client
   ![Screenshot (880)](https://user-images.githubusercontent.com/64592542/151699037-2133b5ef-5eec-4dba-bbfa-0d1e8dd2eca3.png)

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
   ![Screenshot (882)](https://user-images.githubusercontent.com/64592542/151699061-e43becb9-5aef-4d0d-8498-450a040502c9.png)

# step18:
    minikube status
   ![image](https://user-images.githubusercontent.com/64592542/151699094-279598f6-92b8-4b5e-8bd9-fdeb47d7f2f1.png)

    
# step19:
    minikube ip
   ![Screenshot (885)](https://user-images.githubusercontent.com/64592542/151699113-a3c1004e-2d52-40b3-a7d0-09cf119135a9.png)

# step 20:
    kubectl cluster-info
   ![Screenshot (887)](https://user-images.githubusercontent.com/64592542/151699147-eafb35c0-85cf-4ef5-a68e-aa10a3263112.png)

# step21:
    kubectl get nodes
   ![Screenshot (889)](https://user-images.githubusercontent.com/64592542/151699182-ff409480-019a-4542-985a-487daba54bd5.png)

# step22:
    kubectl create deployment test-minikube --image=k8s.gcr.io/echoserver:1.10
    
# step23:
    kubectl expose deployment test-minikube --type=NodePort --port=8080
# step24:
    kubectl get pod
   ![Screenshot (901)](https://user-images.githubusercontent.com/64592542/151699677-d58401d7-29cd-4770-b224-8965dbf99a29.png)

# step25:
    minikube service test-minikube --url
   ![Screenshot (893)](https://user-images.githubusercontent.com/64592542/151699286-a42961c5-72f8-4332-bd5e-6a52ac936545.png)
   ![Screenshot (895)](https://user-images.githubusercontent.com/64592542/151699339-1d9ad22f-043e-4f9d-b064-0e75a1e6feae.png)


# step26:
    minikube addons list
   ![image](https://user-images.githubusercontent.com/64592542/151699382-1ae5697c-baed-4740-bc0b-e2ca8a9ee7c1.png)

    
# step27:
    minikube dashboard --url
   ![image](https://user-images.githubusercontent.com/64592542/151699358-a42f6c61-105f-42b6-8031-8701347b1ffb.png)

    
    

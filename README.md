# Learn Terraform - Provision AKS Cluster

This repo is a companion repo to the [Provision an AKS Cluster learn guide](https://learn.hashicorp.com/terraform/kubernetes/provision-aks-cluster), containing Terraform configuration files to provision an AKS cluster on Azure.

#Az Azure account
Launch Virtual Machine (with 2cpu 4gb Ram) ubuntu 20
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash (install Azure CLI)
a configured Azure CLI
az login
Sudo apt-get update
$ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
$ sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)]
https://apt.releases.hashicorp.com $(lsb_release -cs) main"
$ sudo apt update
$ sudo apt install terraform
$ terraform version



#Clone Repository:

git clone https://github.com/hashicorp/learn-terraform-provision-aks-cluster
cd learn-terraform-provision-aks-cluster
az ad sp create-for-rbac --skip-assignment
You will get the APP id and Password in O/P (Update APP id And Password) in
terraform.tfvars
● $ terraform init
● $ terraform apply
You can see this terraform apply will provision an Azure resource group
and an AKS cluster. Confirm the apply with a yes
(Note : If you get the error try with Different Region)


#Configure kubectl

$ az aks get-credentials --resource-group $(terraform output -raw resource_group_name) --name
$(terraform output -raw kubernetes_cluster_name)Merged "light-eagle-aks" as current context in
/Users/dos/.kube/config

#Access Kubernetes Dashboard:-

$ az aks browse --resource-group $(terraform output -raw resource_group_name)
--name $(terraform output -raw kubernetes_cluster_name)

#Clean up your workspace
terraform destroy


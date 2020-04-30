# Helm-Kubernetes-Example
A small microservices achitecture example using kubernetes as orchestration engine and helm as deployment tool

## Pre-requisites
To create your kubernetes cluster we will need to have installed the following tools on your computer: 
1. AWS CLI (Configured with your aws account credentials)
1. EKS CLI 
1. Helm 
1. Kubectl 

## How to create your cluster
1. Once you have installed eks cli and cloned this repo, open a terminal and run the following command ``` eksctl create cluster -f ./eks/cluster.yaml ```. This command will create an EKS resource in your AWS account and its dependencies specified in the yaml file (2 node instance groups, one with a public IP associated and one private, with 2 t2.micro instances each). 
1. After your cluster is up and running, run the following command ``` helm install <release-name> ./eks-jc-chart ```. This command will start to translate all template files into actual kubernetes resources (deployments, ingresses and clusterIP's). Once kubernetes have finished creating the resources, you will see an output indicating the name of the new helm release. 

## Mess around with your new created infraestructure
1. Try to consume the flask application by opening your browser an navigate to http://<your-aws-network-loadBalancer-dns>/flask. 
1. Try to reach some of the static files hosted on nginx container by navigating to http://<your-aws-network-loadBalancer-dns>/images/<image-name>
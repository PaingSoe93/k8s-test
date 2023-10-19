# Instruction

## Pre requirement

- [AWS CLI](https://aws.amazon.com/cli/) installed and configured with appropriate permissions.
- [eksctl](https://eksctl.io/) tool for EKS cluster creation.
- [kubectl](https://kubernetes.io/docs/tasks/tools/) for deploying applications and services on the EKS cluster.

## Configuration

### 1. AWS Profile Setup

Before you can create the EKS cluster, ensure you've set up your AWS CLI profile:

```
aws configure --profile <your-profile-name>
```

Replace `<your-profile-name>` with your desired profile name. This profile will store the AWS Access Key, Secret Key, region, and output format.

### 2. EKS Cluster Creation

Navigate to the k8s directory and execute the following command to create the EKS cluster:

```
eksctl create cluster -f eks-cluster.yaml
```

This will initiate the cluster creation process which might take several minutes. Once completed, eksctl will automatically configure kubectl to use the newly created cluster.

### 3. Application and Service Deployment

With the EKS cluster ready, deploy the Node.js application and the associated service:

```
kubectl apply -f k8s/server-deployment.yaml

kubectl apply -f k8s/server-cluster-ip-service.yaml
```

## Cleaning Up

To delete the EKS cluster and all associated resources:

```
eksctl delete cluster -f k8s/eks-cluster.yaml
```

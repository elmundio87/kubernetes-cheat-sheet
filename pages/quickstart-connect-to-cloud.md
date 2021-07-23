[Home](../index.md)

Once you've logged in, you can verify the connection via `kubectl get svc`
# Azure Kubernetes Service (AKS) quickstart

> These commands can be run from the Azure Cloud Shell or locally. If run locally you will need to install the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/).

## Set target Azure subscription

This can be the subscription ID or name.

```
az account set -s "subscription"
```

## Setup kubeconfig

You will need to reference the AKS cluster's name, as well as its resource group.

```
az aks get-credentials --resource-group $clusterResourceGroup --name $clusterName --overwrite-existing -a
```

# Elastic Kubernetes Service (AWS EKS) quickstart

You will need to install the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html).

> To run the following command, you must have permission to use the eks:DescribeCluster API action with the cluster that you specify. For more information, see [Amazon EKS identity-based policy examples](https://docs.aws.amazon.com/eks/latest/userguide/security_iam_id-based-policy-examples.html).

## Setup kubeconfig

```shell
aws eks --region $region update-kubeconfig --name $clusterName
```

# Google Kubernetes Engine (GKE) quickstart

You will need to install the [gcloud](https://cloud.google.com/sdk/docs/install) CLI.

## Setup kubeconfig

```shell
gcloud container clusters get-credentials $clusterName
```

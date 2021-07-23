[Home](../index.md)

# Kubectl AKS quickstart

These commands can be run from the Azure Cloud Shell or locally.

## Set target Azure subscription

This can be the subscription ID or name.

```
az account set -s "subscription"
```

## Setup credentials

You will need to reference the AKS cluster's name, as well as its resource group.

```
az aks get-credentials --resource-group "resource group name" --name "AKS cluster name" --overwrite-existing -a
```

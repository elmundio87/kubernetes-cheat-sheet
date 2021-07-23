<!--
Markdown guide: https://github.github.com/gfm/
-->

[Home](../index.md)

> THIS PAGE IS WORK IN PROGRESSs

# Common information gathering

These commands will help with debugging issues within a Kubernetes cluster

NOTE: Most of the following command will  support `--all-namespaces` in lieu of `-n`.

## "Get" commands

Get all namespaces in a cluster

```shell
kubectl get ns
```

Get all pods in a namespace

```shell
kubectl get pod -n "$namespace"
```

Get all pods in a namespace (with detailed information in yaml format)

```shell
kubectl get pod -n "$namespace" -o yaml
```

Get all deployments in a namespace
```shell
kubectl get pod -n "$namespace"
```

Get all nodes in the cluster
```
kubectl get nodes
```

Get all persistent volumes in a namespace
```shell
kubectl get pv -n "$namespace"
```

Get all items in a namespace

```shell
kubectl get all -n "$namespace"
```

## Remote access

Log into a pod

```shell
kubectl exec --stdin --tty "$podName" -n "$namespace" -- /bin/sh

# or

kubectl exec -it "$podName" -n "$namespace"
```

Log into a sidecar container

```shell
kubectl exec -it "$podName" -c "sidecarName" -n -x sh
```

Exec commands on an AKS node (without SSH)

```shell
az vmss run-command invoke --name "$scaleSetName" --command-id RunShellScript --resource-group "scaleset resource group name" --instance-id "get this from the portal" --scripts "echo hello world!"
```

Exec commands on set of AKS nodes

```shell
az vmss list-instances --name "$scaleSetName" --resource-group "$scaleSetResourceGroup" --query "[].id" --output tsv | az vmss run-command invoke --command-id RunShellScript--scripts "echo hello world!" --ids @-
```

## Logs gathering

Gather pod IP addresses

```shell
kubectl get pods -o custom-columns=NAME:.metadata.name,IP:.status.podIP -n "$namespace"
```
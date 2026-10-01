
# About
Preparing the Kubernetes tools.

# Steps

## Install kubectl
```
$ snap install kubectl --classic
```

## Setup kubectl
- Get configuration with technical support in your organization

# Main commands for kubectl
Get contexts
```
$ kubectl config get-contexts
```

Get namespaces from specific context
```
$ kubectl get namespaces --context=<context-name>
```

Get PODs from specific namespace
```
$ kubectl get pods --context=<context-name> --namespace <namespace>
```

Get PODs details from specific namespace
```
$ kubectl get pods -o wide --context=<context-name> --namespace <namespace-name>
```

Get PODs CPU, memory and swap from specific namespace
```
$ kubectl top pod --containers --show-swap --context=<context-name> --namespace <namespace-name>
```

Viewing pod replacement
```
$ watch -n 1 kubectl get pods --context=<context-name> --namespace <namespace>
```

Logs from specific POD
```
$ kubectl logs <pod-name> --context=<context-name> --namespace <namespace-name>
```

Status from specific POD
```
$ kubectl get pod <pod-name> -o wide --context=<context-name> --namespace=<namespace>
```

Details from specific POD
```
$ kubectl describe pod <pod-name> --context=<context-name> --namespace account-block

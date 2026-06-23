
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
- Get namespaces
```
$ kubectl get namespaces
```

- Get contexts
```
$ kubectl config get-contexts
```

- Show current context
```
$ kubectl config current-context
```

- Change context
```
$ kubectl config use-context <context-name>
```

- Get PODs from namespace
```
$ kubectl get pods --namespace <namespace>
```

- Show change of PODs
```
$ watch -n 1 kubectl get pods --namespace <namespace>
```

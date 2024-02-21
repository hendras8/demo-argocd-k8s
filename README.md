## demo-argocd-k8s

## Prerequisites

Before we begin, make sure you have the following prerequisites in place:

```
Docker: Install Docker on your machine to run the Kubernetes cluster with Kind. Refer to the official Docker documentation here for installation instructions specific to your operating system.

Kind: Install Kind, which is a tool for creating lightweight Kubernetes clusters locally. Kind is distributed as a single binary and can be easily installed. 

kubectl: Install the Kubernetes command-line tool, kubectl, to interact with the Kubernetes cluster. 
```

## How to Run ?

create kind cluster
```shell
kind create cluster --config=kind-argocd.yaml
```

create namespace 
```shell
 kubectl apply -f namespace.yaml
```

add ingress to the cluster 
```shell
kubectl apply -f deployment.yaml
```

install ArgoCD
```shell
kubectl apply -f install.yaml
```

add ingress ArgoCD
```shell
kubectl apply -f ingress-argocd.yaml
```


Obtaining the Argo CD Admin Password
To log in to the Argo CD dashboard, you need the admin password. Run the following command to retrieve the password:

```shell
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
```



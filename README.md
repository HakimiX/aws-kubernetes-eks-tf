# Deploying a Kubernetes Cluster with AWS EKS

**Technologies**: 
* Node.js _(v16.20.1 LTS)_
* Vue3, Nuxt3 _(v3.6.2)_

AWS EKS (Elastic Container Service for Kubernetes) is a managed Kubernetes service that 
allows you to run Kubernetes on AWS without the hassle of managing the Kubernetes control
plane. The Kubernetes control plane is responsible for how Kubernetes communicates with 
the cluster (starting, stopping, and scheduling containers).


### Table of Contents
- [Deploying a Kubernetes Cluster with AWS EKS](#deploying-a-kubernetes-cluster-with-aws-eks)
    - [Table of Contents](#table-of-contents)
    - [Introduction](#overview)
    - [Sources](#sources)

## Overview

### Frontend

The frontend is a simple application that is built with Node.js, TypeScript, Vue3 and Nuxt3.

## Local Development

### Prerequisites
* [docker-desktop](https://www.docker.com/products/docker-desktop)
* [kubectl](https://kubernetes.io/docs/tasks/tools/)
* [kubectx + kubens](https://github.com/ahmetb/kubectx#homebrew-macos-and-linux)

### Working with the cluster locally using docker-desktop

1. Create a new namespace using the following command:
```shell
kubectl create namespace <namespace-name>
```
> Note: Replace `<namespace-name>` with the name of your namespace and update the `/infrastructure/helm/config/local.yaml`file with the name of your namespace.

Confirm that the namesapce was created successfully by running the following command:
```shell
kubectl get namespaces
```

2. Use `kubens` to set the namespace as the default namespace for the current context:
```shell
kubens <namespace-name>
```

### Sources

* [amazon-eks-cluster](https://logz.io/blog/amazon-eks-cluster)

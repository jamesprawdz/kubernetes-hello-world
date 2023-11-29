# Basic Kubernetes Project

## Introduction

Welcome to my Basic Kubernetes Project! This project is designed to provide a hands-on experience with Kubernetes, using Minikube as a local environment. It covers essential Kubernetes concepts such as multiple namespaces, network policies, Role-Based Access Control (RBAC), liveness and readiness probes, and includes a restricted account configuration for best practices.

## Project Structure

The project includes several YAML files, each serving a specific purpose:

1. **BusyBox Pod**: [busybox.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/busybox.yaml) - Defines a standalone BusyBox pod in its namespace.
2. **Network Policy**: [example-network-policy.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/example-network-policy.yaml) - An example of a network policy applied to the hello-world app.
3. **Hello World Deployment**: [hello-world-deployment.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/hello-world-deployment.yaml) - Deployment configuration for the hello-world application, including liveness and readiness probes.
4. **Hello World Service**: [hello-world-service.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/hello-world-service.yaml) - Service definition for the hello-world application.
5. **RBAC Role Binding**: [pod-service-reader-binding.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/pod-service-reader-binding.yaml) - RoleBinding for the restricted service account.
6. **RBAC Role**: [pod-service-reader-role.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/pod-service-reader-role.yaml) - Defines a Role for accessing pods and services.
7. **Restricted Service Account**: [restricted-sa.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/restricted-sa.yaml) - A restricted service account for best practices.
8. **Test Pod**: [test-pod.yaml](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/test-pod.yaml) - A test pod using the restricted service account.

## Getting Started

### Prerequisites

- Install [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- Install [kubectl](https://kubernetes.io/docs/tasks/tools/)

### Setup

1. **Start Minikube**:
   ```bash
   minikube start

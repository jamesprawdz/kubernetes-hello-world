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
- Install [Docker](https://docs.docker.com/get-docker/) or your preferred container runtime.

### Setup

1.  Start Minikube:

    `minikube start`

2.  Apply the YAML Configurations: Navigate to the project directory and apply the YAML files. For example:

    `kubectl apply -f hello-world-deployment.yaml`

    Repeat this step for each YAML file in the project.

### Accessing the Hello World Application

1.  Expose the Hello World Service:

    `minikube service hello-world`

    This command will open the hello-world application in your default browser.

### Testing RBAC and Network Policies

#### Understanding RBAC:
While the RBAC configuration in this project is basic, it serves as an introduction to Kubernetes' access control mechanisms. The RBAC roles and bindings in files like [`pod-service-reader-role.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/pod-service-reader-role.yaml) and [`pod-service-reader-binding.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/pod-service-reader-binding.yaml) illustrate the actions that are allowed. Although testing RBAC in this context is not critical, it's beneficial to understand how these configurations define and restrict access within the Kubernetes cluster.

#### Testing Network Policies:
The network policies, as defined in [`example-network-policy.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/example-network-policy.yaml), are crucial for understanding traffic control within your Kubernetes environment. To effectively test these policies:

1. **SSH into Different Pods**: Access the SSH shells of different pods across various namespaces.
2. **Attempt Connections**: Try to connect to the hello-world application or pods from these different namespaces.
3. **Observe Traffic Flow**: Monitor how modifications in the network policy affect the ability of these pods to communicate with the hello-world application.

This hands-on approach to testing will provide deeper insights into how network policies impact pod communication within and across namespaces.

### Best Practices

1. **Resource Limits and Requests**: In files like [`busybox.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/busybox.yaml) and [`hello-world-deployment.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/hello-world-deployment.yaml), resource requests and limits are specified for containers. This practice ensures efficient resource utilization and prevents any single application from consuming excessive resources.

2. **Liveness and Readiness Probes**: The [`hello-world-deployment.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/hello-world-deployment.yaml) includes liveness and readiness probes. These probes help in managing the application's lifecycle by checking its health and readiness to serve traffic.

3. **Using Network Policies**: The [`example-network-policy.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/example-network-policy.yaml) demonstrates the use of network policies to control the traffic flow at the IP address or port level. This is crucial for enhancing the security of your Kubernetes environment.

4. **Role-Based Access Control (RBAC)**: Files like [`pod-service-reader-role.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/pod-service-reader-role.yaml) and [`pod-service-reader-binding.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/pod-service-reader-binding.yaml) implement RBAC, which is essential for secure access control in Kubernetes.

5. **Using a Restricted Service Account**: The [`restricted-sa.yaml`](https://github.com/jamesprawdz/kubernetes-hello-world/blob/main/restricted-sa.yaml) file defines a restricted service account, which is a best practice for limiting the permissions and access scope of applications running in your cluster.

6. **Namespace Usage**: The deployment of resources in specific namespaces (as seen in `busybox.yaml`) is a good practice for organizing and isolating resources within a Kubernetes cluster.

### Conclusion

This project serves as a practical guide to understanding and implementing fundamental Kubernetes concepts. By exploring and modifying the provided configurations, you can gain deeper insights into how Kubernetes works and how to manage applications effectively within a Kubernetes cluster.

# Basic `kubectl` Commands

`kubectl` is a powerful command-line tool used to interact with Kubernetes clusters. It enables you to manage, deploy, and inspect resources in the cluster. Here are some essential `kubectl` commands for working with Kubernetes:

## 1. `kubectl get`

Retrieve information about resources in the cluster.

- List all pods:
  ```bash
  kubectl get pods
  ```

- List all deployments:
  ```bash
  kubectl get deployments
  ```

- List all services:
  ```bash
  kubectl get services
  ```

- List all nodes:
  ```bash
  kubectl get nodes
  ```

## 2. `kubectl describe`

Get detailed information about a specific resource.

- Show detailed information about a specific pod:
  ```bash
  kubectl describe pod <pod-name>
  ```

- Show detailed information about a specific deployment:
  ```bash
  kubectl describe deployment <deployment-name>
  ```

- Show detailed information about a specific service:
  ```bash
  kubectl describe service <service-name>
  ```

## 3. `kubectl create`

Create a resource from a file or inline definition.

- Create a resource defined in a YAML file:
  ```bash
  kubectl create -f <file.yaml>
  ```

- Create a deployment from a specified container image:
  ```bash
  kubectl create deployment <deployment-name> --image=<image-name>
  ```

## 4. `kubectl delete`

Delete a resource.

- Delete a specific pod:
  ```bash
  kubectl delete pod <pod-name>
  ```

- Delete a specific deployment:
  ```bash
  kubectl delete deployment <deployment-name>
  ```

- Delete a specific service:
  ```bash
  kubectl delete service <service-name>
  ```

## 5. `kubectl apply`

Apply changes to a resource.

- Apply changes to a resource defined in a YAML file:
  ```bash
  kubectl apply -f <file.yaml>
  ```

- Apply changes to all resources defined in a directory:
  ```bash
  kubectl apply -f <dir>
  ```

## 6. `kubectl logs`

View the logs of a pod.

- Print the logs of a specific pod:
  ```bash
  kubectl logs <pod-name>
  ```

## 7. `kubectl exec`

Execute a command inside a container of a pod.

- Run an interactive shell in a specific pod:
  ```bash
  kubectl exec -it <pod-name> -- <command>
  ```

## 8. `kubectl port-forward`

Forward local ports to a pod.

- Forward a local port to a specific pod:
  ```bash
  kubectl port-forward <pod-name> <local-port>:<pod-port>
  ```

These are just a few examples of the most commonly used `kubectl` commands. There are many more commands available, and you can explore additional options and parameters in the Kubernetes documentation or by using `kubectl --help`.

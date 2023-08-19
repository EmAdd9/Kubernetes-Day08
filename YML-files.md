# YAML Files for Kubernetes

**YAML** (YAML Ain't Markup Language) is a human-readable data serialization format commonly used for defining configurations in Kubernetes. YAML files are used to describe the desired state of Kubernetes objects, such as pods, services, deployments, and more. They follow a hierarchical structure with key-value pairs and indentation to define the properties and values of each object.

## Deployment YAML Files

Deployment YAML files in Kubernetes are used to define and manage a set of identical pods. They ensure that a specified number of pod replicas are running and handle rolling updates and rollbacks. Deployments provide declarative updates for pods and are widely used for managing stateless applications.

Here's an example of a Deployment YAML file:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: nginx:latest
        ports:
        - containerPort: 80
```

In this example:
- `apiVersion` specifies the Kubernetes API version being used.
- `kind` defines the type of Kubernetes object being created (in this case, a Deployment).
- `metadata` contains information about the Deployment, such as its name.
- `spec` specifies the desired state of the Deployment.
- `replicas` defines the desired number of pod replicas.
- `selector` is used to match the pods controlled by the Deployment.
- `template` defines the pod template used to create the replicas.
- `containers` specifies the list of containers running within the pod template.

## Service YAML Files

Service YAML files in Kubernetes are used to define a stable endpoint for accessing a group of pods. Services enable load balancing and service discovery within the cluster. They provide an abstraction layer that allows pods to be replaced or scaled without affecting the application's accessibility.

Here's an example of a Service YAML file:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: NodePort
```

In this example:
- `apiVersion` specifies the Kubernetes API version being used.
- `kind` defines the type of Kubernetes object being created (in this case, a Service).
- `metadata` contains information about the Service, such as its name.
- `spec` specifies the desired state of the Service.
- `selector` is used to match the pods that the Service will target.
- `ports` defines the list of ports to be exposed by the Service.
- `protocol` specifies the protocol to be used (in this case, TCP).
- `port` specifies the port number for accessing the Service.
- `targetPort` specifies the port number on the pods to which traffic should be forwarded.
- `type` defines the type of Service. NodePort exposes a service externally to the cluster by means of the target nodes' IP address and the NodePort.

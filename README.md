# Kubernetes (K8s)
**Kubernetes, also known as K8s**, is an open source system/platform for automating deployment, scaling, and management of containerized applications.
It helps in efficiently managing clusters of containers, ensuring high availability, scalability, and fault tolerance.

The abbreviation K8s comes from a common numeronym pattern where the first and last letter of a word are kept, and the number in between represents the count of omitted letters. <br>
- K → First letter of Kubernetes <br>
- 8 → Number of letters between K and s (ubernete) <br>
- s → Last letter of Kubernetes <br>

Thus, Kubernetes → K8s <br>

This pattern is used in other tech abbreviations as well, such as: <br>
- i18n → Internationalization (18 letters omitted) <br>
- l10n → Localization (10 letters omitted) <br>

# Who Developed K8s?
**Kubernetes was originally developed by Google** and was based on their internal container management system called Borg.
In 2015, Google open-sourced Kubernetes **and donated it to the Cloud Native Computing Foundation (CNCF)**, which now maintains it.

# What Problem Does Kubernetes Solve?
Kubernetes manages containers, making sure they run efficiently, scale when needed, and recover from failures.

> Automated Scaling (Manual Scaling Was Inefficient)
- Before K8s: Applications had to be scaled manually, either by adding/removing VMs or containers.
- With K8s: Horizontal Pod Autoscaler (HPA) and Vertical Pod Autoscaler (VPA) allow automatic scaling based on demand.

> High Availability & Self-Healing (Downtime Was a Risk)
- Before K8s: If an application crashed, manual intervention was needed to restart or redeploy it.
- With K8s: Self-healing ensures that failed containers are automatically restarted, rescheduled, or replaced without manual action.

> Service Discovery & Load Balancing (Networking Was Complex)
- Before K8s: Applications needed manual IP management or a separate load balancer to distribute traffic.
- With K8s: Built-in service discovery and load balancing (ClusterIP, NodePort, LoadBalancer, and Ingress) ensure seamless traffic distribution.

> Rolling Updates & Rollbacks (Deployment Was Risky)
- Before K8s: Deploying a new version required stopping the service, leading to downtime.
- With K8s: Rolling updates allow new versions to be deployed gradually, while rollback can restore the previous version instantly if something fails.


Before Kubernetes, managing containerized applications manually was complex.
Kubernetes solves several challenges, such as:
- Automated Deployment & Scaling: Easily deploy and scale applications up or down based on demand.
- Self-Healing: If a container crashes, Kubernetes automatically restarts it.
- Load Balancing: Distributes traffic among running containers to prevent overload.

# Key K8s components
> Nodes: (Server/Machine)
  - A node is a server/machine (physical or virtual) where applications run.

> Pods: (Layer on top of container)
  - The smallest unit in K8s, containing one or more containers.
  - If multiple containers are needed for an application (e.g., frontend + backend), they can be inside the same pod.
  - Pod is a layer on top of the container (or Abstraction over container). A pod usually contains a single container, but it can have multiple if needed.

> Containers: (Application runtime)
  - Containers are lightweight, portable environments that run applications.

![image](https://github.com/user-attachments/assets/6de4969e-4d9b-432a-837c-d76ed13a437c)

> Cluster: (Group of Servers/Machines Working Together)
  -  A Cluster is a collection of Nodes (servers) that work together to run applications & serve requests.
  -  It consists of a **Master Node (Control Plane) and multiple Worker Nodes**.

**Restaurant Analogy:**
- Node: A restaurant kitchen - where food (i.e. applications) is prepared
- Pod: A table in a restaurant - where different dishes (i.e. containers) are served together.
- Container: A dish being cooked
- Cluster: Group of restaurant working together - to serve customers (i.e. requests)

**Physical Laptop Analogy:**
- Node: Your physical laptop <br>
Just like your laptop has CPU, RAM, storage, and an OS, a Node in Kubernetes is a machine (physical or virtual) that provides resources for running applications. <br>

- Pod: A Running Application Process (Like a Java Process on Your Laptop) <br>
When you run a Spring Boot application using java -jar myapp.jar, it starts a process that consumes memory and CPU — this is similar to a Pod in Kubernetes. <br>

- Container: A Self-Contained Environment for an Application (Like a Virtual Machine or Docker Container on Your Laptop) <br>
If you run your Spring Boot app inside a Docker container, it has its own runtime environment, dependencies, and isolated filesystem. <br>

- Cluster: A Network of Multiple Laptops (or a Cloud of Machines Working Together) <br>
If you imagine multiple laptops connected via a network, where each laptop is a Node, and they all work together as a unit, that forms a Kubernetes Cluster. <br>

A Pod can contain one or more containers. <br>
A Pod is the process running your application, and inside the Pod, containers provide the actual execution environment. <br>
A Pod is a wrapper around one or more containers. It provides: <br>
	•	A shared network (all containers in a Pod can talk to each other using localhost).
	•	A shared storage volume (if needed).
	•	A single unit of deployment in Kubernetes.
In Kubernetes, a Pod groups multiple containers together so they can share the same network and storage. <br>


**In Kubernetes,**
> Pod
- Each Pod (and not individual containers) in K8s gets its own internal IP address.
- Pods communicate with each other using IPs addresses.
- Pods are temporary (ephemeral) i.e. they can die easily — if a Pod crashes, Kubernetes replaces it with a new one with a new IP address.
- `Pod` is another abstraction layer on top of `containers`.

Please note, a container crashing does not mean the Pod is dead. A Pod can have multiple containers, and if one container crashes, the Pod itself may still be running with other containers intact.

Example:
If you deploy a Spring Boot app to Kubernetes, Kubernetes creates a Pod that contains a Container running the Spring Boot app.
If your app also needs a sidecar container (e.g., a logging agent), both containers will be inside the same Pod.

Therefore, a Pod is like a wrapper that holds one or more Containers. A Pod usually contains a single Container, but it can have multiple if needed.

> Service
- A Service component of K8s provides a stable/permanent IP address and DNS name that can be attached to each pod and to access those pods.
- Even if the pod dies, and is replaced by a new one, it's permanent IP address provided by the service remains the same.

> Ingress
- By default, K8s services are not accessible from outside the K8s cluster.
- Ingress is a component that routes/forwards external HTTP/HTTPS traffic to the appropriate internal service.
- It acts like a web gateway for the cluster.

![image](https://github.com/user-attachments/assets/2743ac6f-8b61-4feb-b692-cea4f6ef62e9)

> ConfigMap
- A ConfigMap, a component of K8s, stores non-sensitive configuration data (e.g., environment variables, app settings) for the application in plain text.
- Useful for keeping app configuration separate from the container image.

> Secret
- A Secret, a component of K8s, stores sensitive information such as passwords, tokens, and certificates.
- Data is stored in base64-encoded format, offering basic security.
  
![image](https://github.com/user-attachments/assets/f525c4a8-0685-47e6-a865-df7c6c398891)

> Volume
- A Volume attaches storage (like, a physical hard drive plugged) to a Pod so that data can be stored and accessed by containers.
- Local Storage: This is storage provided by the node (VM or physical machine) where the Pod is running. Suitable for temporary or short-lived data.
- Remote/Cloud Storage (outside K8s cluster): Used when persistent and shared storage is needed. (like, MongoDB Cloud)

![image](https://github.com/user-attachments/assets/0306d02c-8f7e-45c1-a4ce-c1a15049d541)

> Deployment
- Imagine, running a single pod on a single node - If it dies, the app goes down. Therefore, it's recommended to replicate pods to ensure high availability and no downtime.
![image](https://github.com/user-attachments/assets/8cd984bc-880c-426c-bf61-390a316e35e3)

- Therefore, replicate everything to avoid downtime in production
![image](https://github.com/user-attachments/assets/fae0c24c-c299-41e0-9f2b-10cfcef1ed53)
![image](https://github.com/user-attachments/assets/600fdfe7-55bb-470d-aa19-3795cbb88d8c)

- A Deployment is a K8s component that manages replicas (copies) of Pods to ensure high availability and no downtime. Instead of creating Pods directly, you define a blueprint (template) for the Pod and specify how many replicas should run. That blueprint is Deployment. If a Pod crashes, the Deployment automatically creates a new Pod to replace it.

- `Deployment` is another abstraction layer on top of `pods`.
- `Deployment` is used for stateless applications (apps that don’t store data inside the Pod, like APIs, web servers) & is not used for stateful applications (like, databases that have state/data)!
- In practice, developers work with `Deployments`, not individual Pods.

> StatefulSet
- A StatefulSet is used to manage stateful applications, like databases, that store data and need to keep track of their state.
- Used for apps like MongoDB, MySQL, Cassandra, etc., which can’t use Deployments due to their stateful nature.
- StatefulSets are complex to configure and manage. That’s why in many real-world setups, databases are hosted outside the Kubernetes cluster (e.g., using MongoDB Atlas, AWS RDS, etc.).

![image](https://github.com/user-attachments/assets/20561741-fa98-415f-8a49-5427ff138063)

# K8s Architecture
Kubernetes manages containers, making sure they run efficiently, scale when needed, and recover from failures.

K8s follows a **Master-Worker** architecture. 
K8s cluster consists of one Master node and muultiple worker nodes. <br>

> Master Node (or, Control plane): This is the brain of K8s, that makes the decisions. <br>

  It includes, <br>
- **API Server:** <br>
  Acts as the main communication hub between users, applications, and Kubernetes. <br>
  The entry point to K8s cluster or for K8s commands <br>
  Handles requests (like deploying applications) and communicates with other components. <br>

- **Scheduler:** (Task allocator) <br>
  Assigns new pods to available workers (nodes) based on resources & policies. <br>

- **Controller Manager:** <br>
  Ensures correct number of pods & nodes are running. <br>

- **etcd:** (like, a database) <br>
  A key-value store that stores cluster state & configuration. <br>

- **cloud controller manager** <br>
  Integrates with underlying cloud provider(s). <br>

> Worker Node: This is where the actual applications (containers) run. <br>

  It includes, <br>
- **Kubelet:** Ensures containers in a pod & the pods as well are running correctly. <br>

- **Container runtime:** It's a software (Eg, Docker) responsible for running containers. <br>

# Namespace
- A Namespace in Kubernetes is a virtual cluster within a Kubernetes physical cluster.
- Think of it like creating separate folders/environments in the same machine to organize and isolate your workloads.
- It allows you to create multiple isolated environments within the same cluster.
- Namespace groups resources like Pods, Services, ConfigMaps, Secrets, etc.

## Benefits of Namespaces? <br>
- `Isolation`	Keeps resources of different teams, apps, or environments separate
- `Access Control (RBAC)`	Assign permissions on a per-namespace basis (Example: Devs can access only the dev namespace, not prod)
- `Environment Separation`	Manage dev, staging, and prod etc. in one cluster without interference
- `CI/CD Pipelines` Use namespaces to deploy and test code in isolation
- `Resource Management`	Set quotas to avoid overuse of CPU/memory

## Default Namespace <br>
- If you don't specify a namespace when creating a resource, it goes into the `default` (built-in) namespace.
- By default, Kubernetes has 4 built-in namespaces:
    - `default` The default namespace for resources that don't specify one.
    - `kube-system` Used by Kubernetes core components (DNS, controller, scheduler, etc.).
    - `kube-public` Readable by all users (rarely used; cluster-info only), including those not authenticated.
    - `kube-node-lease` Used for node heartbeat data (helps check if nodes are healthy)

## Best practice <br>
- To use one namespace per environment (e.g., dev, test, prod). In projects, namespaces are used to represent different environments.

## Basic Commands for namespaces <br>

```
# List all namespaces
kubectl get namespaces
```

```
# Create a new namespace
kubectl create namespace dev1
```

```
# Run a command in a specific namespace
kubectl get pods -n dev1
kubectl apply -f my-app.yaml -n dev1
```

```
# To verify current namespace
kubectl config view --minify --output 'jsonpath={..namespace}'
```

```
# To switch to a different namespace
kubectl config set-context --current --namespace=dev1
```

```
# To list objects in a specific namespace (Pods, Services, Deployments, ReplicaSets but not other resources like ConfigMaps or Secrets.)
kubectl get all -n dev1
```
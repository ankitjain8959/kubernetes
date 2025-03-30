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
> Containers: (Application runtime)
  - Containers are lightweight, portable environments that run applications.
 
> Nodes: (Machine)
  - A node is a machine (physical or virtual) where applications run.

> Pods: (that contain one or more containers)
  - The smallest unit in K8s, containing one or more containers.
  - If multiple containers are needed for an application (e.g., frontend + backend), they can be inside the same pod.
  - Pod is a layer on top of the container. A pod usually contains a single container, but it can have multiple if needed.

> Cluster: (Group of Machines Working Together)
  -  A Cluster is a collection of Nodes (machines) that work together to run applications & serve requests.
  -  It consists of a **Master Node (Control Plane) and multiple Worker Nodes**.

**Restaurant Analogy:**
- Container: A dish being cooked
- Node: A restaurant kitchen - where food (i.e. applications) is prepared
- Pod: A table in a restaurant - where different dishes (i.e. containers) are served together.
- Cluster: Group of restaurant working together - to serve customers (i.e. requests)

**Physical Laptop Analogy:**
- Node: Your physical laptop <br>
Just like your laptop has CPU, RAM, storage, and an OS, a Node in Kubernetes is a machine (physical or virtual) that provides resources for running applications. <br>

- Cluster: A Network of Multiple Laptops (or a Cloud of Machines Working Together) <br>
If you imagine multiple laptops connected via a network, where each laptop is a Node, and they all work together as a unit, that forms a Kubernetes Cluster. <br>

- Container: A Self-Contained Environment for an Application (Like a Virtual Machine or Docker Container on Your Laptop) <br>
If you run your Spring Boot app inside a Docker container, it has its own runtime environment, dependencies, and isolated filesystem. <br>

- Pod: A Running Application Process (Like a Java Process on Your Laptop) <br>
When you run a Spring Boot application using java -jar myapp.jar, it starts a process that consumes memory and CPU—this is similar to a Pod in Kubernetes. <br>

A Pod can contain one or more Containers. <br>
A Pod is the process running your application, and inside the Pod, Containers provide the actual execution environment. <br>
A Pod is a wrapper around one or more Containers. It provides: <br>
	•	A shared network (all containers in a Pod can talk to each other using localhost).
	•	A shared storage volume (if needed).
	•	A single unit of deployment in Kubernetes.
In Kubernetes, a Pod groups multiple Containers together so they can share the same network and storage. <br>


In Kubernetes,
- Each pods (and not the containers) gets it's own internal IP address using which they can communicate with each other.
- `Pods` are ephemeral (i.e. temporary/they can die easily). If a Pod crashes, Kubernetes replaces it with a new one, which gets a new IP address.
- `Service` component of K8s provides a permanent IP address that can be attached to each pod. Therefore, even if the pod dies, and is replaced by a new one, it's permanent IP address provided by the service remains the same.
- By default, Kubernetes Services are not accessible from outside the cluster. `Ingress` is a Kubernetes component that routes/forwards external HTTP/HTTPS traffic to the correct Service inside the cluster.

![image](https://github.com/user-attachments/assets/f525c4a8-0685-47e6-a865-df7c6c398891)

Example:
If you deploy a Spring Boot app to Kubernetes, Kubernetes creates a Pod that contains a Container running the Spring Boot app.
If your app also needs a sidecar container (e.g., a logging agent), both containers will be inside the same Pod.

Therefore, a Pod is like a wrapper that holds one or more Containers. A Pod usually contains a single Container, but it can have multiple if needed.

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


# K9s
It's a user-friendly, real-time CLI tool to interact with Kubernetes clusters. <br>

Unlike K8s, K9s is not an abbreviation following the numeronym pattern. Instead, it's a play on words: <br>
- "K9" (canine) is a reference to dogs, which are known as loyal companions.

In this case, K9s is designed to be a "companion" for Kubernetes, helping developers and operators manage K8s clusters efficiently. <br>

So, K9s is not an abbreviation but a creative naming choice, implying that it’s a faithful and useful tool for interacting with Kubernetes. <br>

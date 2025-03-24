# Kubernetes (K8s)
Kubernetes, also known as K8s, is an open source system/platform for automating deployment, scaling, and management of containerized applications.
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
Kubernetes was originally developed by Google and was based on their internal container management system called Borg.
In 2015, Google open-sourced Kubernetes and donated it to the Cloud Native Computing Foundation (CNCF), which now maintains it.

# What Problem Does Kubernetes Solve?
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



# K9s
It's a user-friendly, real-time CLI tool to interact with Kubernetes clusters. <br>

Unlike K8s, K9s is not an abbreviation following the numeronym pattern. Instead, it's a play on words: <br>
- "K9" (canine) is a reference to dogs, which are known as loyal companions.

In this case, K9s is designed to be a "companion" for Kubernetes, helping developers and operators manage K8s clusters efficiently. <br>

So, K9s is not an abbreviation but a creative naming choice, implying that it’s a faithful and useful tool for interacting with Kubernetes. <br>

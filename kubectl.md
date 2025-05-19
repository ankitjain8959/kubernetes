# minikube (tool used for local testing)
- Minikube is a tool that lets you run Kubernetes locally on your own computer.
- Minikube sets up a mini version of Kubernetes on your laptop or PC. (That’s why it’s called “mini” kube!)
- It creates a single-node Kubernetes cluster — just one virtual machine that acts like a real Kubernetes cluster.

> How minikube works:
- You install Minikube.
- It starts a lightweight virtual machine (or container) with Kubernetes running inside.
- You can now use kubectl (command line tool for kubernetes cluster) commands to create Pods, Deployments, Services, etc.
- It simulates a real Kubernetes environment for practice or development.

<img width="889" alt="image" src="https://github.com/user-attachments/assets/8811fc4b-d205-4b27-8deb-c8bd6be554f6" />

## kubectl? (pronounced "cube control" - command line tool for kubernetes cluster)
- kubectl is the command-line tool used to interact with Kubernetes (like, a remote control for your kubernetes cluster)
- It lets you create, manage, inspect, and delete Kubernetes resources like: deployments, pods, services, configMaps, secrets etc.
- You use it to send commands to the Kubernetes API server, which is the brain of the cluster.

### kubectl commands
CRUD commands: <br>
CRUD commands: <br>
- Create deployment : kubectl create deployment [name] <br>
- Edit deployment : kubectl edit deployment [name] <br>
- Delete deployment : kubectl delete deployment [name] <br>

Status of different K8s components <br>
- Get nodes : kubectl get nodes <br>
- Get pod: kubectl get pod <br>
- Get services : kubectl get services <br>
- Get replicaset : kubectl get replicaset <br>
- Get deployment : kubectl get deployment <br>

View detailed information about a specific Kubernetes resource <br>
- Describe deployment : kubectl describe deployment [name] <br>
- Describe service : kubectl describe service [name] <br>
- Describe pod : kubectl describe pod [name] <br>

Debugging pods <br>
- Debugging pods : kubectl logs [pod name] <br>
- Get interactive terminal of a running container : kubectl exec -it [pod name] -- bin/bash <br>

Use Configuration file for CRUD <br>
- Apply a configuration file : kubectl apply -f [file name] <br>
- Delete a configuration file : kubectl delete -f [file name] <br>

# K9s
It's a user-friendly, real-time CLI tool to interact with Kubernetes clusters. <br>

Unlike K8s, K9s is not an abbreviation following the numeronym pattern. Instead, it's a play on words: <br>
- "K9" (canine) is a reference to dogs, which are known as loyal companions.

In this case, K9s is designed to be a "companion" for Kubernetes, helping developers and operators manage K8s clusters efficiently. <br>

So, K9s is not an abbreviation but a creative naming choice, implying that it’s a faithful and useful tool for interacting with Kubernetes. <br>

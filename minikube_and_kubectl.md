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

# kubectl? (pronounced "cube control" - command line tool for kubernetes cluster)
- kubectl is the command-line tool used to interact with Kubernetes (like, a remote control for your kubernetes cluster)
- It lets you create, manage, inspect, and delete Kubernetes resources like: deployments, pods, services, configMaps, secrets etc.
- You use it to send commands to the Kubernetes API server, which is the brain of the cluster.

## kubectl commands
CRUD commands
- Create deployment : `kubectl create deployment [name]`
- Edit deployment : `kubectl edit deployment [name]`
- Delete deployment : `kubectl delete deployment [name]`

Status of different K8s components
- Get nodes: `kubectl get nodes`
- Get pod: `kubectl get pod`
- Get services: `kubectl get services`
- Get replicaset: `kubectl get replicaset`
- Get deployment: `kubectl get deployment`
- Get Ingress: `kubectl get ingress`
- Get all components (pod, service, deployment, replicaset) under a specific namespace: `kubectl get all -n [namespace]`
- Get all resources like ConfigMaps, Secrets, PersistentVolumes, etc: `kubectl get all,cm,secret,pvc -n [namespace]`

View detailed information about a specific Kubernetes resource
- Describe deployment: `kubectl describe deployment [name]`
- Describe service: `kubectl describe service [name]`
- Describe pod: `kubectl describe pod [name]`

Debugging pods
- Debugging pods: `kubectl logs [pod name]`
- Get interactive terminal of a running container: `kubectl exec -it [pod name] -- bin/bash`

Use Configuration file for CRUD
- Apply a configuration file: `kubectl apply -f [file name]`
- Delete a configuration file: `kubectl delete -f [file name]`

> Note: With kubectl commands when you don't use `-n [namespace]`, it will default to the `default` namespace.

## Install Ingress Controller in minikube
```
minikube addons enable ingress
```
It automatically starts the K8s Nginx implementation of Ingress Controller. <br>

To verify if the Ingress Controller is enabled/disabled, you can use the following command:
```
minkube addons list (and look for ingress and check if it's enabled/disabled)

kubectl get ns (and look for ingress-nginx namespace)

kubectl get pod -n ingress-nginx (and check if the pods are running)
```

# K9s
It's a user-friendly, real-time CLI tool to interact with Kubernetes clusters. <br>

Unlike K8s, K9s is not an abbreviation following the numeronym pattern. Instead, it's a play on words: <br>
- "K9" (canine) is a reference to dogs, which are known as loyal companions.

In this case, K9s is designed to be a "companion" for Kubernetes, helping developers and operators manage K8s clusters efficiently. <br>

So, K9s is not an abbreviation but a creative naming choice, implying that it’s a faithful and useful tool for interacting with Kubernetes. <br>
# Volumes: storage for containers
- By default, any files created inside a container are ephemeral (temporary). If a container crashes or restarts, its data is lost.
- Kubernetes Volumes are used to provide persistent storage to containers running inside Pods.
- Each Volume is a directory that is accessible to all containers in a Pod, and it can be backed by various storage systems (like local disk, network storage, cloud storage, etc.).
- Volume = storage that outlives container lifecycle (i.e. doesn't depend on the lifecycle of a Pod).

# Why use Volumes?
- Data Persistence: <br>
  `Without Volumes`, data created by a container is lost when the container stops or crashes.
  `With Volumes`, data can persist even if the container is deleted or restarted.
- Shared storage: <br>
  Volumes allow sharing data between multiple containers in a Pod.

# Storage Requirements
- Storage that doesn't depend on the lifecycle of a Pod.
- Storage must be available on all nodes in the cluster.
- Storage needs to survive even if cluster crashes.

# Defining a Volume in a Pod
- You define a Volume, type of volume (e.g., `emptyDir`, `hostPath`, `persistentVolumeClaim`, etc.), and its configuration in the Pod specification.
> Defined at the Pod level under .spec.volumes.

- You can then mount the Volume to one or more containers in the Pod.
> Mounted into containers via .spec.containers[*].volumeMounts.

# Common Volume Types
https://kubernetes.io/docs/concepts/storage/volumes/

- **emptyDir**: <br>
  - A temporary directory that is created when a Pod is assigned to a node and exists as long as the Pod is running.
  - Useful for scratch space or temporary data storage.
  
- **hostPath**: <br>
  - Mounts a file or directory from the host node's filesystem into the Pod.

- **persistentVolumeClaim (PVC)**: <br>
  - Mounts a PersistentVolume into a Pod, allowing data to persist beyond the Pod's lifecycle.
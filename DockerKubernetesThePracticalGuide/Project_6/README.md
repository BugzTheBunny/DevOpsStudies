# K8 Sections

### Core Components


- ## `Containers` 
    Normal (Docker) containers.
---

- ## `Pods`
    - Pods hold the actual running `App Containers` + their  `required resources` (e.g volumes) It's the smalles unit K8 interacts with.  
    - K8 creates pods, which hold containers, then K8 manages these pods, therefor the containers, *`TYPICALY THERE IS 1 CONTAINER PER POD`*  
    - Pods also can hold different resources that are being utilized / shared, such as volumes for example.
    - Pods can communiticate via the cluster, but also, by default it has a `cluster-internal IP` - **BUT** it changes when a pod is replaced.
    - *Containers inside a Pod, can communicate using `localhost`*
    - `Pods are designed to be ephemeral`: K8 will start, stop and replace them as needed.
---

- ## `Nodes`
    `Physical or virtual machine` with a certain hardware capacity which hosts `one or multiple Pods` and `communicates` with the `Cluster`
    - `Master Node` - Cluster `Control Plane`, managing the `Pods` across Worker Nodes.
    - `Worker Node` - Hosts Pods, running App Containers (+ `resources`)
---
- ## `Cluster`
     A set of `Node` machines which are running the `Containerized` Application (`Worker Nodes`) or control other Nodes (`Master Node`).
---
- ## `Services`
    - A logical set (group) of `Pods` with a unique, Pod and Container `independed IP address`.
    - A `Service` groups `Pods` together, and gives them a shared IP which provids access to them.
    - Without Services Pods are hard to access to, because of the changing IP. 


### Installation

- Install VirtualBox (Not a must). 
- Install Choco if don't have.
- Install `choco install kubernetes-cli`
- Install `choco install minikube`


### Starting
- `minikube start --driver=<driver_name>` : example - (`minikube start --driver=virtualbox`) *This will take some time*


## Project

- build - `docker build -t kub-first-app .`
- tag - `docker tag kub-first-app bugzthebunny/kub-first-app`
- start - `kubectl create deployment first-app --image=bugzthebunny/kub-first-app`
    - This command creates a Master Node (control plane)
- verify - `kubectl get deployments` || `kubectl get pods`
- dashboard - `minikube dashboard`
- exposing paths - `kubectl expose deployment first-app --type=LoadBalancer --port=8080`
- getting service path - `minikube service first-app`
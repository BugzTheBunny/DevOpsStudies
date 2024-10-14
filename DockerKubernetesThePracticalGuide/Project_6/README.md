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

- **build** - `docker build -t kub-first-app .`
- **tag** - `docker tag kub-first-app bugzthebunny/kub-first-app`
- **push image** - `docker push bugzthebunny/kub-first-app`
- **start** - `kubectl create deployment first-app --image=bugzthebunny/kub-first-app`
    - This command creates a Master Node (control plane)
- **verify** - `kubectl get deployments` || `kubectl get pods`
- **dashboard** - `minikube dashboard`
- **exposing paths** - `kubectl expose deployment first-app --type=LoadBalancer --port=8080`
- **getting service path** - `minikube service first-app` (open dashboard so you can see it in a dashboard, and it should open a window with the app)
- **scaling** - `kubectl scale deployment/first-app --replicas=<n>`
- **update deployment (after rebuild & push of new image)** - `kubectl set image deployment/first-app kub-first-app=deployment/first-app` - You will not see the change, because you first need to make a tag, so for example rebuild like in the following
- **build with tag** - `docker build -t bugzthebunny/kub-first-app:2 .`
- **push with the new tag** - `docker push bugzthebunny/kub-first-app:2`
- **update deployment with new tag** - `kubectl set image deployment/first-app kub-first-app=bugzthebunny/kub-first-app:2`
- **check deployment status** - `kubectl rollout status deployment/first-app`
- **rollback to previous deployment** - `kubectl rollout undo deployment/first-app`
- **rollout history** - `kubectl rollout history deployment/first-app`
- **rollout to specific revision** - `kubectl rollout undo deployment/first-app --to-revision=<n>`

- **apply yaml** - `kubectl apply -f <filename>.yaml`

- ## EXTRAS
- **delete deployment** - `kubectl delete -n default deployment first-app`
- **delete a service** - `kubectl delete svc first-app`
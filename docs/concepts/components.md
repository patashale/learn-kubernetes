---
description: Introduces you to various components that make up a Kubernetes cluster
---

### Introduction

A Kubernetes consists of a single or set of compute machines and is referred to as `node(s)`.

When these nodes are installed with Kubernetes and are interconnected with each other in the same isolated space, then it becomes a `cluster`. A cluster **must** have at least one node.

A node consists of two types, and they are:

- `worker node(s)` 
- `master node(s)`

??? note
    When a cluster is created with one node, it acts as both a master node and a worker node.

A Kubernetes comes with two components, and they are:

- `Control plane components` which are installed on master node(s), and
- `Data plane components` which are installed on worker node(s)

### Control Plane Components

It consists of collection processes that are responsible for the global decisions of the cluster as well as detecting and responding to cluster events.

Here are the processes that make up the control plane components and what they are responsible for:

#### kube-apiserver

- This component exposes the APIs of Kubernetes
- It is serves as the frontend for the control plane
- It is designed to scale horizontally and balance traffic between those scaled instances of the component

#### kube-scheduler

- It watches for newly created `Pods` that have not yet been assigned to a node and selects a node for it to run.
- There are several factors taken into consideration by this component, and they are:
    - Individual and collective resource requirements
    - Hardware, software or policy constraints
    - Affinity and anti-affinity configurations
    - Data locality
    - Deadlines


#### kube-controller-manager

- It runs controller processes
- There are various types of controllers and some of them are:
    -`Node` controller: Responsible for observing the nodes going down and triggering appropriate actions.
    -`Job` controller: Responsible for observing `Job` objects and creating `Pods` to run those jobs to completion.
    -`ServiceAccount` controller: Responsible for creating the default `ServiceAccount` for new namespaces.
    -`EndpointSlice` controller: Responsible for populating `EndpointSlice` objects to provide links between `Services` and `Pods`.

    
    ??? Note
        
        Each controller is a separate process; however, they are compiled into a single binary and run as a single process.

#### etcd

A highly available and consistent key-value store is used to persist the Kubernetes cluster data.

??? Tip

    If you are using `etcd` as a backup store for Kubernetes cluster data, then ensure you have a backup plan for those data.

#### cloud-controller-manager

- It is a component that allows you to link your cluster with your cloud service provider's API
- It's only available if your cluster is created by one of the cloud service provider
- It is introduced to separate interaction with the cloud platform from interaction that is specific to cluster
- There are various types of controllers, and some of them are:
    - `Node` controller: Responsible for verifying with the cloud service provider the state of the node when it is unresponsive
    - `Route` controller: Responsible for setting up routes in the underlaying cloud infrastructure
    - `Service` controller: Responsible for provisioning and de-provisioning cloud load balancers


    ??? Note
        
        Each controller is a separate process; however, they are compiled into a single binary and run as a single process.

### Data Plane Components

The data plane components run on every worker node.

#### kubelet

- It is responsible for ensuring that containers are running in `Pod`
- It does it by reading the containers described in `PodSpecs`
- It does not manage containers that are not created by Kubernetes

#### kube-proxy

- It is a network proxy responsible for implementing certain parts of the `Service` object
- It maintains the network rules on worker nodes, which allows network communication to `Pods`
- It uses the packet filtering layer of the operating system if it exists and is available to use; otherwise, it forwards the traffic by itself

#### Container Runtime

- It is responsible for managing the execution and lifecycle of containers within the Kubernetes
- There are various container runtime, and they are:
    - containerd
    - cri-o
    - Any container runtime that adheres to the `Container Runtime Interface`

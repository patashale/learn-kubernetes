
### Introduction

**Kuberenetes** is an open-source platform for the systematic deployment, scaling and management of containerized workloads.

The name **Kubernetes** originates from Greek and it translates to `Helmsman` or `Pilot` or `Captain` of a ship in English.

It is often referred to as `K8s`, where `8` stands for the number of letters between `K` and `s`.


### Features of Kubernetes

<div class="grid cards" markdown>

- __Rollouts and Rollbacks__
    
    -----

    - It rolls out changes to your workloads in a phased manner while monitoring your health to determine its readiness and liveness
    - If the change applied is unable to attain the desired state, it will roll back the changes to their previous known healthy state


- __Self Healing__
       
    -----

    It has default settings that provide abilities such as:

    - restart if containers fail
    - reschedule the workloads when node goes down
    - gracefully terminates the workloads that fail to attain the health check rule and makes them available to end users when they are ready to serve again


- __Horizontal Scaling__
   
    -----

    It allows your workloads to be scaled horizontally based on demand or on certain events that are configured by you

- __Storage Management__
   
    -----
    
    It mounts to the storage system of your choice while also taking care of their lifecycle

- __Secret & Configuration Management__
   
    -----

    It allows you to create, update and consume the secrets and configuration required for your workloads without rebuilding its image and exposing the secrets as plain text

-   __Service Discovery and Load Balancing__
   
    -----

    - It comes with an out-of-the-box service discovery mechanism to discover your workloads
    - It gives workloads their own IP addresses and a single DNS name for a set of workloads and can load balance across them

-  __Batch Execution__
   
    -----

    It allows you to execute certain jobs until the desired result is attained

-   __IPv4 & IPv6 Dual-stack__
   
    -----

    It allocates IPv4 and IPv6 addresses to workloads

-  __Customization__
   
    -----

    It is highly customizable and extensible without requiring you to submit a pull, merge or change request to the upstream source code

-   __Resource Management__
   
    -----

    It schedules the workloads based on the resource requirements and constraints configured, while increasing consumption, saving resources and also providing high availability

</div>

**KUBERNETES**

- **K8S COMPONENTS**
- **API SERVER (application program interface)**
-   API server communicates between master node and worker node via kube-proxy
-   AUTHORIZATION (WHAT THE PERSON CAN DO )
-   AUTHENTICATION (WHO CAN LOGIN INTO MY CLUSTER)
- 1POD(CONTAINER) HAS ONE CONTAINER OR MORE THAN ONE CONTAINER

- **CONTROL MANAGER**
- Controller Manager monitors the current state of your cluster through the API Server
- DESIRED STATE: 10 POD
- CURRENT STATE: 8POD

- **SCHEDULER**
- The Kubernetes scheduler is a control plane process which assigns Pods to Nodes.
- best fit node for your application
- EXAMPLE- deploy Apache on SATA

- **ETCD**
- Distributed database of k8s,which stores the complete cluster configuration and cluster state in the form of KEY AND VALUE

- CONTROL PLANE (MASTER NODE) EC2/VM (t3.medium) 4GB+2CPU
- DATA PLANE (WORKER NODE) (t3.medium) 4GB+2CPU

- **KUBE PROXY**(kube proxy is the network proxy which establish network between the worker node and the master node)

- **NAMESPACE**
- In Kubernetes (K8s), a namespace is a way to partition a single Kubernetes cluster into multiple virtual clusters. Each namespace provides a scope for names, which ensures that resources created within different namespaces do not conflict with each other
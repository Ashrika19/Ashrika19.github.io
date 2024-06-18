**KUBERNETES**
- K8S IS AN OPEN-SOURCE CONTAINER MANAGEMENT TOOL.IT IS ALSO KNOWN AS CONTAINER ORCHESTRATION TOOL.
Kubernetes, also known as k8s or kube, is an open source container orchestration platform for scheduling and automating the deployment, management and scaling of containerized applications

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
- Consider a scenario where a company has multiple departments such as development, testing, and production. Each department can be assigned its own namespace:

- development
- testing
- production
- Each department can operate independently, deploying their applications and managing resources within their namespaces without interfering with each other. Resource quotas can ensure that no single department consumes more than its share of cluster resources.

- **WHAT IS POD ?**
- A Kubernetes pod is a collection of one or more Linux containers, and is the smallest unit of a Kubernetes application

- Kubernetes Nodes are the Worker or master machines where the actual work happens. Each Kubernetes node has the services required to execute Pods and is controlled by the Control Plane. Each kubernetes Node can have multiple pods and pods have containers running inside them

"K8S INSTALLATION"

- Step-2  Kernel argument add / update 		[ Both VM ]

- vi   /etc/sysctl.d/k8s.conf		
		
- net.bridge.bridge-nf-call-ip6tables = 1
- net.bridge.bridge-nf-call-iptables = 1


- save and exit 

-	2.1  sysctl --system

-----------------------------------------------------------------------------


- Step-3  Docker installation and start the service before k8s installation [ Both VM ]

-   yum install docker -y 
   
-   systemctl start docker && systemctl enable docker

------------------------------------------------------------------------------

- Step-4  Now create repo for yum package download of K8s software (Google)   [ Both VM ]

		
- vi /etc/yum.repos.d/k8s.repo
  
- [kubernetes]
- name=Kubernetes
- baseurl=https://pkgs.k8s.io/core:/stable:/v1.28/rpm/
- enabled=1
- gpgcheck=1
- gpgkey=https://pkgs.k8s.io/core:/stable:/v1.28/rpm/repodata/repomd.xml.key
- exclude=kubelet kubeadm kubectl


- Save and exit 

----------------------------------------------------------------------------------  
  
- Step-5 Now pull k8s packages from yum / dnf 				[ Both VM ]



-	yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes


---------------------------------------------------------------------------------

- Step-6  Start kubelet service     			[ Both VM ]


- 	systemctl start kubelet ; systemctl enable kubelet ; systemctl status kubelet

----------------------------------------------------------------------------------

- Step-7  IMPORTANT step 					[ Master node ]

-	kubeadm init



- 7.1 
  
- mkdir -p $HOME/.kube
- sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
- sudo chown $(id -u):$(id -g) $HOME/.kube/config


-----------------------------------------------------------------------------------
- Follow step 7.2 for master node only

- For my master node dont copy / paste it , kindly check your own join code. 
----------------------------------------------------------------------------------

- 7.2

- kubeadm join 172.31.10.231:6443 --token h88whi.yyuw1l80ie6vq561 \
-        --discovery-token-ca-cert-hash - sha256:1a4f283b0c01c48a495b2aaaa7cad3f4272ea2c79eaf851b071f85bcac08ec6    

-----------------------------------------------------------------------------------

- 7.3 Setup Container Network Interface (CNI)    [ master node ]  

-			* calico
-			* flunnel
-			* weavenet    (This one we need setup)
			
- Weave Net, often simply called "Weave," is an open source CNI plugin that creates virtual networks for containers hosted within a Kubernetes cluster. Weave provides the virtual networking infrastructure necessary for containers to talk to each other.	

------------------------------------------------------------------------------------	
- Weavenet cni location :

- https://github.com/weaveworks/weave/blob/master/site/kubernetes/kube-addon.md


- you can run this command on MASTER NODE ONLY: 		[ master node ]  

- kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
------------------------------------------------------------------------------------

- 7.4 		(only master node)

-	kubectl get no
	
-	kubectl get po  --all-namespaces

- 7.5  Repeat step  step 7.2   (ONLY On  Worker Node(s) )

- kubeadm join 172.31.10.231:6443 --token h88whi.yyuw1l80ie6vq561 --discovery-token-ca-cert-hash sha256:1a4f283b0c01c48a495b2aaaa7cad3f4272ea2c79eaf851b071f85bcac08ec6    	

- kubectl get no

- kubectl get ns

- kubectl get po -n default

- kubectl get po -n kube-node-lease

- kubectl get po -n kube-public

- kubectl get po -n kube-system

- kubectl get po -n kube-system  -o wide

- **HOW TO CREATE THE NAMESPACE**

- kubectl create ns tgindia
- kubectl get ns

**LABEL ON NAMESPACE AND NODE**

- kubectl label ns tginida app=apache

- kubectl get ns -L app

- kubectl label ns tgindia app- (to remove the label)

- kubectl label node wn1.tg.com app=apache

- kubectl get node -L app

- kubectl label node wn1.tg.com app- (to remove the label from node)

- kubectl describe po
- kubectl describe no wn1.tg.com 

- **API Resources in k8s cluster ?**
- kubectl api-resources |less

- VI pod-test.yaml

- apiVersion: v1
- kind: Pod
- metadata:
-  name: app1
-  namespace: cdts
- spec:
- containers:
-  - name: c1
-    image: nginx
-  - name: c2
-    image: redis
-  - name: c3
-    image: manoj9923/mydocker_2024:TomcatV1

- kubectl create -f pod-test.yaml (to create the pod)

- kubectl get po -n tgindia -o wide

- kubectl delete po app1 -n tgindia (to delete the pod )

- **CREATE NAMESPACE USING .YAML FILE**

- vi ns.yaml

- apiVersion: v1
- kind: Namespace
  metadata:
    name: cdts

- kubectl create -f ns.yaml

- 
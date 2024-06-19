**REPLICA SET**

- A ReplicaSet is an essential Kubernetes resource for maintaining the desired state of pod replicas, ensuring high availability and scalability of applications. It automatically replaces failed pods and can be scaled up or down based on requirements.

- vi rstest1.yaml 

apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: rstest1
  namespace: cdts
spec:
  replicas:  4
  selector:
    matchLabels:
      app: tg1
  template:
    metadata:
     labels:
      app: tg1
    spec:
     containers:
       - name: c1
         image:  nginx
       - name: c2
         image: redis
       - name: c3
         image: cdtsbikaner/devopstg13jan2024:v1
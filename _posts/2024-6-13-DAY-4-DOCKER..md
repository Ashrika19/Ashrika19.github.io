**DOCKER**

**DOCKER IS A SOFTWARE PLATFORM THAT ALLOWS YOU TO BUILD,TEST AND DEPLOY APPLICATIONS QUICKLY**
**DOKCER IS KNOWN AS DOCKER ENGINE**

- VM1      VM2     VM3
- 4GB      4GB     4GB

-    HYPERVISOR

-    WINDOW

-     H/W


- **DOCKER IS AN ADVANCED VERSION OF VIRTUALIZATION**

-  CONTAINER
-  DOCKER ENGINE (LIKE A HYPERVISOR)
-     OS
-    H/W

- **WHAT IS HYPERVISOR?**

- HYPERVISOR IS A SOFTWARE THAT YOU CAN USE TO RUN MULTIPLE VIRTUAL MACHINES ON A SINGLE PHYSICAL MACHINE

-    VMWARE                        AWS EC2                                        DOCKER
-  VM1     VM2                 EC2          EC2                     CONTAINER1   CONTAINER2   CONTAINER3
-  OS       OS                 OS            OS                        S/W           S/W         S/W
-      ESXI (HYPERVISOR)            XEN/NITRO (HYPERVISOR)                   DOCKER ENGINE(HYPERVISOR)
-   PHYSICAL H/W                PHYSICAL H/W                                        OS         
-                                                                                 PHYSICAL H/W
- **DOCKER IS AN OPEN SOURCE CENTRALISED PLATFORM DESIGNED TO CREATE,DEPLOY,AND RUN APPLICATIONS**
- **DOCKER USES CONTAINER ON THE HOST OS TO RUN APPLICATIONS.IT ALLOWS APPLICATIONS TO USE THE SAME LINUX KERNEL AS A SYSTEM ON THE HOST COMPUTER ,RATHER THAN CREATING A WHOLE VIRTUAL OS**

- **DOCKER WRITTEN IN 'GO' LANGUAGE**

- **DOCKER IS A TOOL THAT PERFORM OS LEVEL VIRTUALIZATION ALSO KNOWN AS CONTAINERIZATION**

- **DOCKER IS A SET OF PLATFORM AS A SERVICE THAT USES OS LEVEL VIRTUALIZTION WHEREAS VMWARE USES HARDWARE LEVEL VIRTUALIZATION**

- **DOCKER IS A OS LEVEL VIRTUALIZTION .IT DOESN'T TAKE RESOURCES FROM H/W BUT IT TAKES THE FILES WHERE OS RUNS AND RUN THE CONTAINER USING THIS**

- **advantages of d0CKER**
-  No pre-allocation of ram
-  less cost
- light in weight
- it can run on physical h/w, virtual h/w, or on cloud
- we can re-use the docker image
- took very less time to create container

- **CONTAINER IS AN LAYERED FILE SYSTEM**

- **DOCKER IS AN ECOSYSTEM** (SET OF S/W OR PACKAGES)
- 1) Docker client (1 Docker users can interact with docker daemon through a client)
-                  (2 Docker client uses commands(CLI) and rest API to communicate with the docker daemon)  
-                   (3 when a clinet runs any server command on the docker client terminal ,the client terminal sends these docker commands to the docker daemon)

- 2) Docker daemon (Docker daemon runs on the host OS)
-                  (It is responsible for running container to manages docker services)
- 3) docker hub or registry (1 Docker registry manages and store the docker images)
-                           (2 There are 2 types of registriees in the docker)
-                           (PUBLIC REGISTRY AND PRIVATE REGISTRY)
-                           (PUBLIC REGISTRY - Public registry is alos called as docker hub)
-                           (PRIVATE REGISTRY- It is used to share images within the enterprise)
- 3) Docker images (Docker images are read-only templates that contain instructions for creating a container)
- 4) Docker compose (Docker compose is a tool for defining and running multi-container applications)

- **DOCKER COMMANDS**
- **redhat / centos / fedora** 
	
-	yum install docker -y

- **UBUNTU** 
- #apt-get install docker -y

- #systemctl  start docker

- #systemctl  enable  docker
	
- #systemctl status  docker

- **DOCKER HOME**
- /var/lib/docker

- #docker info 

- #docker login

- #docker pull nginx

- #docker pull mysql 

- #docker pull ubuntu:20.04

- #docker pull ubuntu

- #docker images 

- #docker rmi ubuntu 

- **#How to delete docker pulled image**
	
- 	docker rmi  <DOCKER-IMAGE-NAME>

- docker pull ubuntu  (To pull the image)

- docker images (To see the images)

- docker run --name c1 -dit <DOCKER-IMAGE-ID/NAME>  (command to create the container)

-		-d  -> deattachble mode (backgroud)
-		-i -> intractive
-		-t -> terminal 

- docker ps -a (To check the status of the container)

- Now login / test your container ?

- docker exec -ti <CONTAINER-ID/NAME>   bash 

- docker stop  <CONTAINER-ID/NAME> (To stop the container)

- docker restart <CONTAINER-ID/NAME> (To restart the container)

- docker start  <CONTAINER-ID/NAME>  (To start the container)

- docker rm  -f  <CONTAINER-ID/NAME> (To remove the container)

- docker ps -a  (To view the status of all container)

- Kill all containers (RUnnning  + Stopped + Exited)

-	docker rm -f  $(docker ps -aq)

- **how to read logs of running container ?**

-	docker logs  -f  <ContainerID/ Container-name> 

-  docker network ls

-  docker volume ls 



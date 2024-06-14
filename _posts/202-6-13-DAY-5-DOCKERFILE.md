- **DOCKERFILE**

- **APACHE TOMCAT SERVER DEPLOYMENT**

- FROM centos:7

- MAINTAINER "info@tg.com"

- RUN  yum install java-devel net-tool netstat vim bind-utils -y

- ADD  apache-tomcat-8.5.98.tar.gz /opt

- WORKDIR /opt/apache-tomcat-8.5.98/bin

- EXPOSE 8080 8081 443 8085

- CMD ["/opt/apache-tomcat-8.5.98/bin/catalina.sh","run"]

- docker build -t img1 .

- docker run --name c1 -d -p 8080:5000 img1:latest

- docker ps -a

- docker exec -it c1 bash


-  **DEPLOY WEBSERVER ON CENTOS**

- vi Dockerfile
- FROM centos:7
- MAINTAINER dahiyaashrika@gmail.com
- WORKDIR /app
- RUN yum update -y  && \
-    yum install httpd -y && \
-    yum install net-tools bind-utils vim php  -y &&\
-    httpd -v
- COPY . ./app
- COPY index.html /var/www/html/
- EXPOSE 80
- CMD ["/usr/sbin/httpd","-D","FOREGROUND"]

-  docker build -t img8 .
- docker images
- docker run --name c1 -d -p 5000:80 img1:latest


- **VOLUMES**

- docker volume create myashrika

- docker volume ls

- docker run --name c3 -dit -v myashrika:/var/lib/docker/overlay2  -P img1:latest

- docker inspect <CONTAINER-NAME>


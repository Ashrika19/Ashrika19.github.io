**Dockerfile for nginx --->  ubuntu / centon**

- webserver :  80 / 443 
	
-	1)  Static web server (HTML / CSS / JS) -->  serve services on 80 and 443 
-	2)  Reverse proxy 
-	3)  Load banalacer 

- Default location of nginx home dir for Web hosting -->  /usr/share/nginx/html

- config file -->  /etc/nginx/* 

- vi nginx.conf

- server {
-       listen 80;
-        server_name localhost;
-
-        location / {
-                root /usr/share/nginx/html;
-                index index.html;
-        }
- }

- vi index.html

- <h1> Hello World </h1>

- vi Dockerfile

- FROM rockylinux:9.3.20231
- MAINTAINER dahiyaashrika@gmail.com
- RUN yum install nginx -y
- COPY ./index.html /usr/share/nginx/html
- COPY./nginx.conf /etc/nginx/conf.d/default.conf
- COPY ./Dockerfile /root
- VOLUME /usr/share/nginx/html
- VOLUME /etc/nginx
- EXPOSE 80 443 8080
- CMD ["nginx", "-g","daemon off;"]

- docker build -t img1 .

- docker run --name c1 -d -p 5000:80 <img name> 

- docker ps -a 

- docker exec -it <container-name> bash

- podman container commit bf1e931b6b3f ashrika19/linux

- podman image push ashrika19/linux

-  podman run --name c1 -dit -v /var/lib/containers/storage/volumes/f670c142dd258981acf05f443e41d9cfab6ebd2a0158b78606c94d3567c1ca5a/_data:/etc/nginx -v /var/lib/containers/storage/volumes/c3d422e7ca182a3dd880cd738a19c5001a3d547e0a9dae6f971bcb8dfc344cb3/_data:/usr/share/nginx/html -P localhost/img1:latest

- (IF OUR CONTAINER LOST OR CRUSH BY ANY CHANCE THEN WE CAN USE THAT VOLUME TO RECREATE THE CONTAINER. BASICALLY IT IS USED FOR BACKUP)

- docker volume create harman
- docker volume ls
- docker inspect harman
- docker run --name c2 -dit -v harman:/usr/share/nginx/html -v /var/lib/containers/storage/volumes/12a87e0376a062377bf307de984f2893c4a728dd7825be42f4a367/_data:/etc/nginx -P  2f6d3cd3239f

- USING MOUNT VOLUME TYPE EXAMPLE

- #dokcer pull nginx:latest

- FIRST MAKE A DIRECTORY AND CREATE A INDEX.HTML PAGE INSIDE IT AND THEN MAP THAT DIR LOC TO THE NGINX LOC /USR/SHARE/NGINX/HTML

- #mkdir /opt/mydata

- #vi index.html

- hello its me

- #docker run --name c1 -dit --mount type=bind,src=/opt/mydata,target=/usr/share/nginx/html,readonly -P nginx:latest


- now test the container 



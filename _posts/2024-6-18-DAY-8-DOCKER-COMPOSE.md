**DOCKER-COMPOSE**
- Docker Compose is used to run multiple containers as a single service. For example, suppose you had an application which required NGNIX and MySQL, you could create one file which would start both the containers as a service without the need to start each one separately.

- vi docker-compose-wp.yaml
- services:
-    db1:
-      image: mysql:5.7
-      volumes:
-        - db_data:/var/lib/mysql
-      restart: always
-      environment:
-        - MYSQL_ROOT_PASSWORD=redhat
-        - MYSQL_DATABASE=tgindia
-        - MYSQL_USER=ekam
-        - MYSQL_PASSWORD=bikaner
-      networks:
-        - myapp_network
-    wp1:
-      depends_on:
-        - db1
-      image: wordpress:latest
-      volumes:
-        - www_data:/var/www/html
-      ports:
-        - "8080:8
-      restart: always
-      environment:
-        - WORDPRESS_DB_HOST=db1:3306
-        - WORDPRESS_DB_USER=root
-        - WORDPRESS_DB_PASSWORD=redhat
-        - WORDPRESS_DB_NAME=tgindia
-      networks:
-        - myapp_network
-volumes:
-  db_data:
-  www_data:
-networks:
-  myapp_network:

- docker compose -f docker-compose-wp.yaml up -d

- docker ps -a


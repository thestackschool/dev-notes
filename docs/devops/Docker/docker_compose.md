# Docker Compose
---

Docker compose YML file looks like:
```
version:
services:
network:
volumes:
```
> Note: `docker-compose.yml` is the default filename.


## Docker Compose Commands
---

A.  Create Containers using Docker Compose.
`$ docker-compose up -d`

B. Create Containers using Docker Compose with custom file name.
`$ docker-compose -f <filename> up -d`

C. Display Containers created by Docker Compose.
`$ docker-compose ps`

D. Display docker compose images.
`$ docker-compose images`

E. restart the containers created by docker compose.
`$ docker-compose restart`

F. Stop & remove the containers created by docker compose.
`$ docker-compose down`


## Docker compose in Linux

1. download docker compose
`$ sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
2. Allow Execution permission 
`$ sudo chmod +x /usr/local/bin/docker-compose`
3. check docker compose is installed or not
`$ docker-compose --version`

```
Example#1
version: '3'

services:
  web:
    image: nginx:latest
    ports:
      - 80:80

  db:
    image: mysql:latest
    environment:
      - MYSQL_ROOT_PASSWORD=secret
```

- Save above file with “docker-compose.yml” or any other name ex: setup.yml
```
$ docker-compose -f setup.yml -d
$ docker-compose -f setup.yml images
$ docker-compose -f setup.yml ps
$ docker exec -it ec2-user-db-1 bash  (check container name)
$ mysql -u root -p
$ exit (2 times to come out of db and container)
```


## Docker-Compose with Spring boot + MySQL
1. Install git and maven
`$ sudo yum install git maven -y`
2. Clone GitHub Repository
`$ git clone https://github.com/javabyraghu/spring-boot-mysql-docker-compose.git`
3. Build Maven application 
```
$ cd spring-boot-mysql-docker-compose
$ mvn clean package
```
4. Create Docker image
`$ docker build -t spring-boot-mysql-app .`
5. Run Docker Compose file
`$ docker-compose up -d`
6. Test Application (Open PORT 8080 on Security Group)
`http://EC2-PUBLIC-IP:8080`
7. Connect to Database container
`docker exec -it <db-container-name> /bin/bash`
8. Login to database and check table data
```
$ mysql -u root -p
$ show databases;
$ use springdb ;
$ show tables;
$ select * from book;
$ exit
$ exit 
```


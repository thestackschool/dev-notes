## Docker Installation on Linux Machine

---

`$ sudo yum update -y`

`$ sudo yum install docker -y `

`$ sudo service docker start (or) sudo systemctl start docker`

`$ sudo systemctl enable docker`

Add ec2-user to docker group by executing below command.
```
$ sudo usermod -aG docker $USER
Example:
        $ sudo usermod -aG docker ec2-user
```
Close the terminal

`$ exit`

Execution below command to see docker status.

`$ docker info`



## Basic Docker Commands
---

Display docker images available in our machine

`$ docker images`

Download docker image.
```
    $ docker pull <image-name / image-id>
    Ex: 
        $ docker pull hello-world
```

Run docker image.
```
    $ docker run <image-name / image-id>
    Ex: 
        $ docker run hello-world
```

Delete docker image.

`$ docker rmi <image-name / image-id>`

Display all running docker containers.

`$ docker ps`

Display all running and stopped containers.

`$ docker ps -a`

Delete docker container.

`$ docker rm <container-id>`

Delete docker image forcefully.

`$ docker rmi -f <image-id>`

Stop Docker container.

`$ docker stop <container-id>`

Delete all stopped containers and unused images and unused networks.

`$ docker system prune -a`


## Dockerfile
---


### FROM
 - Specifies the base image to use for the Docker image.
 - It defines the starting point of the image.
 - 	On Top of base image our image will be created.
```
Syntax: 
    FROM java:jdk-1.8
    FROM tomcat:9.5
    FROM mysql:6.8
    FROM python:3.3
```

### MANTAINER
-	`MAINTAINER` keyword is used to specify Dockerfile author information.
-	keyword has been `deprecated in recent versions` of Docker. 
-	It is no longer recommended to use the `MAINTAINER` keyword in your Dockerfile.
-	We can use the `LABEL` keyword instead.
```
    Syntax:
    MAINTAINER  Amrit <amritcsadhikari@gmail.com>
```
### RUN

### COPY (or) ADD
```
- COPY command is used to copy the files from source to destination while creating docker image

Syntax:
    COPY <source-location>  <destination-location>

Ex: 
    COPY  target/sbi-app.war   /app/tomcat/webapps/sbi-app.war
```

```
- ADD command is also used to copy files from source to destination while creating docker image.

Syntax:
ADD <source-location>  <destination-location>
ADD <url>  <destination-location>

Ex: 
    ADD  <URL>   /app/tomcat/webapps/sbi-app.war
```

### WORKDIR
```
- It is used to set working directory for an image / container.

Ex: 

WORKDIR     /app/

Note: The Dockerfile instructions which are available after WORKDIR will be processed from given working directory.
```

### ENV
```
- ENV is used to set Environment Variables

Ex:
ENV <key> <value>
ENV   java   /etc/softwares/java

```

### ARG
```
- It is used to remove hard coded values.
- Using ARG we can pass values in the BUILD TIME like below.

Ex:

ARG branch
RUN git clone -b $branch <repo-url>
# Now you Build Image using above Dockerfile
$ docker build -t imageone --build-arg branch=master
```
### USER
```
- We can set a user for creating image / container.

Note: After USER instruction all the remaining commands will execute with given user permissions
```


### EXPOSE
```
- It is used to specify our container running PORT.

Ex: 
EXPOSE 8080

Note: It is just like a documentation command to provide container running port number.
```

### CMD
```
- CMD instructions will execute while creating the container.
- We cannot use this to execute multiple Commands.
- If we define always last CMD is executed.
- Using CMD command we can run our application package file jar / war file.

Example
CMD  sudo start tomcat


Note: If we write multiple CMD instructions, also docker will process only the last CMD instruction. There is no use of writing multiple CMD instructions in one Dockerfile.
```

### ENTRYPOINT  
```
- ENTRYPOINT instructions will execute while creating container.

Syntax
    ENTRYPOINT [ "echo"  , "Hello WOrld!" ]
    ENTRYPOINT [  "java" , "-jar" , "target/boot-app.jar"]
```

### VOLUME
```
- VOLUME is used to specify docker container data storage location.

Note: Volumes are used for storage.
```

### LABEL
```
Adds metadata to the Docker image. 
It is typically used for providing information about the maintainer, version, or other identifying details
```

## Interview Questions
---
### RUN VS CMD
```
RUN is used to execute instructions while creating images.
CMD is used to execute instructions while creating Container.
```
```
We can write multiple RUN instructions in Dockerfile, docker will process all those instructions one by one.
If we write multiple CMD instructions in Dockerfile, docker will process only the last CMD instruction.
```

### COPY VS ADD
```
Using COPY command, we can just copy the files from one path to another path within the machine.
Using ADD command we can copy files from one path to another path and it supports source location as URL also.
```
```
- RUN instructions will execute while creating the image.
- Using RUN, we can give instructions to docker to execute commands.
- We can write multiple RUN instructions, and the docker will process all the RUN instructions from top to bottom.

Example
    RUN yum install maven
    RUN yum install git 
    RUN git clone repo-url
    RUN mvn clean package
```

### CMD VS ENTRYPOINT
```
We can override CMD instructions in runtime while creating container.
We can't override ENTRYPOINT instructions.
```

## Detached Mode

`$ docker run -d -p 8080:8080 sb-app`

## List Runnig Processes/ containers
`$docker ps`

## List all the Processes/ containers (running /stopped)
`$docker ps -a`

## Container Logs
`$docker logs <container-id>`



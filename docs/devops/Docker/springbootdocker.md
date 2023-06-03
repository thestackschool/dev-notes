# Spring Boot Docker Example
---

```
-	Spring Boot is an open-source java-based framework available in the market to develop applications quickly.
-	Spring Boot is providing embedded server (internal server will be available, we no need to configure server for execution)
-	Spring Boot application will be packaged as jar/war file  (mvn clean package goal will do that package)

Note:  When we do maven package, project jar will be created in project target folder
```
To run spring boot applications, we just need to run  jar file like below:

`$  java -jar <boot-app-jar-file>`

```
Dockerfile
----------

FROM openjdk:11

COPY target/spring-boot-docker-app.jar  /usr/app/

WORKDIR /usr/app/

ENTRYPOINT ["java", "-jar", "spring-boot-docker-app.jar"]
```

Spring Boot App GitHub Repository URL : https://github.com/javabyraghu/spring-boot-docker-app.git

1. Install git client software
`$ sudo yum install git -y`

2. Clone GitHub Repo
`$ git clone https://github.com/javabyraghu/spring-boot-docker-app.git`

3. Navigating to project folder
`$ cd spring-boot-docker-app`

4. Install maven software
`$ sudo yum install maven -y`

5. execute maven goals
`$ mvn clean package`
```
Note: After the package is successful, we can see project jar file in target folder.
```
 `STEP 6:` Create docker image
`$ docker build -t sb-app .`

`STEP 7:` Run docker image with port mapping
`$ docker run -p 8080:8080 sb-app`
```
Note: Enable 8080 port number in EC2 VM security group

URL To Access Application :   http://ec2-vm-public-ip:8080/welcome/Raghu
```

`STEP 8:` DETACHED MODE:
```
With the command our terminal will be blocked, we can't execute any other command.
To execute other commands, we need to type CTRL+C then the terminal will open for commands execution, but our container gets stopped.
```
`$ docker run -p 8080:8080 sb-app  `
```
Note: To overcome the above problem we can pass '-d' to run container in detached mode.
When we execute the command below it will run the container in detached mode, and it will open terminal for commands execution.
```
`$ docker run -d -p 8080:8080 sb-app  `

`STEP 9:` Once the above command is executed, we can see running containers using the command below.

`$ docker ps`

`STEP 10:` We can check logs of the container using below command.

`$ docker logs <container-id>`

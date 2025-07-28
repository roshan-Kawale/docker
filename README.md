#**Docker**
------------
Date : 2025/07/28

Tasks : 

	Get familiar with docker with documentation. Write core concept of docker you can use LLMs (Preferable if you avoid it) but write the description by your own in Readme File.
	Setup docker.
	Migrate your flask application to built using docker with dockerfile.
	Create dockercompose.yml to run your flask application .
	Mount a folder in your local to container to save the json file into that mounted path.We should be able to see json file in local .
	Call APIs from outside to docker container.

Date : 2025/07/28

### ***Task 1 : Get familiar with docker with documentation.***

#### **What is Docker?**
=> Docker is an open-source containerization platform that helps you package your application will all its dependencies into a single unit called a container. This container can run on any system that has docker installed - local computer , company server or a cloud provider like AWS , Asure etc.

#### **Core Concept of Docker**

##### **1. Docker Image.**
=> An image is a read-only template with instruction for creating a Docker Container.
Docker Image includes:
Code
Runtime
System tools
libraries
and setting needed to run your application.

##### 2. Docker Container
=> Docker Container is instance of a docker image. Container is a lighweight and portable environment where run the actual application. 

##### 3. Dockerfile
=> Dockerfile is a text file that contain a step-by-step instruction for creating a docker image. Use `docker build` to create the image from it. [more about dockerfile.](http://https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/ "more about dockerfile")

##### 4. Docker Engine
=> It is the core part of Docker — includes Docker Daemon, CLI, and REST API.

##### 5. Docker Daemon(dockerd)
=> Docker Daemon is a background service that manages a container and images. and listen docker API requests.

##### 6. Docker CLI(docker command)
=> It is a docker Command-line interface to  communicate with Docker Daemon.

##### 7. Docker Hub
=> A public registry where pull or push a docker images.

##### 8. Volumes
=> Volumes in docker used for a persistence of data means if container delete but data persist in a docker volumes.

##### 9. Networks
=> Docker Networks allow containers to communicate with each others.

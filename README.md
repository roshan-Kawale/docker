# **Docker**

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

### *Task 2 : Docker Setup.*

[Download and Install docker](https://www.docker.com/products/docker-desktop/ "Download and Install docker").

### ***Task 3 : Migrate your flask application to built using docker with dockerfile***

    FROM python:3.11-slim
    WORKDIR /app
    
    # Set Flask app environment variable
    ENV FLASK_APP=app:create_flask_app
    ENV FLASK_RUN_HOST=0.0.0.0
    ENV FLASK_RUN_PORT=5000
    
    # Install the application dependencies
    COPY requirements.txt .
    RUN pip install --no-cache-dir -r requirements.txt
    
    # Copy in the source code
    COPY . .
    EXPOSE 5000
    
    CMD ["flask" , "run"] 

### *Task 4 : Create dockercompose.yml to run your flask application*

    version: "3.8"
    
    services:
      web:
        build: .
        ports:
          - "5000:5000"
        volumes:
          - .:/app
        environment:
          FLASK_APP: app:create_flask_app
          FLASK_ENV: development
        command: flask run	

------------

Date : 2025/07/29

### *Task 5 : Mount a folder in your local to container to save the json file into that mounted path. We should be able to see json file in local*

    version: "3.8"
    
    services:
      web:
        build: .
        ports:
          - "5000:5000"
        volumes:
          - .:/app
        environment:
          FLASK_APP: app:create_flask_app
          FLASK_ENV: development
        command: flask run

In this docker-compose.yml file we have to use a volumes to mount a local root directory `(.)` with container `/app` directory.

     volumes:
          - .:/app

After this , when we have to change a code in local machine they automatically reflect in a container without run a `docker build`.

### *Task 6 : Call APIs from outside to docker container*

In Dockerfile we have to use :

    EXPOSE 5000

In docker-compose.yml we have to use:

        ports:
          - "5000:5000"

This means,
Container port 5000 is mapped to host port 5000.
We have seen a running flask app on `http://localhost:5000` in our local browser.

Using port mapping now we can Call APIs from our local machine.



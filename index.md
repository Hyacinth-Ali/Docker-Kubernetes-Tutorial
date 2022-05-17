---
layout: default
permalink: /
---

# Docker Kubernetes Hands-On Tutorial
This hands-on tutorial discusses containerization of software applications with Docker and Kubernetes. It provides a step-by-step description with sample projects for demonstrations. The sample projects can be accessed [here](https://github.com/Hyacinth-Ali/Docker-Kubernetes-Tutorial).

<!-- This [Bootstrap](http://getbootstrap.com/) plugin allows you to generate a table of contents for any page, based on the heading elements (`<h1>`, `<h2>`, etc.). It is meant to emulate the sidebar you see on [the Bootstrap v3 documentation site](https://getbootstrap.com/docs/3.3/css/). -->


## Section 1: The Basics
[Docker](https://docs.docker.com/get-started/overview/) is a famous container engine which allows users to create and manage containers. On the other hand, A container is a standardized independent unit or module of a software (Application code + Dependencies). Docker facilitates development, shipping, and running of software applications across different environments. 

### Docker Installation 
[Install Docker](https://docs.docker.com/get-docker/) by following the steps specific for your operating system.

### IDE Installation
Docker supports several IDEs. You are encouraged to use any IDE of your choice. However, for consistency, we use [Microsoft Visual Studio](https://code.visualstudio.com) throughout this tutorial.

### Download and Run Sample Project
- Clone the sample [projects](https://github.com/Hyacinth-Ali/Docker-Kubernetes-Tutorial): Navigate to the folder _getting-started-demo-app_, which contains the source code for this quick demo. Open the folder with your IDE, and you will see a very simple **Hello World** NodeJS application, as shown below. <br>

<img src="/assets/images/getting-started-node-app.png" alt="Getting Started Demo App" style="width:100%;"/>

- To run the application without docker; follow the steps below:
```
npm install
node app.js
```
> **npm install** downloads and then install all the depencies in the application <br>
> **node app.js** starts the server on port 3000.

- Open your web browser and then navigate to [http://localhost:3000](http://localhost:3000) to visualize the response of the server.

### Quick Dive into Docker and Container
Here, we containerize the application and then start the container.
- Create a file at the root project and name it _Dockerfile_
- Enter the following set of instructions in the file.

```js
FROM node:14 

WORKDIR /app

COPY package*.json /app

RUN npm install

COPY . .

EXPOSE 3000

CMD [ "node", "app.js" ]
```
- Open a terminal and then navigate to the root project.
- Build the image, i.e., create a Docker image based on the _Dockerfile_

```console
docker build -t demo-image .
```
- List existing images to see the new image (demo-image)
```
docker images
```
- Start a Docker container based on the new image
```
docker run -d -p 3000:3000 demo-image
```
- Navigate to [http://localhost:3000](http://localhost:3000) in your browser or use Docker dashboard to open the running container. Also, you can list running containers with the following command.
```
docker ps
```

## Section 2: The Main Building Blocks (Dockerfile, Image, and Container)
Here, we will walk through the steps to containerize a software application with emphasizes on the core building blocks: Dockerfile, Image, and Container.

#### Dockerfile
A Dockerfile is a configuration file, which can be used to create a Docker image. It comprises a set of instructions that when executed creates an image. Here, we provide a brief explanation of the instructions we used already to create an image with a _Dockerfile_

```js
FROM node:14 
```
1. Here we specify the base image (_node_ image, version:14). The base image provides underlying OS architecture and other packages that are required to run our application.

```js
WORKDIR /app
```
1. This instruction specifies the root directory for the image. Hence, all the contents of the image will stored in an _app_ folder.

```js
COPY package*.json /app
```
1. This instruction copies all the files with the name _package*.json_ to the root directory of image. In our example, both package.json and ackage-lock.json will be copied to oot tdirecory of the image.

```js
RUN npm install
```
This instruction installs all the dependencies that are specified in our .json file. Remember that we had to run ```npm install``` before running our application.

```js
COPY . .
```
Here, we copy all contents from the folder that contains the _Dockerfile_, i.e., the root directory of our project and it is represented as a dot. However, the _Dockerfile_ is not copied though. The second dot is the destination folder inside the image. Similarly, the dot implies that the copied contents will be stores in the root directory (or /app) of the image.

```js
EXPOSE 3000
```
This instruction simply exposes poprt 3000 so that we can reeach the application from outside the container.

```js
CMD [ "node", "app.js" ]
```
Finally, this instruction runs the containerized application.

### Image
An image contains everything required to run an application, including application code, dependencies, libraries, configuirations, and scripts. Also, an image contains other commands for running a container, e.g., ``` CMD [ "node", "app.js" ] ``` is a command to run the containerized node application. To create an image, we run the command below:
```js
docker build -t demo-image .
```
This command downloads all the required images, e.g., the node base image, if they are not yet cached locally in our system. In addition, the command executes all the instructions that are contained in _Dockerfile_ except some commands that are required to run the container, e.g., ``` CMD [ "node", "app.js" ] ```. The flag ``` -t ``` tags our image with a name (demo-image). The demo-image can then be used to refrence the image when we run containers based on the image. And finally, the ``` . ``` informs Docker to look for the _Dockerfile_ at the root directory of our project.

### Container
A container is an independent runnable instance of an image. A container is light weight, fast, portable, and platform indepenent, to name a few. We can run several containers from an image; however, they are independent and each runs in an isolation. 
```js
docker run -p 3000:3000 demo-image
```
This **docker run** command instantiates an image, i.e., it creates a new container from the **demo-image**. The ``` -p ``` exposes port 3000 (the first 3000) from port 3000 (the second 3000), which is inside the container. Remeber that we specify in the _Dockerfile_ that the application exposes port 3000. Note that both the inner port and outer port can have different values. 

### External Images
Instead of creating our own image, we can run a container based on external image. A Docker Hub is an image registory which stores repositories of images. These images can be pulled to our local and then used to start a container. An example is demonstrated below.
```js
docker run -it node
```
Remeber that ```docker run``` creates a new container based on an image. In this example, we using the _node_ image, which we do not have locally. As a result, Docker pulls the image from the Docker Hub and then create a new container based onn the image. The ```-it``` tells Docker expose an interactive shell from inside the node container to our local machine so that we can interact with the running container.

### Managing Images

1. Listing existing images <br>

1. Inspecting Images <br>

1. Removing Images <br>

### Managing Containers

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
1. Clone the sample [projects](https://github.com/Hyacinth-Ali/Docker-Kubernetes-Tutorial): Navigate to the folder _getting-started-demo-app_, which contains the source code for this quick demo. Open the folder with your IDE, and you will see a very simple **Hello World** NodeJS application, as shown below. <br>

<img src="/assets/images/getting-started-node-app.png" alt="Getting Started Demo App" style="width:100%;"/>

1. To run the application without docker; follow the steps below:
```
npm install
node app.js
```
> **npm install** downloads and then install all the depencies in the application <br>
> **node app.js** starts the server on port 3000.

1. Open your web browser and then navigate to [http://localhost:3000](http://localhost:3000) to visualize the response of the server.

### Quick Dive into Docker and Container
Here, we containerize the application and then start the container.
1. Create a file at the root project and name it _Dockerfile_
1. Enter the following set of instructions in the file.

```js
FROM node:14 

WORKDIR /app

COPY package*.json /app

RUN npm install

COPY . .

EXPOSE 3000

CMD [ "node", "app.js" ]
```
1. Open a terminal and then navigate to the root project.
1. Build the image, i.e., create a Docker image based on the _Dockerfile_

```console
docker build -t demo-image .
```
1. List existing images to see the new image (demo-image)
```
docker images
```
1. Start a Docker container based on the new image
```
docker run -d -p 3000:3000 demo-image
```
1. Navigate to [http://localhost:3000](http://localhost:3000) in your browser or use Docker dashboard to open the running container. Also, you can list running containers with the following command.
```
docker ps
```




### Section 2: Building Blocks of a Conatiner
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi.

#### Introduction to Dockerfile, Images, and Containers 
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

#### Using External Images
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

#### Creating our Own Images
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

#### Instantiating Images (Creating Containers)
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

#### Managing Images
1. Naming images <br>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

1. Listing existing images <br>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

1. Inspecting Images <br>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

1. Removing Images <br>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

#### Managing Containers
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam pretium orci eu lorem feugiat aliquet. Fusce massa erat, vehicula sed libero sed, aliquam elementum nisi. Sed vitae est sapien. In consectetur hendrerit nisl. Nulla pulvinar aliquet est maximus ultricies. Curabitur finibus elit ligula, eget hendrerit nisi auctor at. In vestibulum eros ac tristique molestie. Mauris condimentum felis eget diam malesuada luctus. Suspendisse orci justo, tincidunt quis tempor eget, finibus non turpis. Aenean et vulputate velit, vel molestie magna. Donec non elit id lacus facilisis commodo.

## Module 2 - Kubernetes
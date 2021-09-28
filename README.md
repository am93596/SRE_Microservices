# Microservices  

Microservice architecture (also known as microservices) is an approach to software development that centres on software being developed into small, single-function services that can be coupled together and are independently deployable. This means that each small service can be deployed by itself, without the need of other dependencies.  

![image](https://user-images.githubusercontent.com/88166874/135051437-200ebe32-bad2-4816-8ac5-6dc65f1d4be2.png)  

## Microservices vs Monolith Architecture  
Monolith architecture is another approach to software development, namely the creation of a complex application that contains several functions that cannot be quickly or easily extracted from each other. Microservices are simpler and more flexible than monolith architecture apps because they are small, independent services that are easy to deploy, and the code can be reusable.  

![image](https://user-images.githubusercontent.com/88166874/135051208-f5e6d218-cc54-4311-8adc-fc139ec48e85.png)  

### Containerisation with Docker  
Containerisation is the practice of putting services together into a container. This includes all of the dependencies for the application, along with configuration files that will ensure the environment for the application is set up correctly.  

Docker is a containerisation platform. It can help you create isolated, lightweight, and scalable packages that are globally available using Docker's repository platform, DockerHub.  

![image](https://user-images.githubusercontent.com/88166874/135052361-3031f400-b467-4250-a156-affb9e36dead.png)

#### Benefits of Docker  
Docker makes it easy to build, deploy, maintain, and stop your services. It uses an API to make the automation of these processes simple, and provides a number of commands that can be used to carry out activities such as building a new container, pulling an existing container from DockerHub, and running a container.  

##### Difference between Virtual Machine (VM) and Docker  
Each VM contains a separate operating system (OS) image, which significantly increases the amount of memory a VM takes up. By contrast, Docker containers sit on top of a physical server and its host OS, so the OS is shared between the containers. Not only are Docker containers lighter than virtual machines, they are much faster; VMs can take several minutes to start up, whereas Docker containers take only a few seconds.  

![image](https://user-images.githubusercontent.com/88166874/135052741-0a0e03c2-24ae-45b0-b3bb-659b8dd7d2b8.png)

###### How to Set Up Docker  
1. Follow [this link](https://docs.docker.com/desktop/windows/install/) and click `Docker Desktop for Windows`.  
2. Click on the downloaded package (in the bar along the bottom of the browser)

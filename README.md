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

### Benefits of Docker  
Docker makes it easy to build, deploy, maintain, and stop your services. It uses an API to make the automation of these processes simple, and provides a number of commands that can be used to carry out activities such as building a new container, pulling an existing container from DockerHub, and running a container.  

### Difference between Virtual Machine (VM) and Docker  
Each VM contains a separate operating system (OS) image, which significantly increases the amount of memory a VM takes up. By contrast, Docker containers sit on top of a physical server and its host OS, so the OS is shared between the containers. Not only are Docker containers lighter than virtual machines, they are much faster; VMs can take several minutes to start up, whereas Docker containers take only a few seconds.  

![image](https://user-images.githubusercontent.com/88166874/135052741-0a0e03c2-24ae-45b0-b3bb-659b8dd7d2b8.png)

### How to Set Up Docker  
1. Follow [this link](https://docs.docker.com/desktop/windows/install/) and click `Docker Desktop for Windows`.  
2. Click on the downloaded package (in the bar along the bottom of the browser) and follow the instructions of the installation wizard.  

![docker_installation_screenshot](https://user-images.githubusercontent.com/88166874/135055863-0ef533c3-65dc-48cc-9786-414e4fdb1cfd.PNG)

3. Once the installation is complete, restart your computer.  
4. Docker installation can be checked by opening a new terminal and running `docker` or `docker version`:  

![docker-command](https://user-images.githubusercontent.com/88166874/135059198-056d2ef1-e217-4a3d-bc54-3fc808b18343.PNG)  

![docker-version-command](https://user-images.githubusercontent.com/88166874/135059537-3059926c-30ca-424d-8128-9c16c7e83abd.PNG)  

5. Open Powershell as admin, and run the following command: `Enable-WindowsOptionalFeature -Online -FeatureName $("VirtualMachinePlatform","Microsoft-Windows-Subsystem-Linux")`  
6. Open Docker Desktop as admin. You may be prompted to install a kernel; follow step 4 of the page that comes up when you click on the install button.  

![docker-as-admin (2)](https://user-images.githubusercontent.com/88166874/135055610-61229232-f17c-4d87-926a-1f1648849309.PNG)  

7. Agree to the Docker service agreement, and start Docker.  
8. In Settings -> General, tick the box labelled `Start Docker Desktop when you log in`. Then in Settings -> Resources -> WSL Integration, tick the box labelled `Enable integration with my default WSL distro`.  

![docker-settings-a_LI](https://user-images.githubusercontent.com/88166874/135057075-c1073c5c-26d8-4299-9bf2-4d9bc23a4f72.jpg)  

![docker-settings-b_LI](https://user-images.githubusercontent.com/88166874/135057094-25f624e1-a250-4479-81c5-7ac1b14c31d2.jpg)  

### Set Up a DockerHub Account
Follow [this link](https://hub.docker.com/) to set up a DockerHub account, and then sign into DockerHub. Then click `Repositories` -> `Create repository`. Name your repo and save it.  

### Docker Commands
- `docker images` -> lists all the images that you have pulled or built on your local computer
- `docker pull name_of_image` -> pulls an image from DockerHub
- `docker run name_of_image` -> runs an image
- `docker build -t am93596/sre_docker_app:v1` -> builds an image
- `docker push name_of_image` -> pushes an image to DockerHub
- `docker rmi name_of_image` -> removes image from your images. can be forced with `-f` at the end of the command
- run `docker` to get the full list of commands (at the bottom of the output):  

![docker-command-list](https://user-images.githubusercontent.com/88166874/135062551-76a05c45-14bf-49d5-a07e-03fecab0c57f.PNG)  

### Naming Convention For Images
- `account_id/image_name`
- Create an example of a new image with the correct naming convention: `am93596/sre_docker_app:v1`

### Using Images From DockerHub
- Let's see an example of an image that is already available on DockerHub/registry
- Image called `ghost`
- `docker run -d -p 2368:2368 ghost` -> `-d` detached mode, `-p` port map (map the container port with your machine's port)  

![docker-run-ghost](https://user-images.githubusercontent.com/88166874/135063484-458c35ba-9e74-41b3-81c9-7461eaa80d50.PNG)  

- Run `docker images` to make sure it appears:  

![docker-images-ghost](https://user-images.githubusercontent.com/88166874/135063685-0494a560-c9e3-4463-9e6e-8f05973e5a08.PNG)

- `docker ps` or `docker ps -a` -> tells you whether the image is running
- Type `http://localhost:2368/` into the browser to see the Ghost site

#### Container Lifecycle
- Stop - Start - Remove
- `docker stop container_id` -> copy container_id from `docker ps` results
- Stopped state still holds the same data available
- `docker start container_id` to restart

![docker-stop-and-start](https://user-images.githubusercontent.com/88166874/135065150-38a5cffc-96d8-4576-990f-b3aabfad425d.PNG)  

- To remove, run `docker rm 4ce387dccd4f -f` -> doesn't need `rmi` as it is a container and not an image
- Remove deletes it completely from your computer

### Interact With Running Container
- `docker exec -it container_id` -> docker execute interactive mode
- First need to run `alias docker="winpty docker"` if you are using Windows
- Then `docker exec -it b2fba4b45b24 sh` -> shells into the container
- You can run any commands without affecting the official Ghost image

![docker-ghost-shell](https://user-images.githubusercontent.com/88166874/135066960-dd9c5639-902b-4202-b0e1-3b666f0befbd.PNG)

### DockerHub Docs
- Run `docker run -d -p 4000:4000 docs/docker.github.io`
- Then go to `http://localhost:4000/` in your browser

### Nginx
- `docker run -d -p 80:80 nginx`
- Enter `http://localhost/` into the browser
> Why not `http://localhost:80/`? The port does not need to be specified because 80 is the default port for http  
- Then run `docker exec -it container_id sh`
- `uname -a`
- `apt-get update -y`
- `apt-get upgrade -y`
- `clear`
- `ls`
- `apt-get install nano`
- `clear`
- `cd /usr/share/nginx/html`
- `nano index.html`
- Make any change you like - here's my one!

![nginx-html-pg-edit](https://user-images.githubusercontent.com/88166874/135074350-6fca3ebb-4e16-4fce-bb7b-d8f2129167f0.PNG)

![nginx-html-pg-edit-results](https://user-images.githubusercontent.com/88166874/135074372-372c82e3-f9d5-4d74-9277-e011f0c25443.PNG)

- If you remove the container using `docker rm f16003a6b851 -f`, and then re-run using `docker run -d -p 80:80 nginx`, your changes are not saved. Changes will only be saved if you commit and push them to DockerHub.

![nginx-after-remove-and-rerun](https://user-images.githubusercontent.com/88166874/135075199-a61f4fec-32f2-480e-8c16-c91cd14d7c51.PNG)

#### Instructions for running node app container
- `docker rm nginx_id -f`
- `docker run -d -p 80:3000 name_of_node_app_image:version_num`
- go to browser and open `localhost`
- Microservice architecture for Node App w/ DB: 
  - one microservice for node app
  - one microservice for database
  - then manage them using Kubernetes (K8S)

### Task
- Create container with nginx image
  - `docker run -d -p 80:80 nginx`
- Create index.html file on localhost
  - Create a new folder called `files_for_container` and put your own index.html in there
- Copy the file to default location in nginx (/usr/share/nginx/html)
  - `docker cp files_for_container/.  b8f85e280530:/usr/share/nginx/html`
- Commit changes
  - `docker commit -m "making new image from changes to nginx page" nginx_id am93596/sre_customised_nginx`
- Create a new repo on DockerHub called `my_id/sre_customised_nginx`
  - then run `docker push am93596/sre_customised_nginx`
- Remove the nginx image
  - `docker rm image_id -f`
- End goal: can run docker run command and see the app in the browser `http://localhost/`
  - `docker run -d -p 80:80 am93596/sre_customised_nginx` -> give it time!!!

![new_nginx_page](https://user-images.githubusercontent.com/88166874/135091510-880d7be3-a705-4cea-a5c4-f21fcf255ada.PNG)

# Building our own image
- `nano Dockerfile`
- contents:
```dockerfile
# BUILDING OUR OWN IMAGE

# Choose the image

# Create a container

# Copy the index.html file from host machine to container

# port 80

# CMD TO LAUNCH THE NGINX WEB SERVER
```
- Now codify our pseudocode instructions
```dockerfile
# BUILDING OUR OWN IMAGE

# Choose the image
FROM nginx

# Optional - says who made this
LABEL MAINTAINER=amurphy@spartaglobal.com
# Create a container

# Copy the index.html file from host machine to container
COPY . /usr/share/nginx/html

# port 80
EXPOSE 80

# CMD TO LAUNCH THE NGINX WEB SERVER
CMD ["nginx", "-g", "daemon off;"]
```
- Then build the image: `docker build -t am93596/sre_nginx_test:v1 .`
- Then run the image: `docker run -d -p 80:80 am93596/sre_nginx_test:v1`
- Then push: `docker push am93596/sre_nginx_test:v1`

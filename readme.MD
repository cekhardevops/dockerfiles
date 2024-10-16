# monolithic vs microservices:

Monolithic and microservices architectures are two different approaches to design and structure the applications.

when it comes to monolithic architecture,it is traditional approach where entire project is build, package as a single and indivisible unit includes (user interface, backend, data access layer interconnected each other) and the configuration required for running the application smoothly.

**characterstics:**

* Single Codebase: this means that the enitre applicaiton, including its various components and functionalities, is packaged and deployed as a single unit.
* common database: all the components uses same dabase
* Unified Deployment: Everything is deployed together, and any change requires redeploying the entire application.
* Tight Coupling: Different modules are interconnected and depend on each other within the application.

**pros:**

* entire project functionality at one place. easy to understand the design and development process.
* Monolithic applications can achieve high throughput and low latency as there is no inter-service communication overhead
* ensures data consistency with in single application.

**cons:**
* as project functionality increases, maintaining code as a single unit is quite challanging. change in part of application might effect on other part.
* specific component can't be scaled up. 
* uniform technology for entire application.
* deploying new features in a monolithic application can be complex. since entire application is deployed as single unit, any small change requires deploying entire application. there might be chance of deployment errors and downtime.
* an error in one component might bring down entire application.

**Microservice Architecuture**

in this approach, application is composed of loosely coupled, independently deployable services, each responsible for specific business function.

**pros:**
* as microservices are independently running services, it allows to scale based on load or demand
* option to choose best tech stack for particual business function. spring boot useful building service within less time where apache spark is suitable for running data intensive tasks.
* microservice promotes fault tolerance.as each microservice running independently, a failure of one service will not impact on entire echo system.

**cons:**
* requires more resources to maintain microservices based architecutre.
* quite challanging for data consistency across system.
* as each service interacts with others, there might be chance of performance issue due to network calls.   
* debugging and testing microservice based applications can be tough task.

# why docker / containerization:

***

***When a microservice architecture is chosen, the entire business functionality is designed and implemented as small, lightweight services that do not require high end servers to operate effectively.***


In the context of microservices architecture, Docker and containerization are particularly valuable because they align well with the core principles of microservices.

**isolation of services:**
* Microservices are designed to be independently deployable and manageable. Docker containers encapsulate each service along with its dependencies, ensuring it operates in isolation from other services. 

**Lightweight and Resource-Efficient**
* Microservices typically need to be lightweight to keep resource consumption minimal. Containers are less resource-intensive than virtual machines, enabling more efficient scaling and management of microservices without requiring "Bahubali" or powerful server configurations.

**Consistency Across Environments**
* Containers ensure that each microservice behaves consistently across different environments (development, testing, production), reducing the "it works on my machine" problem. This consistency is crucial in microservices, where multiple services need to interact reliably across various environments.

**Rapid Deployment and Scaling**
* Microservices benefit from the ability to quickly deploy, scale, and update individual services. Docker containers start up faster than traditional VM instances, making it easier to scale services up or down as needed in response to demand, which is ideal for high-performance microservices.

**Easy Automation with Orchestration Tools**

* In microservices, often deal with many small services. Container orchestration platforms like Kubernetes make it straightforward to manage these containers, automating deployment, scaling, and health checks. This enables microservices to operate smoothly in production with minimal manual intervention.

**Efficient Resource Utilization and Lower Costs**
* Containers enable optimal resource usage by packing multiple microservices on the same host without performance degradation. This reduces the need for high-powered servers, lowering infrastructure costs.

**physical servers vs VMs vs Containers**
* PENDING...


# docker installation on RHEL

**Set up the repository**

```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
```

**To install latest version**
```
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

**start docker**

```
sudo systemctl start docker
```
**add user to docker group to run docker command without root previledges**
```
usermod -aG <user-name> docker
```

**docker commands:**

***listed below commands are useful to pull the image from the repo and create container and run the container.***

```
docker ps (lists all running containers on that node)

docker ps -a (lists all the containers includes running and stopped)

docker images ( gives list images downloaded from the repository) 

docker pull nginx:version ( if it is vendor image) 

docker create nginx:version 

docker start container-id 

docker stop container-id 

docker rm container-id 

docker rm -f container-id( to stop forcefully and remove the container)

docker rmi image-id( to remove the image locally downloaded) 

docker run nginx ( it will pull the image from the repository if it not already exit in local repo and create the container and run the container) 

docker run -d nignx ( it runs the container in detaching mode) 

docker run -p 9090:80 nginx 

docker run -p 9091:80 nginx 

docker exec -it conatiner-id bash ( to login to container and opens the bash terminal) 

docker inspect <conatiner-id> ( gives information about container) 

docker logs <conatiner-id> ( gives the container logs) 

docker run -p 8080:80 --name docker-practice -d <conatiner-id> 
```

if nginx container is running inside the ec2 isntance, how to access the conatiner from outside the instance?
* container is like a nano server running inside the ec2 isntance. it also has (0-65535 ports) container opens 80 port on container. when user hits the request, it will reach to host port. we need to map host port with container port. using -p we can acheive this port forwarding docker run -p 80:80 nginx now, request will go through hostport to conatiner port and serve the request

**Customized docker images:**

To build a custom Docker image, Docker provides the option to create a Dockerfile.
 
Dockerfile: is used to build custom images. By using docker instructions to create custom images like FROM RUN CMD ENTRYPOINT COPY ADD ENV ARG WORKDIR USER


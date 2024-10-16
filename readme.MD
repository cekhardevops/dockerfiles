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
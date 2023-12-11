### Microservices vs Monolithic Architecture:

- Multiple smaller pieces insteas of a monolithic system.
- Monolithic Architecure:
  - Built as a sinlge unit
  - Deployed as a single unit
  - Duplicated on every server
  - Example: Web, Business, Data all together
- Microservices:
  - Segregates functionality into smaller separate services wach with a single responsibility
  - Scales by deploying each service independently
  - Lossely couples
  - Enables autonomous dev with diff languages/platforms
  - Smaller teams
  - Each microservice can have own DB

### Containers Basics:

- Unit of software/deployment
- Move faster by deploying smaller units
- uses fewer resources
- fit more into same host
- faster automation
- portable
- isolated

### VMs vs Containers:

- VMs

  - VM runs on hardware with OS installed
  - VM virtualizes the hardware
  - VM can take up a lot of ram / hard drive space and take several minutes to start
  - Large footprint, slow to boot, ideal for long running tasks though

- Containers
  - Still have hardware / OS (in the overall system not in the container)
  - Container run time installed
  - Container images are run in memory
  - Container does not have to boot, it will use host OS kernel.
  - Use less memory since there is no OS (on the container)
  - lightweight, quick to start, portable, however, ideal for short lived tasks

### Container layers:

- Base OS
- Customizations
- Application
- Each layer gets downloaded, local cache to store layers already loaded.
- Goal should be to create containers with as few layers needed.

### Container registry:

- Centralized container repo
- Kinda like GitHub for containers
- Docker Hub is offered by Docker
- Cloud providers have their own registries

### Orchestrators:

- Manage
  - Infrastructure
  - Containers
  - Deployment
  - Scaling
  - Failover
  - Health monitoring
  - App upgrades
- Popular ones: Kubernetes, Swarm, Service Fabric
- Or use as a service: Azure, AWS, GCP

### What is Docker:

- Open source container run time
- Command line tool for creating / running images
- Docker file format for building images

### Running a container:

- docker run --publish 80:80 --name webserver nginx
  - 80:80 Mpas the host port to the container listening port
  - webserver: Container local name
  - nginx: Container image in the Docker registry
- See Docker CLI for options to attach shells to containers

### Persisting Data

- Containers are ephemerous and stateless
  - Therefore, you won't store data within containers (typically)
- Non persistent data
  - You can store some data that will be scrapped at the time of the container being destroyed.
- Persistant data
  - Stored outside containers typically in a Volume (which is mapped to a folder)

### Volumes

- Mapping a volume
  - Create a volume
  - run container with volume
    - docker run -d --name devtest -v myvol:/app nginx:latest

### YAML

- YAML: YAML Ain't Markup Language
- Human friendly data serialization standard
- Used by Docker-Compose / Kubernetes

### Docker Compose Concepts

- Multi containers apps
  - Frontend. Backend, Redis Cache
- Solution: Docker Compose
  - Define using YAML files
  - Run using the docker CLI with the compose plugin
  - Compose Specs: https://compose-spec.io
- Docker Compose File:
  - 3 containers: webapi1, webapi2, apigateway
  - Good for workloads that don't require a full orchestrator
  - Development and testing
  - Use of a service that can run Docker Compose files (Azure, AWS)
## Docker Containers

- Package software  into standardized units for development,shipment and deployment.

- A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.

-  A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

- images become containers when they run on [Docker Engine](https://www.docker.com/products/container-runtime)

- Available for both Linux and Windows-based applications, containerized software will always run the same, regardless of the infrastructure.

- Docker containers are everywhere : Linux,Windows,Data center,Cloud,Serverless etc.

  

#### Docker containers that run on Docker Engine:

------



- ##### Standard: 

  Docker created the industry standard for containers, so they could be portable anywhere	

- **Lightweight:** Containers share the machine’s OS system kernel and therefore do not require an OS per application, driving higher server efficiencies and reducing server and licensing costs

- **Secure:** Applications are safer in containers and Docker provides the strongest default isolation capabilities in the industry

#### Running Docker containers:

------

- Docker container can be run using docker run command.

- Usage: docker run <image_name>:<tag> 

- Example:

  If have docker image as sample: app see below command for how to run container using this image

  docker run sample: app ---> docker container will be created with random name

- If we want to give name to container we need to use --name flag

  ```
  docker run --name sample sample:app 
  ```

- If we want to run container in detach mode we should use -d flag

  ```
  docker run --name sample -d sample:app 
  ```

#### Listing Docker containers:

------

- If we want to see all running containers we need to use  docker ps command.

- If we want to see all containers such as stopped as well as running containers we should use 

  docker ps -a command 

#### Port Mapping:

------

- Port mapping means mapping container port to the host port in order to communicate with container.

- For port mapping we should use -p flag while running container

- Usage

  ```
  docker run -p <host_port>:<container_port> <image_name>:<tag>
  ```

- Example:

  ```
  docker run --name sample -d -p 3001:3000 sample:app
  ```

  In the above example container port 3000 can be mapped to host port 3001 so we can communicate with container using 3001 port from host.

#### Docker Inspect:

------

- If we want see  information about containers we need to inspect container using docker inspect command.

- Usage:

  ```
  docker inspect <container_id>
  ```

#### Docker exec:

------

- The `docker exec` command runs a new command in a running container.

- Usage

  ```
  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
  ```

- Example:

  ```
  docker exec -d ubuntu_bash touch /tmp/execWorks
  ```

  This will create a new file `/tmp/execWorks` inside the running container `ubuntu_bash`, in the background.

  ```
  docker exec -it ubuntu_bash bash
  ```

  This will create a new Bash session in the container `ubuntu_bash`.

#### Docker logs:

------

- If we want to all the console printed logs in running container we need to use docker logs command

- The `docker logs` command batch-retrieves logs present at the time of execution.

- Usage:

  ```
  docker logs [OPTIONS] CONTAINER
  ```

- The `docker logs --follow` command will continue streaming the new output from the container’s `STDOUT` and `STDERR`

- Passing a negative number or a non-integer to `--tail` is invalid and the value is set to `all` in that case.

#### Docker start ,stop and remove container:

------



- If we want to start one or more containers we use docker start command.

- Usage:

  ```
  docker start <container_id>
  ```

- If we want to stop one or more  running container we use docker stop command.

- Usage

  ```
  docker stop <container_id>
  ```

- If we want to remove one or more container we use docker rm command

- Usage

  ```
  docker rm <container_id> 
  ```

- if we want to remove running containers first we need to stop other wise we will get errors.

For more information about docker CLI commands [click here](https://docs.docker.com/engine/reference/commandline/docker/)




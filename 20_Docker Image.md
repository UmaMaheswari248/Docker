## Docker Image

- A Docker image is a file, comprised of multiple layers, that is used to execute code in a Docker container.
- A user composes each Docker image to include system libraries, tools and other files and dependencies for the executable code.
- Docker images are also a reusable asset that can be deployed on any host.
- Most Docker images start with a base image.
- Each image has one readable/writable top layer over static layers ,layers are added to the base image.
- Each layer of a Docker image is viewable under /var/lib/docker/aufs/diff, or via the Docker history command. ex: docker history image_name : tag 
- If we create new container using docker image a writable layer is created.  this layer is called container layer. and it hosts all changes made to the running container.
- This layer can store newly written files, modifications to existing files and newly deleted files. 

#### Building Docker Images:

------

​	we can build docker images using two ways:

	1. Create from an existing container
 	2. Using Docker file

####     Create From an existing container:

​		First we need to start container with existing image and we need to do some changes and then build new image from it.

​	Steps involved in this:

 1. First we need to create container with existing image.

 2. log back into the container.

 3. Make changes to the container.

 4. Creating new image by using commit command :

    docker commit -m "Message" -a "Author Name" [containername] [imagename]

    Ex:

    I have image called simple: app

    1. First i need to create container with my existing image: 

       ​	docker run -d  --name sample simple: app  ---> docker run is used create container and -d flag is used for running container in background. --name is used for giving name to container.

    2. log back into the container:

        For this we need to know container id docker ps  command will give all running containers.

       docker exec -it [container id] bash --> this command is used for entering into the container

    3. Make changes to the container.

       Here we need to do some changes to the container i have create one file sample.txt in this container.

    4. Create new Image

       ​	In order to create new image we need to commit changes made to writable layer of container.

       docker commit -m "added file" -a "my name" sample simple: app1

       If we want to see all images in our system we use docker images command

       docker images  command will give newly created image.



#### Using Docker file:

- Docker can build images automatically by reading the instructions from a Dockerfile.
- A Docker file is a text document that contains all the commands a user could call on the command line to assemble an image.
- docker build command is used for building image from docker file.
- docker file is a file name Dockerfile with no extension.

Steps to create Image using docker file:

1. Create  Docker file.

2. use docker build -t [image name]:[tag name] . to build the image   

   Here . means it will search Dockerfile in current directory  if we have Docker file in any other directory we need use -f flag for passing file path:

   docker build -f [file path]

   #### Dockerfile creation:

   ​	If we want to run python program using docker first we need to build image.

   for that we need to create Dockerfile.

   ```
   # This is Docker file for sample.py
   FROM ubuntu:18.04
   WORKDIR /app
   COPY . /app
   RUN make /app
   CMD python /app/app.py
   ```

   Understanding Docker file:

   1. First line is comment we can write comments in docker file using # command.
   2.  The FROM sets the base image for the rest of the instructions creates a layer from the `python:3.7` Docker image.
   3. The MAINTAINER command tells who is the author of the generated images.
   4. WORKDIR is working directory inside container.
   5. COPY command is used for copy content in Docker clients current  directory into the container.
   6. RUN command is used for  execute any commands in a new layer on top of the current image and commit the results  here it build application with make. 
   7. CMD specifies what command to run within the container.
             
   
   ​    
   
   ​    
   
   ​    
   
   ​    
   
   ​    
   
   ​    
   
   ​    
   
    
   


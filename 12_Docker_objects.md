### Docker Objects:

​	In docker images,containers,networks,volumes are called objects.

#### Docker Image:

- an *image* is a read-only template with instructions for creating a Docker container.
-  an image is *based on* another image, with some additional customization.
- images are stored in configured docker registry(by default docker hub).
- images are build using docker build command.

#### Docker container:

- A container is a runnable instance of an image
-  we can create, start, stop, move, or delete a container using the Docker API or CLI.
- we can create a new image based on its current state.
- By default, a container is relatively well isolated from other containers and its host machine.
- When a container is removed, any changes to its state that are not stored in persistent storage disappear.
- container contains all application data and dependencies to run application.
- we can run docker container using docker run command.

### Docker Volume:

- A volume is a persistent data stored in `/var/lib/docker/volumes/...`
-  In order to be able to save (persist) data and also to share data between containers docker volumes will be used.
- **volumes** are directories (or files) that are outside of the default Union File System and exist as normal directories and files on the host filesystem.
- It is used to quickly allow other containers to mount said **volume**.
- If you had persisted some content in a volume, but since then deleted the container (which by default does not deleted its associated volume, unless you are using docker rm -v), you can re-attach said volume to a new container (declaring the same volume).

### Docker Network:

- ​	**Docker networking** allows you to attach a container to as many **networks** as you like. You can also attach an already running container.
- Docker network is used for communicating one container with another container.
- if one container wants to communicate with another container those two containers should be in the same network.
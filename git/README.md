## Git Docker With Ubuntu
It is possible that a user can have multiple git configurations and it is little hard to maintain all these different configurations in a single desktop system. My intention here is to create a git environment from an Ubuntu docker image. So, this docker image build from Ubuntu has git and vim installed. We can configure our own git configure inside this docker, which is totally different than the host system.

#### Prerequisite
docker/docker-compose installed and set up on an Ubuntu system.

#### This directory contains the following files.
- **Dockerfile** - Build and creates a docker image name git
- **docker-compose.yaml** - Creates a docker container from git image and runs it
- **start_git.sh** - This file alternatively runs the docker container

#### Follow the below steps
- Change these values (**<>**) in Dockerfile with appropriate values
```Dockerfile
ARG user=<username>
ARG grp=<groupname>
ARG uid=<userid in number>
ARG gid=<groupid in number>

RUN git config --global user.name "<git user name>"
RUN git config --global user.email "<git email address>"

LABEL maintainer="<maintainer name>" version="1.0"
```
- Execute this command in your terminal `docker image build -t git . -f Dockerfile`
- The previous step will create a docker image name **git**
- Now change the path you want to mount from your host directory into docker container
- You can change this (`<your project absolute path>:/practice`)  in `start_git.sh` or `docker-compose.yaml` file
- Execute `./start_git.sh` to start the docker container and log into it.

#### That’s all, now you are done setting up the new git environment.

If you want to keep your container running, you can follow the below steps

- Alternatively, you can use `docker-compose -f docker-compose.yml up -d`, to start the container.
- To attach a bash shell to this container, you can use - `docker exec -it docker_git_1 bash`




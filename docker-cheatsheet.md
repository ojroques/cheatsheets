# DOCKER cheatsheet

A list of commands for Docker.

## Contents

* [General](#general)
* [Image management](#image-management)
* [Container information](#container-information)
* [Container creation](#container-creation)
* [Container management](#container-management)
* [Saving containers](#saving-containers)


## General

List all available commands:
```sh
docker
```

View the options available to a specific command:
```sh
docker <subcommand> --help
```

View system-wide information about Docker;
```sh
docker info
```

Clean up any resources that are dangling (not associated with a container) in addition to any stopped containers and all unused images (`-a`):
```sh
docker system prune -a
```


## Image management

Search for an image:
```sh
docker search <image>
```

Download an image:
```sh
docker pull <image>
```

List all downloaded images:
```sh
docker images
```

Remove an image:
```sh
docker rmi <image>
```

## Container information

Get detailed information about a container:
```sh
docker inspect <container_id>
```


Provide the statistics of a running container:
```sh
docker stats <container_id>
```

See the top processes within a container:
```sh
docker top <container_id>
```


## Container creation

Run an image:
```sh
docker run <image>
```

Run an image (Ubuntu here) in a container named *myname* with access to an interactive (`-i`) shell (`-t`) that removes itself when stopped (`--rm`):
```sh
docker run -it --rm --name myname ubuntu
```

Run an image and map a local directory to a container directory:
```sh
docker run -v source/:dest/ <image>
```


## Container management

View all (`-a`) containers (active and inactive) with their size (`-s`):
```sh
docker ps -as
```

Start a stopped container:
```sh
docker start <container_id>
```

Stop a running container:
```sh
docker stop <container_id>
```

Remove a container:
```sh
docker rm <container_id>
```

Attach to a running container:
```sh
docker attach <container_id>
```

Detach from an interactive shell (`-it`) inside a container:
```
CTRL-p CTRL-q
```


## Saving containers

Commit changes to a new Docker image:
```sh
docker commit -m "Commit message" -a "Author name" container_id repository/new_image_name
```
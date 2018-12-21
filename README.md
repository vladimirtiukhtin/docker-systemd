Docker-systemd
--------------

A collection of enhanced Dockerfiles for various operating system images with an ability to run systemd

## Requirements
An image to be built and run requires docker - containerization platform.
Check [upstream documentation](https://docs.docker.com/install) for how to install docker on your system

## How to build
To build an image from the repository root path, replace or set a variable ${os} and run
```bash
docker build \
  --file ${os}/Dockerfile \
  --tag ${os}:systemd .
```

## How to run
To successfully start an image you must provide number of filesystems mounted/bindmounted inside a container
```bash
$ docker run \
  --detach \
  --name=${os}-systemd \
  --mount type=bind,source=/sys/fs/cgroup,target=/sys/fs/cgroup \
  --mount type=bind,source=/sys/fs/fuse,target=/sys/fs/fuse \
  --mount type=tmpfs,destination=/run \
  --mount type=tmpfs,destination=/run/lock hippolab/${os}:systemd
```

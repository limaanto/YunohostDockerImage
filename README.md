# YunoHost Docker image

This repository contains tools to build and run a YunoHost container using Docker.

With this image, you can use YunoHost like a true instance on physical server with more flexibility for system management (quick install, easier upgrade, multiple instances on the same server, can tag/backup/restore state with docker tools ...).

## Pre-requirements 

**The linux docker host must run systemd.**

## First Install

Build the image

```bash
docker build -t <your image tag>:build .
```

Run the image 

```bash
docker-compose up -d
```

Post install Yunohost (create the main user, first domain, ...)

This can be done either in the browser at `127.0.0.1` or in the CLI by entering the running container

```bash
docker compose exec yunohost bash
```

and typing

```bash
yunohost tools postinstall
```

Then follow the steps like any other yunohost install.

### Commit

To save you the post-install steps next time, you can save the container state in a new image with

```bash
docker commit yunohost yunohost:postinstalled
```

and replacing the image name in `docker-compose.yml`

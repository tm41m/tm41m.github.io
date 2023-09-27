---
layout: default
title: aethervest
nav_order: 4
parent: How to Contribute FAQ Guidelines
---

## About

Aethervest is our engine for obtaining primary sourced data. Each application contains a set of pipelines controlled
with a cron schedule. The data is relationalized and written to a postgres database that is then used by our other libraries.

## Quick Start
1. Build the Docker image with the Dockerfile or pull the latest from `tm41m/aethervest`

2. Compose the docker image with `docker-compose -f docker-compose-local.yml up -d`

3. Open a bash shell with `docker exec -it -u0 ${container_id} bash` and start testing locally

Use xvfb-run ${cmd}, this wrapper has some virtualization niceties which allows for not headless browsing.

## Bootstrapping Server

This bootstrapping technique is compatible with Docker 23.0.6 on Ubuntu 22.04.

I.e.

```
user@aethervest-dev:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:        22.04
Codename:       jammy

user@aethervest-dev:~$ docker version
Client: Docker Engine - Community
 Version:           23.0.6
 API version:       1.42
 Go version:        go1.19.9
 Git commit:        ef23cbc
 Built:             Fri May  5 21:18:13 2023
 OS/Arch:           linux/amd64
 Context:           default

Server: Docker Engine - Community
 Engine:
  Version:          23.0.6
  API version:      1.42 (minimum version 1.12)
  Go version:       go1.19.9
  Git commit:       9dbdbd4
  Built:            Fri May  5 21:18:13 2023
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.21
  GitCommit:        3dce8eb055cbb6872793272b4f20ed16117344f8
 runc:
  Version:          1.1.7
  GitCommit:        v1.1.7-0-g860f061
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

Notably, use `docker compose` over `docker-compose`.

1. Set up `~/.ssh/config` with the following config block

```
Host ${AETHERVEST_BOOTSTRAP_SERVER_IP}
  ForwardAgent yes
```

2. Ensure that your `.env.dev` file contains a environment variable `AETHERVEST_DEV_HOST`
pointing to the server you want to bootstrap.

3. Run `make bootstrap-dev-remote`

## Migrations

To run a migration against an environment, see the `Makefile` definitions requiring `scripts/migrate.sh`.
Notably, the migrations can't be run in a range to resolve state. This will have to be an addition where
some convention is enforced and parsed for files in the `migrations` directory.

## FAQs

1. I'm trying to run a migration locally against a remote database but getting the following error:

```
psql: error: connection to server at "${host}" (68.183.116.225), port 25060 failed: Connection refused
        Is the server running on that host and accepting TCP/IP connections?
```

This is because your ip must be added as a trusted source. Contact admin@ to get permissions for
running migrations.

2. Why am I getting the following error when running tests against development?

```
ModuleNotFoundError: No module named 'loblaws'
```

Make sure that in your environment, you have activated `venv`. This will be in the
working directory for `aethervest`.

Secondly, a precursor step is to `pip install .` the application(s) where you will find
`setup.py`.

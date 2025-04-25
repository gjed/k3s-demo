# k3s-demo

This repository contains a `docker-compose.yml` file for deploying a K3S cluster with Rancher web UI. The deployment is designed to be simple and straightforward, allowing for easy setup and testing of K3S and Rancher.

## Requirements

A K3S cluster deployment is requested, along with its Rancher web UI, with the following characteristics:

- The cluster must consist of 3 nodes: 1 master and 2 agents.
- The web UI must be exposed outside the containerized environment.
- There are no restrictions on the tools used (apart from Docker or Podman).
- There are no restrictions on the use of computing resources (RAM, CPU, etc.).
- There are no specific constraints on the SSL certificate (if necessary, use and configure a self-signed certificate).
- There are no restrictions on data persistence.
- Docker/Podman flags such as `--privileged` or `--network=host` are not allowed.

Everything must be presented as a working `docker-compose.yml` file (not for Swarm).

The correct execution will be tested with the following command:

```bash
docker-compose up
```

or

```bash
podman-compose up
```

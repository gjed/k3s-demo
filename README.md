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

The Rancher UI will be available at https://rancher.localhost/ 

## Implementation notes

1. The Rancher UI is accessible via HTTPS at `https://rancher.localhost`.

2. Traefik has been added as a reverse proxy to handle SSL termination and routing to the Rancher UI. The configuration uses Let's Encrypt for certificate management, with the staging ACME server for testing purposes. 

> The certificate is not valid but can be easily replaced with a valid one in production.

3. The deployment consists of three nodes:
   - One master node (`rancher`) running the Rancher server.
   - Two agent nodes (`cattle-1` and `cattle-2`) connected to the master node.

4. Data persistence local and uses named Docker volumes for each node.

5. The `--privileged` flag is required to allow the K3s agent to run correctly. It grants the container full access to system resources, such as the `/sys` filesystem and other kernel interfaces, which are essential for Kubernetes components to manage networking, storage, and node-level operations.

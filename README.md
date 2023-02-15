# sigmap-docker

Podman container for running the Sigmap backend. Should work with Docker as well.

Workflow runs once daily and pulls from main branch of [irc3-system](https://github.com/SVC-Sigmap/irc3-system)

Workflows can also be manually triggered by repo maintainers.

## Usage

### Docker

Docker install one-liner:

```
docker pull ghcr.io/svc-sigmap/sigmap-backend:latest && docker run -it --net="host" sigmap-backend
```
**Note:** Docker may need `--privileged` flag to gather WiFi data. This is not needed for Podman.

Docker start:
```
docker start -ai sigmap
```

### Podman


Podman one-liner:
```
podman pull ghcr.io/svc-sigmap/sigmap-backend:latest && podman run -it --net="host" sigmap-backend
```
Podman start:
```
podman start -ai sigmap
```

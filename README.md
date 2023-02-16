# sigmap-pod

Podman container for running the Sigmap backend. Should work with Docker as well.

Workflow runs once daily and pulls from main branch of [irc3-system](https://github.com/SVC-Sigmap/irc3-system)

Workflows can also be manually triggered by repo maintainers.

## Usage

### Podman (Linux)
Podman one-liner:
```
podman pull ghcr.io/svc-sigmap/sigmap-backend:latest && \
podman run -it --net="host" --name="sigmap" --rm sigmap-backend
```
Firebase Auth PR (Change the json directory on the host appropriately)
```
podman pull ghcr.io/svc-sigmap/sigmap-backend-firebase:latest && \
podman run -it --net="host" && \
-v $PWD/sigmap.firebase.json:/opt/irc3-system/sigmap.firebase.json:ro && \
--name="sigmap-firebase" --rm sigmap-backend-firebase
```
**Note:** Podman-compose doesn't like host networking, so the we're using the ugly solution of manually tearing down.
### Podman (Windows, MacOS):
Main
```
podman pull ghcr.io/svc-sigmap/sigmap-backend:latest && \
podman run -it -p 8080:8080 --name="sigmap" --rm sigmap-backend
```
Firebase Auth PR (Change the json directory on the host appropriately)
```
podman pull ghcr.io/svc-sigmap/sigmap-backend-firebase:latest && \
podman run -it -p 8080:8080 && \
-v $PWD/sigmap.firebase.json:/opt/irc3-system/sigmap.firebase.json:ro && \
--name="sigmap-firebase" --rm sigmap-backend-firebase
```

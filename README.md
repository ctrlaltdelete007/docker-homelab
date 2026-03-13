# Docker Homelab

Example of my Docker homelab setup using Dockhand.

## Host

Ubuntu VM with Docker

## Folder structure

### Stacks
`/mnt/docker/stacks`

### Persistent data
`/mnt/docker/data`

## Services

- Dockhand
- Immich
- Plex
- Mealie
- Calibre-Web
- Watchtower

Each service runs in its own compose stack.

## Example Dockhand stack

```yaml
services:
  dockhand:
    image: fsnys/dockhand:latest
    container_name: dockhand
    restart: unless-stopped
    ports:
      - "3000:3000"
    volumes:
      - /mnt/docker/data/dockhand:/app/data
      - /mnt/docker/stacks:/stacks
      - /var/run/docker.sock:/var/run/docker.sock
```
Notes

This repository is a sanitized example setup.
Secrets, tokens, private domains and internal details are intentionally removed.

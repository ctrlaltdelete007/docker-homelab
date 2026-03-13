# Docker Homelab

Example of my Docker homelab setup using Dockhand.

## Overview

This repository contains a simplified and sanitized example of my Docker homelab structure.

It is **not** my full production setup.
Secrets, API keys, internal domains, private network details and personal configuration have been removed.

## Host

- Ubuntu VM
- Docker / Docker Compose
- Dockhand for stack management

## Folder layout

### Compose stacks
`/mnt/docker/stacks`

### Persistent app data
`/mnt/docker/data`

### External storage / media
`/mnt/ds`

## Example structure

```text
/mnt/docker
├── data
│   ├── dockhand
│   ├── immich
│   ├── plex
│   ├── meali
│   └── acw
└── stacks
    ├── dockhand
    ├── immich
    ├── plex
    ├── meali
    ├── cwa
    └── watchtower
```
## Architecture

```text
Internet / Browser
        │
        ▼
   Dockhand UI
        │
        ▼
 Docker Host (Ubuntu VM)
        │
        ├── /mnt/docker/stacks
        │     ├── dockhand
        │     ├── immich
        │     ├── plex
        │     └── ...
        │
        ├── /mnt/docker/data
        │     ├── dockhand
        │     ├── immich
        │     ├── plex
        │     └── ...
        │
        └── /mnt/ds
              ├── photo
              ├── video
              ├── music
              └── backup_proxmox
```
## Migration from Portainer to Dockhand

This homelab originally used Portainer for container management.

Over time the setup was migrated to a file-based workflow using
Docker Compose and Dockhand.

### Why migrate

Portainer works well for managing containers, but most configuration
lives inside the UI. As the setup grew, it became harder to reproduce
the environment and track changes.

The goal was to move to a **declarative setup** where the entire
infrastructure is defined in files.

### Migration approach

The migration was done step by step:

1. Existing containers were exported from Portainer as **Docker Compose**
2. Compose files were cleaned and stored under  
   `/mnt/docker/stacks`
3. Persistent data was organized under  
   `/mnt/docker/data`
4. Containers were recreated using `docker compose`
5. Dockhand was introduced as a lightweight UI to manage stacks

### Result

- All services now run as **Compose stacks**
- Configuration is **versionable**
- The system can be rebuilt easily
- Dockhand provides a simple overview and control UI

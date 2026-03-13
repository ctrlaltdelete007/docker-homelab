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

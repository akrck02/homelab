# Homelab Documentation

> Personal homelab running self-hosted services for development, media, backups, and automation.

## Architecture Overview

┌─────────────────────────────────────────────────────-─────────┐
│                     fuyu (Local IP)                           │
│                AMD Ryzen 5 5600G · 32 GiB RAM                 │
│                                                               │
│   ┌──────────────────────────────────────────────────────┐    │
│   │               Proxmox VE  (Debian 12)                │    │
│   │                                                      │    │
│   │   ┌──────────────────────────────────────────────┐   │    │
│   │   │   CasaOS  (host UI · :81)                    │   │    │
│   │   └──────────────────────────────────────────────┘   │    │
│   │                                                      │    │
│   │   ┌──────────────────────────────────────────────┐   │    │
│   │   │   Arcane  (Docker stack mgmt · :3552)        │   │    │
│   │   │                                              │   │    │
│   │   │  [gitea] [jellyfin] [sonarr] [grafana] …     │   │    │
│   │   └──────────────────────────────────────────────┘   │    │
│   └──────────────────────────────────────────────────────┘    │
│                                                               │
│       - NVMe 500GB  /              (Proxmox OS)               │
│       - SSD  1TB    /media/services (service data)            │
│       - SSD  500GB  /media/backup   (backups)                 │
└────────────────────────────────────────────────────────────-──┘

**fuyu** is the single physical server running **Proxmox VE** on bare metal. **CasaOS** provides a host-level management UI, and **Arcane** manages all Docker Compose stacks. Service data lives on a dedicated 1 TB SSD; backups go to a separate 500 GB SSD and Google Drive.

## Docs

| File | Description |
|------|-------------|
| [hardware.md](./hardware.md) | Physical hardware specs |
| [software.md](./software.md) | All running services by category |
| [backup.md](./backup.md) | Backup schedules and routines |

## Quick Service Reference

| Service      | Port | Category   |
| ------------ | ---- | ---------- |
| CasaOS       | 81   | System     |
| Arcane       | 3552 | System     |
| Gitea        | 3002 | Dev        |
| Nextcloud    | 3333 | Cloud      |
| Jellyfin     | 8096 | Media      |
| Uptime Kuma  | 3001 | Monitoring |
| Grafana      | 3010 | Monitoring |
| Prometheus   | 9999 | Monitoring |
| AdGuard Home | 1080 | Networking |
| Syncthing    | 8384 | Backup     |
| RClone       | 5572 | Backup     |
| Seerr        | 5055 | Downloads  |
| qBittorrent  | 8080 | Downloads  |
| Sonarr       | 8989 | Downloads  |
| Radarr       | 7878 | Downloads  |
| Prowlarr     | 9696 | Downloads  |
| Bazarr       | 6767 | Downloads  |
| Dockercraft  | —    | Gaming     |

# Software & Services

All services run as Docker containers on `fuyu`, managed by **Arcane** (Docker Compose stack manager, port 3552). CasaOS (port 81) provides host-level management.

---

## System Administration

### CasaOS — `localhost:81`
Host-level dashboard. Provides a web UI to monitor system resources (CPU, RAM, disk), manage apps, and configure the server. It's the entry point for managing fuyu itself.

### Arcane — `localhost:3552`
Docker Compose stack manager. Used to deploy, configure, and manage all containerized services. Think of it as a self-hosted Portainer alternative with a Compose-centric workflow.

---

## Software Development

### Gitea — `localhost:3002`
Self-hosted Git service. Stores and manages private code repositories. Provides a GitHub-like UI with issues, pull requests, and CI hooks.

---

## Private Cloud

### Nextcloud — `localhost:3333`
Self-hosted file storage and sync (Google Drive alternative). Supports file sharing, calendar, contacts, and mobile clients.

### Jellyfin — `localhost:8096`
Media streaming server (Plex/Netflix alternative). Organizes and streams movies, TV shows, and music to any device on the network (or remotely).

---

## Backup

### Syncthing — `localhost:8384`
Peer-to-peer file synchronization between devices (phone, laptop, server). No cloud intermediary — syncs directly over LAN or the internet.

### RClone — `localhost:5572`
Offsite backup to Google Drive (and other cloud providers). The web UI allows managing sync jobs and checking backup status. Protects against local drive failure.

---

## Monitoring

### Uptime Kuma — `localhost:3001`
Service uptime monitor. Checks that each service is reachable and alerts on downtime. Acts as an internal status page.

### Prometheus — `localhost:9999`
Metrics collector. Scrapes system and container metrics at regular intervals and stores them as time-series data.

### Grafana — `localhost:3010`
Metrics visualization. Reads from Prometheus and renders dashboards for CPU, memory, network, disk, and container stats.

> **Stack**: Prometheus collects → Grafana visualizes → Uptime Kuma alerts.

---

## Networking

### AdGuard Home — `localhost:1080`
Network-wide DNS resolver and ad blocker. Acts as the local DNS server, blocking ads and trackers for all devices on the LAN.

---

## Download Automation

A full *arr* stack for automating media acquisition. The flow is:

Seerr (request) → Sonarr/Radarr (search) → Prowlarr (indexers) → qBittorrent (download) → Bazarr (subtitles)

| Service | Port | Role |
|---------|------|------|
| **Seerr** | 5055 | Request UI — users submit movie/show requests |
| **Sonarr** | 8989 | TV show automation — monitors RSS, grabs episodes |
| **Radarr** | 7878 | Movie automation — same as Sonarr but for films |
| **Prowlarr** | 9696 | Indexer manager — connects Sonarr/Radarr to torrent/NZB sources |
| **Bazarr** | 6767 | Subtitle automation — downloads subtitles for existing media |
| **qBittorrent** | 8080 | Torrent client — handles the actual downloading |

---

## Game Servers

### Dockercraft (Minecraft)
Minecraft-as-a-service container. Spins up a Minecraft server instance. Port is assigned dynamically per instance.

# Hardware

## fuyu

| Component | Details |
|-----------|---------|
| **CPU** | AMD Ryzen 5 5600G (12 threads) @ 4.46 GHz |
| **GPU** | AMD Radeon Vega Series (integrated) |
| **RAM** | 32 GiB DDR4 |
| **Swap** | 8 GiB |
| **OS** | Proxmox VE on Debian 12 (Bookworm) x86_64 |

## Storage

| Disk | Type | Size | Mount | Purpose |
|------|------|------|-------|---------|
| Crucial NVMe | NVMe SSD | 500 GB | `/` | Proxmox OS + system |
| Crucial SATA | SATA SSD | 1 TB | `/media/services` | All Docker service data |
| Kingston SATA | SATA SSD | 500 GB | `/media/backup` | Backups (Syncthing, RClone) |

## Network

| Item     | Value                                                      |
| -------- | ---------------------------------------------------------- |
| Hostname | `fuyu`                                                     |
| DNS      | AdGuard Home (port 1080) — handles LAN DNS and ad-blocking |

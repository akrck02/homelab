# Backup Schedule

The following automated routines handle data redundancy and remote syncing:

| Time (Daily) | Command / Action | Target | Description |
|---|---|---|---|
| **03:00 AM** | `rclone` | `/media/services` ➔ Google Drive | Offsite cloud mirror of service configurations |
| **04:00 AM** | `rsync` | `/media/services` ➔ `/media/backup` | Local cross-drive backup snapshot |
| **05:00 AM** | Custom Sync | GitHub ➔ Gitea | Mirrored backup of external code repositories |

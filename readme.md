# Home Server Lab

## Hardware

- Raspberry Pi 5 (4GB)
- Heatsink & Cooling Fan
- SATA Hat (5 SATA Slots)
- 2x HDD 4TB (Backup & Storage)
- 1x SSD 1TB (OS & Containers)
- Power Supply

## Software

- **OS:** Raspberry Pi OS (64-bit Lite)


## Storage Setup

- 1TB SSD (OS, Programs, Containers)
  - Filesystem: ext4

- 2x 4TB HDDs (Storage)
  - RAID1 (Mirroring) with mdadm: This remains the recommended solution for redundancy with two drives. It protects against a single drive failure. Usable storage: 4TB.
  - Filesystem: ext4.

### Backups

#### Server Data (Fileserver, Containers)

- **rsync**: Simple and effective for synchronizing data to another location.
- **borgbackup**: Deduplicated, compressed, and encrypted backups. Excellent for versioned backups of your important data.
- **Docker Volumes**: If using Docker, ensure your important container data (volumes) are mapped to persistent storage (either on your SSD or the RAID array) and included in your backup strategy.

#### Client System Backups (Laptop & PC)

- **Windows/Linux**: Duplicati, borgbackup, rsync.
- **Apple**: Time Machine can use a Samba share on your server.
- **Destination**: Your RAID1 array. You will need more storage if backing up multiple full systems over time.

#### Off-site Backup (For Critical Data)

- **External USB HDD**: Manually (or script-driven) copy vital data/backups and store off-site.
- **Cloud Storage**: rclone is fantastic for syncing data to various cloud providers (Backblaze B2, Google Drive, OneDrive, etc.)

### Virtualization & Containerization

#### Docker

- Install Docker Engine: sudo apt update && sudo apt install docker.io
- Add your user to the docker group: sudo usermod -aG docker $USER (log out and back in for this to take effect).
- Run your Minecraft server and other containerized apps here. Docker Compose simplifies multi-container setups.

#### LXC (Linux Containers)

- LXC provides more isolation than Docker but is lighter than a full VM. It's built into the Linux kernel.
- Can be useful for more isolated "virtual machines" that share the host kernel.

## Apps / Containers

- Navidrome ( Spotify )
- Stremio Selfhost / JellyFin ( Netflix )
- copyparty ( fileserver )
- Nextcloud ( google docs / humane fileserver )
- Homepage
- Portainer ( Container Manager )
- Pi-Hole?
- Watchtower ( Update Manager )
- Immichi ( Image Manager )
- Fail2Ban ( Security )
- NetData ( Monitoring )
- Duplicati? ( Backup Manager )

---
title: System info
search: true
---

# System and Hardware

<!-- TOC -->
* [System and Hardware](#system-and-hardware)
  * [OS info](#os-info)
  * [Hardware Info](#hardware-info)
    * [Disk Drive](#disk-drive)
    * [Mount points](#mount-points)
    * [Memory](#memory)
    * [CPU Info](#cpu-info)
    * [Other hardware components](#other-hardware-components)
  * [Process Information](#process-information)
  * [Network Info](#network-info)
<!-- TOC -->

## OS info

- `uname`: get system info
    - `-o`: get OS info
    - `-s`: get kernel name
    - `-r`: get kernel release
    - `-v`: get kernel version
    - `-n`: get node hostname
    - `-m`: get hardware architecture
- `lsb_release -a`: get distro info
- `hostname`: get hostname
- `hostnamectl`: get system info
- `lsmod`: list loadable kernel modules

## Hardware Info

`lshw` stands for list hardware.

- `sudo lshw -short`
- `sudo lshw -html > hardwareinfo.html`

### Disk Drive

- `lshw -c disk`:  info about storage controllers
- `lshw -c volume`: info about partitions and disk controllers
- `fdisk -l`: get partition table

### Mount points

- `lsblk`: list block devices
- `df`: "disk filesystem" - get filesystem disk usage
    - `-h`: human-readable storage numbers
- `du <path>`: "disk usage" - get disk usage of a folder
    - `-h`: human-readable storage numbers
    - `-s`: without subdirectories

### Memory

- `lshw -c memory`: info about memory hardware
- `free`: get RAM info (usage incl. swap)
    - `-h`: human-readable storage numbers
    - `--si`: Use SI prefixes (base 1000 instead of 1024)
    - `-t`: include total

### CPU Info

- `lshw -c cpu`: info about cpu
- `lscpu`: get cpu info

### Other hardware components

- `lspci`: list PCI devices
- `lsscsi`: list SCSI devices
- `lsusb`: list USB devices
- `bluetoothctl`: list Bluetooth devices
- `boltctl list -a`: list Thunderbolt devices

## Process Information

- `top`: get processes (interactive, like task manager)
    - Interactive shortcuts:
        - `k <pid> <signal>`: kill
        - `r <pid> <priority>`: renice
        - `u <user>`: only processes for user
        - `q`: quit
        - `i`: idle
        - `ESC`: manual refresh
        - `?`: help
    - Command arguments:
        - `-b -n <N>`: batch mode with iteration limit
- `htop`: get processes (more modern)
- `pgrep "<name>"`: find process PID by name
    - `-l`: display names
        - `-a`: display path
- `ps [-u <user>]`: process status
    - `-e`: every process
    - `-f`: detailed
    - `-Z`: also show SELinux context/labels
    - (typical: `-aux`; can be grepped)
- `kill [...] <PID1> [PID2...]`: send a signal to a process (default: TERM)
    - `-TERM` (15): end gracefully (let process terminate itself)
    - `-KILL` (9): kill forcefully (nuke process)
    - `-STOP` (19): stop/pause process (same as `Ctrl-Z`)
    - `-CONT` (18): resume stopped process
    - => see `man 7 signal` for more

## Network Info

- `ifconfig -a` or `io addr`: list active network interfaces
- `route` or `ip route`: display routing table
- `netstat`: display network connections, routing tables, interface statistics and more
    - `-p`: include pid and process
- `ss`: same but more TCP and state info

For more, see [networking](networking.md).

<!-- end of file -->

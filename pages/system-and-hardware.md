---
title: System info
search: true
---

# System & Hardware

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
- `ps [-u <user>]`: "process status" (typical: `-aux`)
  - `-e`: every process
  - `-f`: detailed
- `kill <PID>`: send a signal to a process (default: KILL)
  - `-<SIG>`: KILL/TERM/STOP/CONT

## Network Info

- `ifconfig -a` or `io addr`: list active network interfaces
- `route` or `ip route`: display routing table
- `netstat`: display network connections, routing tables, interface statistics and more
	- `-p`: include pid and process
- `ss`: same but more TCP and state info

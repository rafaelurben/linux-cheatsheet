---
title: System info
search: true
---

# System info

## OS info

- `uname`: get system info
  - `-o`: get OS info
  - `-s`: get kernel name
  - `-r`: get kernel release
  - `-v`: get kernel version
  - `-n`: get node hostname
  - `-m`: get hardware architecture
- `lsb_release -a`: get distro info
- `hostnamectl`: get system info

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
- `df`: get filesystem disk usage
	- `-h`: (human readable storage numbers)

### Memory

- `lshw -c memory`: info about memory hardware
- `free`: get RAM info
	- `-h`: (human readable storage numbers)
	- `-t`: (include total)


### CPU Info

- `lshw -c cpu`: info about cpu
- `lscpu`: get cpu info

## Process Information

- `top`: get processes
- `htop`: get processes (more modern)
- `pgrep "<name>"`: find process PID by name
	- `-l`: display names
	- `-a`: display path

## Network Info

- `ifconfig -a` or `io addr`: list active network interfaces
- `route` or `ip route`: display routing table
- `netstat`: display network connections, routing tables, interface statistics and more
	- `-p`: include pid and process
- `ss`: same but more TCP and state info
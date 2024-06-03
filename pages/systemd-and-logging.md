---
title: systemd
search: true
---

# systemd & logging

<!-- TOC -->
* [systemd & logging](#systemd--logging)
  * [systemd](#systemd)
    * [systemctl](#systemctl)
      * [unit files](#unit-files)
    * [loginctl](#loginctl)
    * [journalctl](#journalctl)
  * [Syslog](#syslog)
<!-- TOC -->

## systemd

`Systemd` is the most commonly used init system in Linux. It represents the first process started by the kernel.

### systemctl

`systemctl` is used to manage system services.

- `systemctl start <name>`: start the service
- `systemctl restart <name>`: restart the service
- `systemctl reload <name>`: reload the service and its config files
- `systemctl stop <name>`: stop the service
- `systemctl status <name>`: display the status of the service
- `systemctl enable <name> [--now]`: set the service to be started on boot (and start now)
- `systemctl disable <name>`: set the service to not be started on boot

Note: If a name without extension is specified, `.service` is automatically assumed.

**Units** represent a single service. **Targets** are groups of services that can be activated together:

- `systemctl get-default`: get default target
- `systemctl set-default <target>`: set default target
- `systemctl isolate <target>`: enable target

Other useful commands are:

- `systemctl list-units [--type=service|target] [--state active|inactive] [--user]`: List units
- `systemctl daemon-reload`: Reload systemd
- `systemctl cat <name.service|.target>`: View service/target file via cat
- `systemctl reboot`: same as `reboot`
- `systemctl poweroff`: same as `shutdown`

#### unit files

Example:

```service
[Unit]
Description=My New Service

[Service]
ExecStart=/bin/bash /opt/service.sh

[Install]
WantedBy=multi-user.target
```

_WantedBy_ is used to define when a unit starts. More: `man systemd.unit`

Unit files from installed software are stored in `/lib/systemd/system`. To overwrite them, create a file
in `/etc/systemd/system`.

To use a unit stored in another folder, it can be linked to `/etc/systemd/system`:

- `systemctl link <full-path>`: create a link
- `systemctl disable <path>`: disable link

After changing unit files, the following command needs to be run:

- `systemctl daemon-reload`: reload

### loginctl

`Loginctl` can be used to view sessions managed by systemd.

- `loginctl`
- `loginctl show-session`
- `loginctl show-session -p Type 2`

### journalctl

`Journalctl` can be used to view logs created with systemd.

- `journalctl -b`: show all log messages since boot.
- `journalctl -x`: add explanatory help text to log messages when available.
- `journalctl -f`: follow new messages.
- `journalctl -u <unit>`: show logs only from the specified unit.
- `journalctl --list-boots`: list boots

Note: Systemd journald stores files in a binary format which cannot be easily tampered with.

## Syslog

Syslog is older that journal but is still widely used. Logs are stored in plaintext format.

<!-- TODO -->

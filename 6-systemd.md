---
title: systemd
search: true
---

# systemd

## systemctl

- `systemctl start <name>.service`: start the service.
- `systemctl restart <name>.service`: restart the service.
- `systemctl stop <name>.service`: stop the service.
- `systemctl status <name>.service`: display the status of the service.
- `systemctl enable <name>.service`: set the service to be started on boot.
- `systemctl disable <name>.service`: set the service to not be started on boot.

Note: If no extension is specified, `.service` is automatically assumed.

### unit files

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

Unit files from installed software are stored in `/lib/systemd/system`. To overwrite them, create a file in `/etc/systemd/system`.

To use a unit stored in another folder, it can be linked to `/etc/systemd/system`:

- `systemctl link <full-path>`: create a link
- `systemctl disable <path>`: disable link

After changing unit files, the following command needs to be run:

- `systemctl daemon-reload`: reload

## journalctl

- `journalctl -b`: show all log messages since boot.
- `journalctl -x`: add explanatory help text to log messages when available.
- `journalctl -f`: follow new messages.
- `journalctl -u <unit>`: show logs only from the specified unit.

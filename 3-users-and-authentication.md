---
title: Users and authentication
search: true
---

# Users and authentication

Learn about users, groups and user authentication.

## Users

Users are stored in the `/etc/passwd` file.

- `adduser <name>`: create a user
  - `-c <comment>`
  - `--home <dir>`
  - `--no-create-home`
  - `--gid <group id>`
  - `--shell <shell>`
  - `--disabled-login`
  - `--disabled-passord`
- `adduser <name> <group>`: add user to a group
- `deluser <name>`: delete a user
- `deluser <name> <group>`: remove user from a group
- `id [user]`: get information about the current (a specific) user


### Understanding _/etc/passwd_

w.i.p

- `getent passwd <username>`: get the line in `/etc/passwd` for the specified username

## Groups

Groups are stored in the `/etc/group` file.

- `addgroup <name>`: create a group
- `delgroup <name>`: delete a group
- `usermod -a -G <groupname> <username>`: add user to group (a = append)

### Understanding _/etc/group_

w.i.p

- `getent group <groupname>`: get the line in `/etc/group` for the specified group

## Password authentication

Info about user authentication is stored in `/etc/shadow` .

### Understanding _/etc/shadow_

w.i.p

- `getent shadow <username>`: get the line in `/etc/shadow` for the specified user

#### Encryption algorithms

1. MD5
2. bcrypt
3. -
4. -
5. sha256
6. sha512

## Passwords

- `passwd -S <user>`: get user status
- `passwd -l <user>`: lock user
- `passwd -u <user>`: unlock user

## Elevated privileges

- `sudo <command>`: run command with elevated privileges
- `sudo -i`: change to root user
- `su <user>`: login as user

## SSH

- `ssh-keygen -b <bits>`: generate a new keypair with the length of b bits

Generated keys are stored in `~/.ssh/` with the names `...id_rsa` and `...id_rsa.pub` (name changes depending on options).

- `ssh-copy-id -i ~/.ssh/id_rsa <username>@<hostname>`: upload the public key to a server

Authorized keys are stored in `~/.ssh/authorized_keys`.

- `ssh <username>@<hostname> [command]`: start an ssh session (and run a command and exit)
- `ssh-keygen -f "/home/<username>/.ssh/known_hosts" -R "<hostname>"`: remove server from known_hosts file

### SSH Config

File: `~/.ssh/config`
Example content:

```conf
Host *
   ForwardX11 no

Host prod-de-1
   HostName 192.168.1.125
   User admin
   IdentityFile ~/.ssh/work_key
   Port 2222
```

---
title: Users and authentication
search: true
---

# Users and authentication

Learn about elevated privileges (sudo mode), users, groups and user authentication.

<!-- TOC -->
* [Users and authentication](#users-and-authentication)
  * [Elevated privileges & switching users](#elevated-privileges--switching-users)
  * [Users](#users)
    * [Understanding _/etc/passwd_](#understanding-_etcpasswd_)
  * [Groups](#groups)
    * [Manage group membership:](#manage-group-membership)
    * [Understanding _/etc/group_](#understanding-_etcgroup_)
  * [Password authentication](#password-authentication)
    * [Understanding _/etc/shadow_ and _/etc/gshadow_](#understanding-_etcshadow_-and-_etcgshadow_)
      * [Encryption algorithms](#encryption-algorithms)
  * [Passwords](#passwords)
  * [SSH](#ssh)
    * [SSH Config](#ssh-config)
<!-- TOC -->

## Elevated privileges & switching users

`sudo` commands are only allowed for users listed in `/etc/sudoers` (or, by default, in the `wheels` group).

- `sudo <command>`: run command with elevated privileges
- `sudo -s`: open shell as root user
- `sudo -i`: open login shell as root user (with root's environment)
- `su <user>`: substitute user / open an interactive shell as the specified user (You need to know the user's password!)
- `sudo su <user>`: same as above, but without knowing the user's password

## Users

Users are stored in the `/etc/passwd` file.

- `who`: see all currently logged in users
- `whoami`: find out who's currently logged in
- `useradd <name>`: create a user
  - `-c <comment>`
  - `--home <dir>`
  - `--no-create-home`
  - `--gid <group id>`
  - `--shell <shell>`
  - `--disabled-login`
  - `--disabled-passord`
- `userdel <name>`: delete a user
- `userdel <name> <group>`: remove user from a group
- `usermod <name>`: modify a user
- `id [user]`: get information about the current (a specific) user

The alternatives `adduser` and `deluser` have more prompts but do more or less the same.

### Understanding _/etc/passwd_

```
rafael:x:1001:1001:rafael,,,:/home/rafael:/bin/bash
[----] - [--] [--] [-------] [----------] [-------]
|      |   |    |      |          |         |
|      |   |    |      |          |         +------> 7. Login shell
|      |   |    |      |          +----------------> 6. Home directory
|      |   |    |      +---------------------------> 5. GECOS (user infos)
|      |   |    +----------------------------------> 4. GID (group id)
|      |   +---------------------------------------> 3. UID (user id)
|      +-------------------------------------------> 2. Password (nowadays "x"; password in /etc/shadow)
+--------------------------------------------------> 1. Username
```

- `getent passwd <username>`: get the line in `/etc/passwd` for the specified username

Deactivate login for user: Set login shell to `/usr/sbin/nologin setzen.`

## Groups

Groups are stored in the `/etc/group` file.

- `groups [username]`: view which groups the current (a specific) user is member of
- `groupadd <name>`: create a group
- `groupdel <name>`: delete a group

### Manage group membership:

- `usermod -aG <groupname> <username>`: add user to group (a = append)
- `gpasswd -a <user> <group>`: add user to group
- `gpasswd -d <user> <group>`: remove user from group (d = delete)

Commands available on some distros:
- `usermod -rG <groupname> <username>`: remove user from group (r = remove)
- `useradd <name> <group>`: add user to a group
- `userdel <name> <group>`: add user to a group

### Understanding _/etc/group_

```
wheel:x:10:rafael,fritz
[---] - -- [----------]
|     |  |      |
|     |  |      +------> 4. Members (comma separated)
|     |  +-------------> 3. GID (group id)
|     +----------------> 2. Password (nowadays "x"; password in /etc/gshadow)
+----------------------> 1. Group name
```

Group passwords are usually not used.

- `getent group <groupname>`: get the line in `/etc/group` for the specified group

## Password authentication

Info about user and group authentication is stored in `/etc/shadow` and `/etc/gshadow`.

Note: Group passwords are not really used anymore.

### Understanding _/etc/shadow_ and _/etc/gshadow_

- `sudo getent shadow <username>`: get the line in `/etc/shadow` for the specified user
- `sudo getent gshadow <groupname>`: get the line in `/etc/gshadow` for the specified group

#### Encryption algorithms

1. MD5
2. bcrypt
3. -
4. -
5. sha256
6. sha512

## Passwords

- `passwd [user]`: change own or user's password
- `passwd -S <user>`: get user status
- `passwd -l <user>`: lock user
- `passwd -u <user>`: unlock user
- `gpasswd`: change/manage group passwords

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

<!-- end of file -->

# Common commands 

## General
- `getent <db> <?>`

## SSH
Generated keys are stored in `~/.ssh/` with the names `...id_rsa` and `...id_rsa.pub` (name changes depending on options).

Authorized keys are stored in `~/.ssh/authorized_keys`.

- `ssh-keygen -b <bits>` generate a new keypair with the length of b bits
- `ssh-keygen -f "/home/<username>/.ssh/known_hosts" -R "<hostname>"` remove server from known_hosts file

- `ssh-copy-id -i ~/.ssh/id_rsa <username>@<hostname>` upload the public key to a server

- `ssh <username>@<hostname> [command]` start an ssh session (and run a command and exit)

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

## Environment
- `export VAR=CONTENT`
- `export VAR` 
- `export -n VAR`

- `VAR=CONTENT`

## Files & folders
### Folders (directories)
- `pwd` print working directory
- `cd <path>` change directory
- `mkdir <path>` create a directory
- `rmdir <path>` delete a directory

### Files
- `touch <path>` create a file
- `rm <path>` remove a file
- `cp <path_old> <path_new>` copy a file/dir
- `mv <path_old> <path_new>` move/rename a file/dir


## Users, groups & passwords
### Users
- `adduser <name> [group]` create a user or add a user to a group
- `deluser <name> [group]` delete a user or remove a user from a group

### Groups
- `addgroup <name>` create a group
- `delgroup <name>` delete a group

### Passwords
- `passwd -S <user>` get user status
- `passwd -l <user>` lock user
- `passwd -u <user>` unlock user

### Elevated privileges
- `sudo <command>` run command with elevated privileges
- `sudo -i` change to root user
- `su <user>` login as user

## Software management
Repos stored in `/etc/apt/sources.list`

### Install & Upgrade
- `apt-get install <name-of-package>` install/upgrade a package
- `apt-get install -f` fix broken dependencies
- `apt-get update` update local database from repos
- `apt-get upgrade` upgrade installed packages
- `apt-get dist-upgrade` upgrade installed packages but better

Manual install:
- `apt-get download <name-of-package>` download a package without installing it
- `dpkg -i <name-and-version-of-package.deb>` manually install a package

### Remove
- `apt-get remove <name-of-package>` remove a package without removing its config 
- `apt-get purge <name-of-package>` remove a package and remove its config
- `apt-get clean`
- `apt-get autoclean` clean obsolete deb packages
- `apt-get autoremove` remove obsolete packages (e. g. old dependencies)

Trick: `remove` and `purge` support a wildcard (\*) at the end!

- `apt-cache show <name-of-package>` get infos about a package from cache

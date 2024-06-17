---
title: Software management
search: true
---

# Package management

<!-- TOC -->
* [Package management](#package-management)
  * [Overview over different package managers](#overview-over-different-package-managers)
  * [apt (Advanced Package Tools)](#apt-advanced-package-tools)
    * [Install & Upgrade packages](#install--upgrade-packages)
      * [Manual install](#manual-install)
    * [Hold packages](#hold-packages)
    * [Remove packages](#remove-packages)
  * [dnf (Dandified Yum)](#dnf-dandified-yum)
<!-- TOC -->

## Overview over different package managers

Depending on the system used, there is a different package manager installed. Common ones are...

- [apt (Advanced Package Tools)](#apt-advanced-package-tools)
- yum (Yellowdog Updater, Modified)
- [dnf (Dandified Yum)](#dnf-dandified-yum)
- rpm (RedHat Package Manager)

## apt (Advanced Package Tools)

Apt ist used in Ubuntu distributions and many more.

The repos that are used as package database are stored in `/etc/apt/sources.list`.

### Install & Upgrade packages

- `apt-get install <name-of-package> [-y]`: install/upgrade a package
- `apt-get install -f`: fix broken dependencies
- `apt-get update`: update local database from repos
- `apt-get upgrade`: upgrade installed packages
- `apt-get dist-upgrade`: upgrade installed packages but better

#### Manual install

- `apt-get download <name-of-package>`: download a package without installing it
- `dpkg -i <name-and-version-of-package.deb>`: manually install a package

### Hold packages

- `apt-mark hold <name-of-package>`: exclude a package from upgrading
- `apt-mark unhold <name-of-package>`: remove the hold from a package

### Remove packages

- `apt-get remove <name-of-package>`: remove a package without removing its config
- `apt-get purge <name-of-package>`: remove a package and remove its config
- `apt-get clean`: clean obsolete deb packages
- `apt-get autoclean`: clean obsolete deb packages
- `apt-get autoremove`: remove obsolete packages (e. g. old dependencies)

Trick: `remove` and `purge` support a wildcard (\*) at the end!

- `apt-cache show <name-of-package>`: get infos about a package from cache

## dnf (Dandified Yum)

TODO

...

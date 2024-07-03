---
title: Software management
search: true
---

# Package management

<!-- TOC -->
* [Package management](#package-management)
  * [Overview over different package managers](#overview-over-different-package-managers)
  * [apt (Advanced Package Tools)](#apt-advanced-package-tools)
    * [Install & Upgrade packages (APT)](#install--upgrade-packages-apt)
      * [Manual install (APT)](#manual-install-apt)
    * [Hold packages (APT)](#hold-packages-apt)
    * [Remove packages (APT)](#remove-packages-apt)
  * [dnf (Dandified Yum)](#dnf-dandified-yum)
    * [Listing and finding packages (DNF)](#listing-and-finding-packages-dnf)
    * [Install & Upgrade packages (DNF)](#install--upgrade-packages-dnf)
    * [Remove packages (DNF)](#remove-packages-dnf)
    * [Working with repositories (DNF)](#working-with-repositories-dnf)
    * [Working with modules (DNF)](#working-with-modules-dnf)
<!-- TOC -->

## Overview over different package managers

Depending on the system used, there is a different package manager installed. Common ones are...

- [apt (Advanced Package Tools)](#apt-advanced-package-tools)
- yum (Yellowdog Updater, Modified)
- [dnf (Dandified Yum)](#dnf-dandified-yum)
- rpm (RedHat Package Manager)

There are two low-level package formats: `.rpm`, which is used by DNF/Yum and ZYpp and `.deb`, which is used by Apt.

## apt (Advanced Package Tools)

Apt ist used in Ubuntu distributions and many more.

The repos that are used as package database are stored in `/etc/apt/sources.list`.

### Install & Upgrade packages (APT)

- `apt-get install <name-of-package> [-y]`: install/upgrade a package
- `apt-get install -f`: fix broken dependencies
- `apt-get update`: update local database from repos
- `apt-get upgrade`: upgrade installed packages
- `apt-get dist-upgrade`: upgrade installed packages but better

#### Manual install (APT)

- `apt-get download <name-of-package>`: download a package without installing it
- `dpkg -i <name-and-version-of-package.deb>`: manually install a package

### Hold packages (APT)

- `apt-mark hold <name-of-package>`: exclude a package from upgrading
- `apt-mark unhold <name-of-package>`: remove the hold from a package

### Remove packages (APT)

- `apt-get remove <name-of-package>`: remove a package without removing its config
- `apt-get purge <name-of-package>`: remove a package and remove its config
- `apt-get clean`: clean obsolete deb packages
- `apt-get autoclean`: clean obsolete deb packages
- `apt-get autoremove`: remove obsolete packages (e. g. old dependencies)

Trick: `remove` and `purge` support a wildcard (\*) at the end!

- `apt-cache show <name-of-package>`: get infos about a package from cache

## dnf (Dandified Yum)

Dnf is the newer version of Yum. 

- Repos: /etc/yum.repos.d
- Config: /etc/dnf/dnf.conf
- Plugins: /etc/dnf/plugins

Dnf also includes "modules": groups of packages.

### Listing and finding packages (DNF)

- `dnf list installed`: list installed packages
- `dnf list available "abc*"`: list available packages
- `dnf search "abc*"`: find package
- `dnf provides <feature/cmd>`: find package that contains command/executable
- `def depkist <package-name>`: list dependencies of package

### Install & Upgrade packages (DNF)

- `dnf install <name-of-package>`: install package
- `dnf localinstall <file.rpm>`: manually install rpm file
- `dnf check-update`: check for updates
- `dnf update [name-of-package]`: update package / all packages

### Remove packages (DNF)

- `dnf remove <name-of-package>`: remove package
- `dnf autoremove <name-of-package>`: remove package including non-needed dependencies

### Working with repositories (DNF)

- `dnf repolist`: list installed repositories
- `dnf repoinfo`: list installed repositories with additional info
- `dnf --enablerepo <repoid>`: enable specific repo
- `dnf --disablerepo <repoid>`: disable specific repo

### Working with modules (DNF)

- `dnf module <subcommand...>`: all

(see documentation for details)

<!-- end of file -->

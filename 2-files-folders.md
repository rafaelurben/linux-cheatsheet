---
title: Files and folders
search: true
---

# Files and folders

Learn how to manage files and folders.

## Folders (directories)

### Navigation

- `pwd`: print working directory
- `cd <path>`: change directory
	- Use `../` to navigate upwards / to parent directory
	- Use `/<...>` for an absolute path (relative to root folder)
	- Use `~/<...>` for a path relative to the current user home

Always wrap path names with spaces in quotes. (e. g. `"/users/pi/my folder/ex.txt"`)

### Information

- `ls [folder]`: list the items in the currect or specified folder
- `ls -l [folder]`: same, but with details
- `ls -ld [folder]`: get infos about the current or specified folder

### Manipulation

- `mkdir <path>`: create a directory
- `rmdir <path>`: delete a directory

## Files

### Manipulation

- `touch <path>`: create an empty file
- `rm <path>`: delete a file
- `cp <path_old> <path_new>`: copy a file/dir
- `scp <username@hostname>:<path_source> <path_target>`: copy file from remote to local
- `mv <path_old> <path_new>`: move/rename a file/dir


### Editing

- `nano [+<line>] <path>`: edit (and create) a file with the nano editor
  - `Ctrl+o ENTER Ctrl+x` to save and exit
- `vi <path>`: edit (and create) a file with the vi(m) editor
  - `I` to enter insert mode
  - `Esc` to exit insert mode / enter command mode
  - `:wq` to save and exit
  - `:q!` to exit without save

### Reading

- `cat <path>`: print a file to console
- `tail <path>`: print the end of a file
	- `-n <line>`: print the last x lines
	- `-f`: follow the file for changes and print them continuously
- `b cat <path>`: print an image to console with the _butterfly launcher_ (if installed)

### Information

- `wc <file>`: get word count 
- `wc -l <file>`: get line count

### Finding

- `find / -name '*searchstring*'`: Searches the file system for a file that includes searchstring in its name.
- `find / -name '*searchstring*' -exec rm {} \;`: Searches the file system for a file that includes searchstring in its name and deletes it with the rm command. The backslash and semicolon symbolize the end of the -exec section.
- `grep searchstring /var/myfirstfile`: Searches for the pattern searchstring from the contents of /var/myfirstfile.
	- `-i`: ignore case
	- `-R`: read all files under directories recursiveley and follow symbolic links
	- `-n`: print line number

## Archives

- `tar -czvf <filename>.tar.gz /var/myfirstdirectory`: compress a directory into an archive
- `tar -xzvf <filename>.tar.gz`: extract the archive

More: `zip` and `unzip`

- `unzip [options] <file>`: unzip a file
	- `-j`: into current directory

## Permissions

There are three permission types: _`r`ead_, _`w`rite_ and _e`x`ecute_.

### File permissions

Example permissions: `-rwxrwxrwx`

The first positions stands for file (`-`) or folder (`d`). The three `rwx` triplets are for the three permission groups: (nothing or `a` stands for all of them)

1. owner `u`ser
2. owner `g`roup
3. `o`thers

#### Numeric permissions

Permissions can also be represented using the octal (base 8) system.

Each of the three `wxr` triplets (owner user, owner group, others) is represented as one octal integer.
`w` stands for 4, `x` for 2 and `r` for 1.

- Example 1: `rwxr-xr-x` = 755
- Example 2: `rwxr-x---` = 750

#### Change file permissions

File permissions can be changed via `chmod` command.

- `chmod +x`: add execute permission to all three groups
- `chmod g+w`: add write permission to the owner group
- `chmod o=r`: only allow others to read
- `chmod o-wx`: remove write and execute permissions from others
- `chmod -w`: make the file read-only

### File ownership

- `chown <username> <path>`: transfer user ownership
- `chown <username>:<group> <path>`: transfer user and group ownership
- `chown:<group> <path>`: transfer group ownership
- `chgrp <group> <path>`: transfer group ownership

### Special permissions

Files created in folders that have the setUID or setGID permission set will not belong to the creator but to the (user/group) owner of the parent folder.

`s` = with execute permission; `S` = without execute permission

- `chmod u+s`: setUID permission
- `chmod g+s`: setGID permission
- `find / -perm /4000 2>/dev/null`: find files with setUID permission
- `find / -perm /2000 2>/dev/null`: find files with setGID permission
- `find / -perm /1000 2>/dev/null`: find files with stickybit permission

### More

More on this topic: [here (external link)](https://www.redhat.com/sysadmin/suid-sgid-sticky-bit)

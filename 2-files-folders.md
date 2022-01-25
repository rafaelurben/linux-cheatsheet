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

Use `../` to navigate to parent dir.
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
- `mv <path_old> <path_new>`: move/rename a file/dir

### Editing

- `nano <path>`: edit (and create) a file with the nano editor
  - `+<num>`: open at specific line
  - `Ctrl+o ENTER Ctrl+x` to save and exit

### Reading

- `cat <path>`: print a file to console
- `tail <path>`: print the end of a file
	- `-n <line>`: print the last x lines
	- `-f`: follow the file for changes and print them continuously
- `b cat <path>`: print an image to console with the _butterfly launcher_ (if installed)

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

## Permissions

There are three permission types: _`r`ead_, _`w`rite_ and _e`x`ecute_.

### File permissions

Example permissions: `-rwxrwxrwx`

The first positions stands for file (`-`) or folder (`d`). The three `rwx` triplets are for the three permission groups: (nothing or `a` stands for all of them)

1. owner `u`ser
2. owner `g`roup
3. `o`thers

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

### Numeric permissions

Permissions can also be changed numeriacally:

w.i.p.

More on this topic: [here (external link)](https://www.redhat.com/sysadmin/suid-sgid-sticky-bit)

---
title: Basics
search: true
---

# Basics

Learn the basics.

## The prompt

The prompt will usually look something like this `username@hostname: ~$ ` or this `[username@hostname ~]$ `.
You can type commands after the prompt.

If you're in [sudo mode](users-and-authentication#elevated-privileges--switching-users), `#` will be displayed
instead of `$`. `~` is your current working directory.

### Output redirect

You can redirect the output of a command to a file or something else with appending `>PATH`.
You can redirect errors with `2>PATH`.

### Chaining commands

- `<cmd1> || <cmd2>`: only execute cmd2 if cmd1 failed
- `<cmd1> && <cmd2>`: only execute cmd2 if cmd1 was successful
- `<cmd1> ; <cmd2>`: run both commands no matter the result of the first one
- `<cmd1> | <cmd2>`: feed the results of cmd1 into cmd2 ("piping")
- `<cmd1> &`: run the command in background

### Useful shortcuts

- `Ctrl+A`: jump to start of line
- `Ctrl+E`: jump to end of line
- `Ctrl+C`: stop/abort/exit command
- `Ctrl+Z`: interrupt process
- `Ctrl+D`: exit session/terminal

## General Commands

- `exit`: end a terminal (or ssh) session
- `history`: view the command history
- `clear`: empty terminal
- `reset`: reset terminal (use when issues arise regarding weird symbols)
- `echo <args>`: print arguments to default output

### Getting help

- `<command> --help`: common argument for most commands
- `man [group] <command>`: get man pages (group is a number, e.g. 1 stands for user commands)
- `info <command>`: get info pages

### System

- `shutdown <time> "<message>"`
  * `<time>`: z. B. 22:00, +5, now
  * `-r`: reboot
  * `-F`: Dateisystem bei nächstem Neustart überprüfen
  * `-c`: cancel
  * `-p`: explizit ausschalten (in virtualisierten Systemen z. T. notwendig)
  * `-f`: force (bis zu 2x angeben)
- `halt`: same as  `shutdown now`
- `poweroff`: same as `shutdown now`
- `init 0`: same as `shutdown now`
- `reboot`: same as  `shutdown -r now`

## Variables

### Common variables

- `$SHELL`: path to the current shell
- `$HOME`: path to the current user's home directory
- `$HOSTNAME`: name of current device
- `$?` exit code of last command

### Shell variables

- `set`: print all shell vars
- `set | more`: print shell vars
- `set | grep VAR=`: get a specified shell var
- `$VAR`: use a shell var
- `echo $VAR`: print a shell var
- `VAR=CONTENT`: set a shell variable

### Environment variables

- `printenv`: print all environment vars
- `printenv VAR VAR2...`: print one or more environment vars
- `export VAR=CONTENT`: set an environment var

### Both var types

- `unset VAR`: unset a shell or environment variable
- `export VAR`: promote a shell to an environment variable
- `export -n VAR`: demote an environment to a shell variable

### Persistent env vars

To make environment variables persistent, their export statements have to be saved in files.

User-specific vars can be stored in `~/.bashrc` (accessable in non-login bash shells), `~/.bash_profile` (acessible only
by Bash) or `~/.profile` (accessible in any Bourne shell).

System-wide vars can be stored in `/etc/environment` (accessible by every shell) or `/etc/profile` and the files
in `/etc/profile.d/` (accessible by bash login shells; using files in the folder is recommended).

### More

- `export PATH="$PATH:<path-to-add>"`: add a path to PATH

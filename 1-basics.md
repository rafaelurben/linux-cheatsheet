---
title: Basics
search: true
---

# Basics

Learn the basics.

## The prompt

w.i.p

- `exit` — end a terminal (or ssh) session
- `echo <args>` — print arguments to default output
- `man <command>` — get help pages

## Output redirect

You can redirect the output of a command to a file or something else with appending `>PATH`.

You can redirect errors with `2>PATH`.

## Variables

### Shell variables

- `set` — print all shell vars
- `set | more` — print shell vars
- `set | grep VAR=` — get a specified shell var
- `$VAR` — use a shell var
- `VAR=CONTENT` — set a shell variable

### Environment variables

- `printenv` — print all environment vars
- `printenv VAR VAR2...` — print one or more environment vars
- `export VAR=CONTENT` — set an environment var

### Both var types

- `unset VAR` — unset a shell or environment variable
- `export VAR` — promote a shell to an environment variable
- `export -n VAR` — demote an environment to a shell variable

### Persistent env vars

To make environment variables persistent, their export statements have to be saved in files.

User-specific vars can be stored in `~/.bashrc` (accessable in non-login bash shells), `~/.bash_profile` (acessible only by Bash) or `~/.profile` (accessible in any Bourne shell).

System-wide vars can be stored in `/etc/environment` (accessible by every shell) or `/etc/profile` and the files in `/etc/profile.d/` (accessible by bash login shells; using files in the folder is recommended).

### More

- `export PATH="$PATH:<path-to-add>"` — add a path to PATH

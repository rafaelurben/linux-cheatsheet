---
title: tmux
search: true
---

# tmux

## terminal commands

- `tmux new-session [-s <name>]` — create a new session
  - `tmux new [-s <name>]` — alias
  - `tmux` — alias
- `tmux list-sessions` — list sessions
  - `tmux ls` — alias
- `tmux attach -t <name>` — attach to a session

## tmux commands

These command can be either run via the terminal via the `tmux` command or via the tmux command prompt. To open the tmux command prompt, press `Ctrl+b` followed by a colon `:`.

- `kill-session -t <name>` — kill a session
- `set-option [-g] <option> <state>` — change an option (-g for global)
  - `set` — alias
- `source-file ~/.tmux.conf` — reload config or load another config
- many more...

## shortcuts

All shortcuts start with `Ctrl+b` followed by the shortcut listed here.

| shortcut | action                           |
| -------- | -------------------------------- |
| d        | detach from current session      |
| :        | open tmux command prompt         |
| c        | window: create new               |
| ,        | window: rename current           |
| .        | window: move current             |
| &        | window: kill current             |
| w        | window: open tree                |
| n        | window: go to next               |
| p        | window: go to previous           |
| \[0-9\]  | window: go to window ...         |
| %        | panes: split window vertically   |
| "        | panes: split window horizontally |
| {        | panes: switch pos                |
| }        | panes: switch pos                |
| o        | panes: cycle between panes       |
| x        | panes: kill current              |

Many of these shortcuts can also be run via commands. Check the tmux docs for that.

## config

Config file: `~/.tmux.conf`

Example:

```conf
set -g mouse on
```

Short: `echo 'set -g mouse on' >> ~/.tmux.conf`

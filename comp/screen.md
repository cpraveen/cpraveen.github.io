---
layout: default
---

# GNU Screen

[Screen](https://www.gnu.org/software/screen) is a full-screen window manager that multiplexes a physical terminal between several processes, typically interactive shells.

For some configuration, see my [screenrc](https://github.com/cpraveen/cfdlab/blob/master/configs/screenrc.txt) file.

Some basic commands

```shell
screen                Start screen
screen -S <name>      Start session with some name
screen -ls            List all screen sessions
screen -r             Re-attach to running session if there is only one
screen -r <name/pid>  Re-attach
```

Screen manipulation commands

```shell
C-a d                 Detach session
C-a c                 Create new window
C-a n                 Move to next window
C-a p                 Move to previous window
C-a <num>             Move to window <num>
C-a C-a               Change to last visited active window
C-a A                 Rename current window
```

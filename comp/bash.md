---
layout: default
---

# Bash programming

## top and ps

`ps` shows running processes and is helpful to check if your code is running or not.

```shell
ps -u praveen # show processes owned by user praveen
ps -ef        # gives lot more processess
```

`top` shows the processes taking most resources and is again useful to see whats going on in your computer.

## Running programs in background

When a program prints a lot of stuff to the screen, it can slow down the code. It is always best to run it in background and direct the output to a file. For example

```shell
./a.out > log.txt &
```

If there is some error message, then you can capture them in the same file like this

```shell
./a.out > log.txt 2>&1 &
```

To ensure that the program does not get killed when you close your terminal or when you are running on a remote computer via ssh, use nohup like this

```shell
nohup ./a.out > log.txt 2>&1 &
```

## .bashrc file

Set a simple command line prompt so you dont waste space

```shell
export PS1="$ "
```

Display hostname and current path in your terminal window bar

```bash
export PROMPT_COMMAND='echo -ne "\033]0;@$HOSTNAME:${PWD/#${HOME}/\~}\007"'
```

## Conditional operators

```text
^  operator  ^  produces true if...  ^  no. of operands  ^
|  -n   | operand has non zero length                                                      |  1  |
|  -z   | operand has zero length                                                          |  1  |
|  -d   | there exists a directory whose name is operand                                   |  1  |
|  -f   | there exists a file whose name is operand                                        |  1  |
|  -eq  | the operands are integers and they are equal                                     |  2  |
|  -neq | the opposite of -eq                                                              |  2  |
|  =    | the operands are equal (as strings)                                              |  2  |
|  !=   | opposite of =                                                                    |  2  |
|  -lt  | operand1 is strictly less than operand2 (both operands should be integers)       |  2  |
|  -gt  | operand1 is strictly greater than operand2 (both operands should be integers)    |  2  |
|  -ge  | operand1 is greater than or equal to operand2 (both operands should be integers) |  2  |
|  -le  | operand1 is less than or equal to operand2 (both operands should be integers)    |  2  |
```

## For loops

A loop over integers:

```bash
for ((i=1;i<=10;i+=1)); do
echo $i
done
```

## While loops

```bash
myvar=0
while [ $myvar -le 10 ]
do
    echo $myvar
    myvar=$(( $myvar + 1 ))
done
```


## Shell keyboard shortcuts

These work on MACOSX, there could be some differences for Linux.

```text
Ctrl + a    move to begin of line
Ctrl + e    move to end of line

Ctrl + b    move back one char
Ctrl + f    move forward one char

Ctrl + k    cut until end of line
Ctrl + w    cut previous word
Ctrl + u    cut whole line

Ctrl + l    clear screen

Opt  + <    move back one word
Opt  + >    move forward one word

Ctrl + >    move to right workspace
Ctrl + <    move to left workspace

Ctrl + r    search history
Ctrl + r    repeat to search backwards in history
Ctrl + rr   last remembered search term
Ctrl + j    run current line
Ctrl + g    cancel search and restore original
```

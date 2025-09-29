---
layout: default
---

# Debian

## apt commands

Most used commands

```text
list         - list packages based on package names
search       - search in package descriptions
show         - show package details
install      - install packages
reinstall    - reinstall packages
remove       - remove packages
autoremove   - Remove automatically all unused packages
update       - update list of available packages
upgrade      - upgrade the system by installing/upgrading packages
full-upgrade - upgrade the system by removing/installing/upgrading packages
edit-sources - edit the source information file
```

To search for a package

```shell
apt-cache search gcc
```

See a description of package

```shell
apt-cache show gcc
```

Install a package

```shell
sudo apt install gcc
```

Remove a package

```shell
sudo apt remove openmpi-bin
```

To upgrade all packages to latest version

```shell
sudo apt update
sudo apt list --upgradable # check if you really want to upgrade all packages
sudo apt upgrade
```

## Setting the locale

If the locale is not set correctly, you can get weird errors while installing some softwares. Edit the file `/etc/locale.gen` with this line

```text
en_US.UTF-8 UTF-8
```

and run `sudo locale-gen` command in the terminal.

## Changing hostname

Edit `/etc/hostname` and `/etc/hosts` files. If using systemd, run

```shell
hostnamectl set-hostname HOSTNAME
```

## Install packages

I use [Spack](comp/spack.html) to install scientific packages. Before that, install some needed dependencies

```shell
sudo apt install gcc g++ gfortran gnuplot make curl wget git vim
sudo apt install build-essential
```

To get `GL/gl.h`, install

```shell
sudo apt install mesa-common-dev
```

Next see the [Spack](comp/spack.html) tips for installing other softwares. openmpi will also be installed by Spack, so do not install it from apt.

Install `locate`

```shell
sudo apt install locate
sudo updatedb
```

To get `ifconfig`

```shell
sudo apt install net-tools
export PATH=$PATH:/sbin
```

For PDF viewing

```shell
sudo apt install xpdf evince
```

`screen` or `tmux` for working remotely

```shell
sudo apt install screen tmux
```

## Enable ssh connections

```shell
systemctl start  ssh
systemctl enable ssh  # to automatically start at next boot
```

Check that sshd is started using

```shell
systemctl status sshd | grep Active
```

## Add/remove user

Add new user

```shell
sudo useradd -m -s /bin/bash <username>
```

This will create home directory usually in `/home`. You can change the location like this

```shell
sudo useradd -m -s /bin/bash -d /home2/<username> <username>
```

To delete a user account

```shell
sudo userdel -r <username>
```

`useradd` and `userdel` are usually in `/usr/sbin` which may not be in your path; then add it to your `PATH` variable.

## Give sudo privileges

To add an existing user to sudo group

```shell
sudo usermod -a -G sudo <username>
```

## Show login message when you ssh

Edit the file `/etc/profile.d/greeting.sh` and add your message

```shell
UNAME=`uname -s -n -r -m -o`
OS2=`lsb_release -s -r`
OS3=`lsb_release -s -c`
OS1=`lsb_release -s -i`
echo $UNAME $OS1 $OS2 "("$OS3")"
echo "CPU:" `cat /proc/cpuinfo | grep 'model name' | uniq | cut -d":" -f 2-`
echo
echo "----------------------IMPORTANT INFO FOR ALL USERS-----------------------"
echo " * Regularly check how much disk space you are using in your home."
echo "   \"du -sh ~\"      -->  Remove data you dont need."
echo " * Before launching MPI job, check how many jobs are already running."
echo "   Use \"top\" command to see running jobs"
echo "   Use only the number of free cores available for your job."
echo " * Regularly check if you have any old running jobs you may not need;"
echo "   \"top -U $USER\" or \"ps -u $USER\"  --> kill any that are not needed"
echo " * Do not install software in your home; first check if they are already"
echo "   installed and ask admin to install them for you. This prevents waste"
echo "   of disk space."
echo "-------------------------------------------------------------------------"
```

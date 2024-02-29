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
```

Essential compilers can also be installed like this

```shell
sudo apt install build-essential
```

Next see the [Spack](comp/spack.html) tips for installing other softwares. openmpi will also be installed by Spack, so do not install it from apt.

Install locate

```shell
sudo apt install locate
sudo updatedb
```

To get ifconfig

```shell
sudo apt install net-tools
export PATH=$PATH:/sbin
```

---
layout: default
---

# OpenSuse

The package manager is called `zypper`. Here are some useful commands

```text
zypper search gcc --  Search for string gcc
zypper info   gcc --  Show description for package gcc
zypper refresh    --  Update package description from repositories
zypper lu         --  List upgradable packages
zypper up         --  Upgrade packages
zypper dup        --  Upgrade distribution
```

We will install most softwares using Spack. But first we need to get some basic stuff from Suse

```shell
sudo zypper install gcc
sudo zypper install gcc-c++
sudo zypper install gcc-fortran
sudo zypper install gnuplot
sudo zypper install git
sudo zypper install patch
sudo zypper install vim-data       # for extended functionality
sudo zypper install mlocate && sudo updatedb
```

After this, see the [Spack](comp/spack.html) page on how to install scientific softwares. openmpi will be installed by Spack, so do not install it with zypper.

To get common python modules (better to install Python using Conda or Spack in order to get latest version)

```shell
sudo zypper install python3-numpy python3-sympy python3-scipy python3-matplotlib
```

To install intel compilers, see [here](https://en.opensuse.org/SDB:Install_oneAPI) and do

```shell
sudo zypper install intel-basekit intel-hpckit
```

To delete all of texlive

```shell
sudo -E zypper rm texlive-*
```

List files installed by a package

```shell
rpm -ql PACKAGENAME
```

## Stop firewall

```shell
systemctl -q is-enabled SuSEfirewall2 && systemctl disable SuSEfirewall2
systemctl -q is-active SuSEfirewall2 && systemctl stop SuSEfirewall2
```

## Enable ssh connections

```shell
systemctl start  sshd
systemctl enable sshd  # to automatically start at next boot
```

Check that sshd is started using

```shell
systemctl status sshd | grep Active
```

You may also have to enable ssh connections by going into Yast - Firewall - public and enable ssh.

## gcc alternatives

Opensuse Leap 15.2 has gcc7 as default. We can install newer gcc versions

```shell
export VER=13
sudo zypper install gcc$VER gcc$VER-c++ gcc$VER-fortran
```

Now create links to this version

```shell
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-$VER $VER
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-$VER $VER
sudo update-alternatives --install /usr/bin/gfortran gfortran /usr/bin/gfortran-$VER $VER
```

Check available versions; this will show list if there is more than one version available.

```shell
sudo update-alternatives --config gcc
sudo update-alternatives --config g++
sudo update-alternatives --config gfortran
```

## Setting locale

If you get this error upon login

```shell
/usr/bin/manpath: can't set the locale; make sure $LC_* and $LANG are correct
```

then add following to `/etc/environment`

```text
LC_ALL=en_US.UTF-8
```

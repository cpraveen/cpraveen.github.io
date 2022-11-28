---
layout: default
---

# Computers at TIFR-CAM

We have two good workstations running Linux in our Centre which are listed below. They are located inside the server room and access is by ssh. Most of the software are already installed, you can set the path by adding following line to your `$HOME/.bash_profile` file

```bash
. /home/praveen/.setenv
```

Logout and login for the settings to work.

You can ssh into these machines using their hostname or IP number, see below

```shell
ssh -Y euler
```

The extra option enables you get display of some X programs. For example, the document viewer is evince

```shell
evince foo.pdf
```

## Euler (192.168.1.67)

* Dual Intel(R) Xeon(R) CPU E5-2699 v4 @ 2.20GHz (2 x 22 cores)
* 128 GB RAM
* [NVIDIA Quadro M5000    (GM204GL)](https://videocardz.net/nvidia-quadro-m5000)
* Storage: 2 TB + 2 TB
* OS: OpenSuse Leap 15.2

## Fourier (192.168.1.65)

* Dual Intel(R) Xeon(R) Gold 6148 CPU @ 2.40GHz (2 x 20 cores)
* 128 GB RAM
* [NVIDIA Quadro P4000](https://videocardz.net/nvidia-quadro-p4000)
* Storage: 2 TB + 2 TB
* OS: Debian 11 (Bullseye)

## Commands to get some info

See cpu info

```shell
cat /proc/cpuinfo
sudo dmidecode --type processor
sudo lshw -C cpu
```

See RAM info

```shell
cat /proc/meminfo
sudo dmidecode --type memory
sudo lshw -C memory
```

See disk info

```shell
sudo lshw -C disk
```

See OS info

```shell
lsb_release -a
```

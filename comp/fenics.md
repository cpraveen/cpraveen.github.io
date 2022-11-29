---
layout: default
---

# Fenics

## Install using Anaconda

Let us create a new environment called `fenics` and install under this.

```shell
conda create -n fenics -c conda-forge fenics mshr
```

You may also want to install some other packages

```shell
conda install -n fenics -c conda-forge ipython notebook matplotlib scipy
```

Now activate the environment and do your Fenics work

```shell
source activate fenics
```

After you are done working with Fenics

```shell
source deactivate
```

Show list of installed packages in this environment

```shell
conda list -n fenics
```

Update the packages in this environment

```shell
conda update -n fenics -c conda-forge --all
```

NOTE: Fenics installed via Anaconda does not provide full functionality of Fenics, and Docker images are the best option for this.

## Installing fenics using Docker

First install Docker; this is easy on a Mac and needs some configuration on Linux, see [here](comp/docker.html). After this, start Docker and install the fenics script

```shell
docker pull quay.io/fenicsproject/stable:latest
```

This installs the last version of fenics which is 2019.1.0.

## Installing an older version of fenics using Docker

To install an older version using Docker

```shell
docker pull quay.io/fenicsproject/stable:2017.2.0
```

Now, run this version like this

```shell
docker run -ti -p 127.0.0.1:8000:8000 -v $(pwd):/home/fenics/shared \
       -w /home/fenics/shared quay.io/fenicsproject/stable:2017.2.0
```

## Install dolfinx using docker

Install latest version

```shell
docker pull dolfinx/dolfinx:stable
```

Run in docker

```shell
docker run -ti -p 127.0.0.1:8000:8000 -v $(pwd):/home/fenics/shared \
       -w /home/fenics/shared dolfinx/dolfinx:stable
```

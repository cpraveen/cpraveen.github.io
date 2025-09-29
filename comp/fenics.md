---
layout: default
---

# Fenics

> These instructions refer to the older version of fenics which is no longer under development. The new version dolfinx is much different from fenics, see last section to install dolfinx from Docker.

## Install using Conda

Let us create a new environment called `fenics` and install under this.

```shell
conda create -n fenics
conda activate fenics
conda install -c conda-forge fenics-dolfinx mpich pyvista
```

You may also want to install some other packages

```shell
conda install -n fenics -c conda-forge ipython notebook matplotlib scipy
```

Now activate the environment and do your Fenics work

```shell
conda activate fenics
```

Show list of installed packages in this environment

```shell
conda list -n fenics
```

Update the packages in this environment

```shell
conda update -n fenics -c conda-forge --all
```

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

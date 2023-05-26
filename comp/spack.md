---
layout: default
---

# Spack

[Spack](https://spack.readthedocs.io) is a package manager which is very useful to install scientific software.

## Preparing a Linux system

We will install the gcc and gfortran compilers from the system package manager.  Dont install anything else since they will be installed using Spack. There are some instructions for [OpenSUSE](comp/suse.html) and [Debian](comp/debian.html). Since Spack installs its own MPI library, it is best to uninstall any MPI you may have installed from your system package manager, since having multiple MPI around can cause problems.

## Preparing a Mac system

* Make sure you have latest command line tools (XCode is not required).
* Install gcc from Homebrew which also provides the gfortran compiler. See [here](comp/brew.html).

## Install Spack

We will install Spack into `SPACK_ROOT` directory.

```bash
export SPACK_ROOT=/path/to/spack
```

Now get Spack

```shell
git clone https://github.com/spack/spack.git $SPACK_ROOT
```

You can add following lines to your `.bashrc` or `.profile` file

```bash
export SPACK_ROOT=/path/to/spack
. ${SPACK_ROOT}/share/spack/setup-env.sh
```

Here are some useful Spack commands

```text
spack list intel          -- search package names containing intel
spack info gcc            -- show information for package gcc
spack find                -- shows installed packages
spack compilers           -- show available compilers
spack location -i openmpi -- show location of openmpi
```

Setup compilers by running

```shell
spack compiler find
```

which creates the file `compilers.yaml` inside `$HOME/.spack/darwin` directory on MacOS and inside `$HOME/.spack/linux` on a Linux machine. Edit it if needed.

On Mac, use clang from Apple command line tools and gfortran from Homebrew. My file `$HOME/.spack/darwin/compilers.yaml` looks like this

```text
compilers:
- compiler:
    environment: {}
    extra_rpaths: []
    flags: {}
    modules: []
    operating_system: highsierra
    paths:
      cc: /usr/bin/clang
      cxx: /usr/bin/clang++
      f77: /usr/local/bin/gfortran
      fc: /usr/local/bin/gfortran
    spec: clang@9.0.0-apple
    target: x86_64
```

On Linux, use the gcc and gfortran from your system.


Set some package variants in `$HOME/.spack/darwin/packages.yaml` file like this

```text
packages:
   hdf5:
      require: +fortran +cxx +hl
   petsc:
      require: +mumps +suite-sparse
   cgns:
      require: +fortran
   trilinos:
      require: +rol
   all:
      providers:
         mpi: [mpich]
```

By default, Spack uses openmpi but you can select mpich as above. If you want to use openmpi, then change above line from mpich to openmpi or just dont specify the mpi provider.

My packages.yaml file for MacOS is available [here](https://raw.githubusercontent.com/cpraveen/cfdlab/master/configs/spack_packages.yaml).

## Install softwares

I install deal.II and its dependencies which provides all the softwares that I need for my work. Since I like to compile deal.II myself, I will install only dependencies. But first check that all variants you need are correct by running

```shell
spack spec dealii
spack spec -I dealii # -I shows already installed dependents
```

If this is ok, then we install

```shell
spack install -j4 --fail-fast --only dependencies dealii
```

The flag `-j4` means that four processes will be used while compiling; increase this if you have more cores on your computer. If you primarily use Petsc and Metis, and dont need other stuff, then do

```shell
spack spec petsc
spack install -j4 --fail-fast petsc
```

Now create a Spack view by running the script `spack_view.sh` which will install symlinks into `SPACK_VIEW` directory.

```bash
export SPACK_VIEW=/path/to/spack/view # Add to .bashrc or .profile file
sh /path/to/spack_view.sh /path/to/spack/view/dir
```

If the `SPACK_VIEW` directory is in not in your home directory, then set ownership, e.g.,

```shell
sudo mkdir $SPACK_VIEW
sudo chown praveen:users $SPACK_VIEW
```

and then run the `spack_view.sh` script. This is useful on a Linux computer where I want to install the software for all users.

Here is a sample [spack_view.sh](https://raw.githubusercontent.com/cpraveen/cfdlab/master/bin/spack_view.sh) script which you can edit for your needs.

You can set some variables in your `.bashrc` or `.profile` file

```bash
export PETSC_DIR=$SPACK_VIEW
export SLEPC_DIR=$SPACK_VIEW
export METIS_DIR=$SPACK_VIEW
export HDF5_DIR=$SPACK_VIEW
export PATH=$SPACK_VIEW/bin:$PATH
```

which can be used in your makefiles for compiling your applications.

## Upgrading

When I want to upgrade, I usually reinstall everything from scratch.

```shell
cd $SPACK_ROOT
git pull
```

Update your compilers.yaml and packages.yaml files if needed. Verify that you get all package variants that you need. Then continue

```shell
spack uninstall --all
spack install -j4 --fail-fast --only dependencies dealii
```

Now we create a new spack view,

```shell
sh /path/to/spack_view.sh /path/to/install/spack/view
```

## Finding info on an installed package

```shell
$ spack find -l petsc
==> 1 installed package
-- linux-opensuse_tumbleweed20200511-broadwell / gcc@9.3.1 ------
c67eysz petsc@3.13.1
```

Find more about installed petsc

```shell
spack spec /c67eysz
```
## Compiling deal.II using spack packages

If you want to compile deal.II on your own, then I have a cmake configure script [here](https://raw.githubusercontent.com/cpraveen/cfdlab/master/bin/dealii_spack.sh).

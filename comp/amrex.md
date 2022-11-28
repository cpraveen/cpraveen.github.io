---
layout: default
---

# AMREX

```bash
export AMREX_HOME=/path/to/amrex
```

For Arm Macs, create this file in `$AMREX_HOME/Tools/GNUMake/make.local`

```make
CXX = g++-11
CC  = gcc-11
FC  = gfortran-11
F90 = gfortran-11

INCLUDE_LOCATIONS += /opt/homebrew/include
```

For ARM macs, you may need to edit `$AMREX_HOME/Tools/GNUMake/comps/gnu.mak` file to remove quadmath library; change this line

```make
override XTRALIBS += -lgfortran -lquadmath
```

to

```make
override XTRALIBS += -lgfortran
```

Compile and run a make project, specify DIM if needed (default is DIM=3)

```bash
make -j4 DIM=2
./exe inputs
```

To use visit for animating solution

```shell
ls -1 plt*/Header | tee master.visit
visit -o master.visit
```

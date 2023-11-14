---
layout: default
---

# Clawpack

## Install from source

[See here for installation steps](http://www.clawpack.org/installing_fortcodes.html)

```shell
git clone git@github.com:clawpack/clawpack.git
cd clawpack
git tag -l                    # see available versions
git checkout v5.9.2           # Checkout version you want
git submodule init            # for repositories pyclaw, clawutil, visclaw, etc.
git submodule update          # clones all the submodule repositories
export CLAW=/path/to/clawpack # in your shell config
```

If you want to compile python/pyclaw support do this

```shell
conda install ipython matplotlib meson-python ninja nose notebook numpy scipy seaborn six
conda install petsc4py    # if you want parallel support.
                          # Add flah "-c conda-forge" if not using miniforge.
cd $CLAW
pip install --user --no-build-isolation -e .   # note trailing dot indicating "this directory"
```

This should install some files in your `$HOME/.local/lib/python#.#/site-packages` directory.

**Recommended**: You can also do this inside a conda environment in order to not mess with your base environment, see below for how to do this.

[Test a fortran example](http://www.clawpack.org/first_run_fortran.html#first-run-fortran)

The following command does all the steps: compile, run and make plots

```shell
cd $CLAW/classic/examples/acoustics_1d_example1
make .plots
```

Open `_plots/_PlotIndex.html` file to see the results.

Make options:

```shell
make .exe      # compile
make .output   # compile and run
make .plots    # compile, run and make plots
```

## Install using script

I have made a shell script which installs clawpack from source and uses conda to get python packages. 

```shell
wget https://raw.githubusercontent.com/cpraveen/cfdlab/master/bin/clawpack.sh
export CLAW=/path/to/clawpack   # where you want to install clawpack sources
sh ./clawpack.sh v5.9.2
```

## Install using conda

This does not seem to give the classic fortran version. But it will install pyclaw including parallel version which needs PETSc.

```shell
unset CLAW PYTHONPATH   # These might interfere if set to something already.
conda create -n claw
conda activate claw
conda install -c conda-forge clawpack ipython notebook nose six seaborn
```

Test pyclaw: start ipython and

```python
from clawpack.pyclaw import examples
claw = examples.shock_bubble_interaction.setup()
claw.run()
claw.plot()
```

To go out of this environment

```shell
conda deactivate
```

To delete this environment

```shell
conda remove -n claw --all
```

You can see a list of environments using

```shell
conda env list
```

## Examples from the book

The original set of examples designed to run with clawpack-4.3 are [here](https://depts.washington.edu/clawpack/clawpack-4.3/book.html). To run these, download Clawpack-4.3 and set `CLAW` to the path where it is located. Visualizing the results requires matlab.

Some of these have been converted to run with newer version of clawpack, see [here](http://depts.washington.edu/clawpack/users/book.html#book) and [here](http://depts.washington.edu/clawpack/users/claw/doc/gallery/gallery_book.html). You can get the code like this

```shell
cd $CLAW  # or where ever you want apps to be
git checkout master
git clone --recursive https://github.com/clawpack/apps
```

The book examples are in the directory `apps/fvmbook`.

## Documentation

* [Table of contents](https://www.clawpack.org/contents.html)
* [Riemann solvers](https://www.clawpack.org/riemann.html)
* [Shallow water Riemann solvers](https://www.clawpack.org/riemann/Shallow_water_Riemann_solvers.html)
* [PyClaw modules](https://www.clawpack.org/pyclaw/index.html#pyclaw-modules-reference-documentation)
  * [Understanding Pyclaw Classes](http://www.clawpack.org/pyclaw/classes.html)
  * [Python Riemann solver package](https://www.clawpack.org/pyclaw/rp.html)
  * [PyClaw solvers](https://www.clawpack.org/pyclaw/solvers.html)
  * [Setup your own problem](https://www.clawpack.org/pyclaw/problem.html)
* Visclaw
  * [setplot](http://www.clawpack.org/setplot.html)
* [Developer's Guide](https://www.clawpack.org/developers.html)

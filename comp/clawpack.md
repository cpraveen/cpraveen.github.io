---
layout: default
---

# Clawpack

## Installing using Conda

I have installed Clawpack using Conda. It is better to create a separate environment for this purpose

```shell
conda create -n claw
```

You can see a list of environments using

```shell
conda env list
```

To activate the environment

```shell
conda activate claw
```

Once you are inside this environment, install clawpack using pip, see [here](http://www.clawpack.org/installing_pip.html#installing-pip) for more details.

Now you can run Clawpack programs. Once you are done, you can deactivate the environment

```shell
conda deactivate
```

If you want to delete an environment

```shell
conda remove -n claw —-all
```

## Installing Clawpack fortran

[See here for installation steps](http://www.clawpack.org/installing_fortcodes.html)

```shell
git clone git@github.com:clawpack/clawpack.git
cd clawpack
git checkout v5.9.0     # or an older version; `git tag -l` to list options
git submodule init      # for repositories pyclaw, clawutil, visclaw, etc.
git submodule update    # clones all the submodule repositories
export CLAW=/full/path/to/clawpack    # in bash
```

[Test a fortran example](http://www.clawpack.org/first_run_fortran.html#first-run-fortran)

The following command does all the steps: compile, run and make plots

```shell
make .plots
```

Open _plots/_PlotIndex.html file to see the results.

## Install clawpack using conda

This does not seem to give the classic fortran version.

```shell
unset CLAW PYTHONPATH   # These might interfere is set to something already.
conda create -n claw
conda activate claw
conda install clawpack
conda install nose ipython
```

Test pyclaw: start ipython and

```python
from clawpack.pyclaw import examples
claw = examples.shock_bubble_interaction.setup()
claw.run()
claw.plot()
```

## Examples from the book

The original set of examples designed to run with clawpack-4.3 are [here](https://depts.washington.edu/clawpack/clawpack-4.3/book.html). To run these, download Clawpack-4.3 and set CLAW to the path where it is located. Visualizing the results requires matlab.

Some of these have been converted to run with newer version of clawpack, see [here](http://depts.washington.edu/clawpack/users/book.html#book) and [here](http://depts.washington.edu/clawpack/users/claw/doc/gallery/gallery_book.html). You can get the code like this

```shell
cd $CLAW  # or where ever you want apps to be
git checkout master
git clone --recursive https://github.com/clawpack/apps
```

The book examples are in the directory apps/fvmbook.

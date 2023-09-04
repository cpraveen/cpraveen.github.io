---
layout: default
---

# Python using Conda

I prefer to install [Miniforge](https://github.com/conda-forge/miniforge) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html) and then install whatever packages I need. Miniforge can be installed from brew, see below.

```shell
conda update conda
conda update --all
conda install numpy scipy sympy matplotlib ipython 
conda install jupyterlab
conda install jupyter_contrib_nbextensions
conda install ipympl          # matplotlib widget for jupyter
conda install ipywidgets
conda install prettytable
conda install pandas
conda install pylint autopep8 # vscode wants these
conda install clingo          # needed by spack
conda install meshio          # to read gmsh grids
conda install fortls          # needed to use vscode fortran
conda install imageio         # to read images from url
conda install tensorflow      # if you need this
conda install tensorflow-probability
conda install scikit-learn
conda install deepxde
conda install lfortran        # jupyter fortran kernel
conda install nose            # needed to use pyclaw
conda install six seaborn     # for riemann book/clawpack
conda install clawpack
```

or together

```shell
conda update conda && conda update --all && \
conda install numpy scipy sympy matplotlib ipython \
              jupyterlab jupyter_contrib_nbextensions \
              ipympl ipywidgets \
              prettytable \
              pandas \
              pylint autopep8 \
              clingo \
              meshio \
              fortls \
              imageio \
              tensorflow tensorflow-probability \
              scikit-learn \
              deepxde \
              lfortran \
              clawpack nose six seaborn
```

I set `PATH` to point to conda directory

```bash
export PATH=/path/to/conda/bin:$PATH
```

Install matlab jupyter integration if needed

```shell
pip install jupyter-matlab-proxy
```

See installed packages

```shell
conda list
```

Upgrade all packages

```shell
conda upgrade --all
```

Periodically, delete older versions of packages

```shell
conda clean --all
```

## Use Eigen with tensorflow

Install Miniconda and then

```shell
conda update conda
conda install nomkl  # use openblas instead of mkl
conda update --all
conda install tensorflow-eigen
```

## Install Mayavi: using conda

Make sure you are using pip from conda

```shell
conda install mayavi
pip install PyQt5
```

To upgrade pip installed packages

```shell
pip install --upgrade PyQt5 PyQt5-sip
```

## Install Mayavi: using pip

Conda may not have the latest mayavi, then use pip.  Make sure you are using pip from Conda.

```shell
pip install mayavi
pip install PyQt5
```

To upgrade pip installed packages

```shell
pip install --upgrade mayavi PyQt5
```

To see packages installed with pip

```shell
conda list | grep pypi
```

## Install via brew

miniforge is a community version of miniconda which can be easily installed using brew.

```shell
brew install --cask miniforge
conda init zsh  # If you use zsh, this modifies your .zshrc file
conda activate
```

Now you can install the packages you need.

## pylab

pylab imports some commonly used modules like numpy. Define an alias

```bash
alias pylab="ipython --pylab --matplotlib --nosep --pprint"
```

Now you can use it like this

```shell
$ pylab
Python 3.9.9 | packaged by conda-forge | (main, Dec 20 2021, 02:41:07)
Type 'copyright', 'credits' or 'license' for more information
IPython 8.0.0 -- An enhanced Interactive Python. Type '?' for help.
Using matplotlib backend: MacOSX
In [1]: x = linspace(0, pi, 100)
In [2]: y = sin(10 * x)
In [3]: plot(x, y)
```

## Nbextensions

Install this to get ToC and other features.

```shell
conda install  jupyter_contrib_nbextensions
```

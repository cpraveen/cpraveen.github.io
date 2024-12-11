---
layout: default
---

# Python using Conda

I prefer to install [Miniforge](https://github.com/conda-forge/miniforge) which is a community version of conda and uses conda-forge channel. It installs a minimal set of packages and then you can install whatever additional packages you need. 

## Install miniforge from github

Download the latest miniforge from [here](https://github.com/conda-forge/miniforge/releases) and the install from terminal

```
sh FILENAME.sh
```

Follow the instructions.

## Install miniforge via brew

On mac, install using [homebrew](https://brew.sh)

```shell
brew install --cask miniforge
conda init zsh  # If you use zsh, this modifies your .zshrc file
conda activate
```

Now you can install the packages you need.

## Install packages

```shell
conda update -y conda && conda update -y --all && \
conda install -y numpy scipy sympy matplotlib ipython \
                 jupyterlab ipympl ipywidgets \
                 pyvista prettytable pandas pylint autopep8 \
                 clingo meshio imageio vtk \
                 fprettify fortls lfortran \
                 mystmd pandoc jupytext \
                 jupyter-book sphinx-exercise sphinx-proof ghp-import \
                 tensorflow tensorflow-probability \
                 scikit-learn deepxde
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

Do not add env to prompt, we show it in window bar

```shell
conda config --set changeps1 False
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

Install this to get ToC and other features in jupyter notebooks.

```shell
conda install  jupyter_contrib_nbextensions
```

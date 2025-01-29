---
layout: default
---

# Discontinuous Galerkin Method for hyperbolic PDE

This is part of the workshop on Finite elements for Navier-Stokes equations, held in SERC, IISc during 8-12 September, 2014.

## Slides

1. [DGFEM for scalar conservation law in 1-D](https://github.com/cpraveen/femnse2014/blob/master/dg_scalar_1d.pdf?raw=true)
1. [DGFEM for system of conservation laws in 1-D](https://github.com/cpraveen/femnse2014/blob/master/dg_system_1d.pdf?raw=true)
1. DGFEM for conservation law in 2-D

## Additional resources

1. [S. Baskar, Introduction to scalar conservation laws](https://github.com/cpraveen/femnse2014/blob/master/conlaw.pdf?raw=true)
1. E. Godlewski and P. Raviart, Hyperbolic systems of conservation laws, Ellipses
1. R. J. LeVeque, Numerical methods for conservation laws, Birkhäuser

# Numerical examples

The numerical example codes are written using the deal.II finite element library. In order to run the codes, you have to first install deal.II on your computer. For most of the examples, a basic installation of deal.II without any additional libraries is sufficient. For the last example, you also need to install the Trilinos library and build deal.II with Trilinos support.

1. [1-d linear, scalar PDE](https://github.com/cpraveen/femnse2014/tree/master/1d_scalar_legendre)
1. [1-d Euler equations](https://github.com/cpraveen/femnse2014/tree/master/1d_euler_legendre)
1. [2-d linear scalar PDE](https://github.com/cpraveen/femnse2014/tree/master/2d_scalar_unsteady_legendre)
1. [2-d Euler equations](https://github.com/cpraveen/dflo.git) (requires Trilinos)

You are strongly encouraged to come to the lectures with deal.II installed on your laptop. To test your installation, run some of the examples included in deal.II and make sure they run successfully. If you have trouble installing deal.II, then write to Anant Diwakar (anant.diwakar @ gmail.com) for help. We may not be able to provide any help for installing on windows; please use Linux or Mac OSX. No installation help will be provided during the lectures.

## Getting the examples

You can download the code using git (recommended)

```shell
$ cd $HOME
$ git clone https://github.com/cpraveen/femnse2014.git
```

or download a zip file [here](https://github.com/cpraveen/femnse2014/archive/master.zip), or from your terminal

```shell
$ cd $HOME
$ wget https://github.com/cpraveen/femnse2014/archive/master.zip
$ unzip master.zip
$ mv femnse2014-master femnse2014
```

## Installing deal.II

Note: If you use Gentoo or Debian, you may be able to install deal.II relatively easily, see [here](http://www.dealii.org/download.html).

Otherwise, follows these steps. You will need atleast cmake, blas and lapack to install a basic version of deal.II. Download deal.II to your home directory and extract it.

```shell
$ cd $HOME
$ wget http://www.ces.clemson.edu/dealii/deal.II-8.1.0.tar.gz
$ tar zxvf deal.II-8.1.0.tar.gz
$ cd deal.II
```

If you dont have wget, copy and paste the url in your browser and download the file. Alternately, if you have git, you can download deal.II from github

```shell
$ cd $HOME
$ git clone https://github.com/dealii/dealii.git deal.II
$ cd deal.II
```

Create a build directory and download the script to configure deal.II

```shell
$ mkdir build
$ cd build
$ ~/femnse2014/dealii.sh
```

If the configure was successful, then you can compile

```shell
$ make all
```

If the build succeeds, then install it

```shell
$ make install
```

Add the path to deal.II in your `.bashrc` file.

```shell
export DEAL_II_DIR=$HOME/deal.II/install
```

Source your `.bashrc` file or open a new terminal.

### Test your deal.II

```shell
$ cd $DEAL_II_DIR/examples/step-1
$ cmake .
$ make
$ make run
```

This should generate two postscript files `grid-1.eps` and `grid-2.eps` which you can view with some postscript viewer like gv.

### Download deal.II documentation

```shell
$ cd $DEAL_II_DIR
$ wget http://www.ces.clemson.edu/dealii/deal.offlinedoc-8.1.0b.tar.gz
$ tar zxvf deal.offlinedoc-8.1.0b.tar.gz
$ rm deal.offlinedoc-8.1.0b.tar.gz
```

You can open `$DEAL_II_DIR/doc/index.html` in your web browser.

## Visualization software

Please install following software to visualize the solutions

1. [Gnuplot](http://www.gnuplot.info/)
1. [Visit](https://wci.llnl.gov/simulation/computer-codes/visit) or [Paraview](http://www.paraview.org/)

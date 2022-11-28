---
layout: default
---

# Julia

Install some commonly needed modules 

```shell
wget https://raw.githubusercontent.com/cpraveen/cfdlab/master/bin/julia.jl
julia julia.jl
```

To update all installed packages

```julia
using Pkg
Pkg.update()
```

On Linux, to install MAT, you need the hdf5-tools package to be installed first

```shell
sudo apt install hdf5-tools
```

To test the plotting, do the following (you must have installed Plots modules using Pkg.add)

```julia
using Plots
x = linspace(0,2*pi,100);
y = sin.(x);
plot(x,y)
```

To enable automatic recompilation in the REPL, install the Revise package and enable it in startup file: <code>$HOME/.julia/config/startup.jl</code>

```julia
ENV["MPLBACKEND"]="tkagg" # to use Agg backend with PyPlot
using Revise
```

## Plotting gui backend

To use TkAgg, do

```julia
julia> ENV["MPLBACKEND"]="tkagg"
julia> using PyPlot
```

or set this as default in `$HOME/.matplotlib/matplotlibrc` file

```text
backend : TkAgg
```

---
layout: default
---

# ATM Workshop on PDE and Mechanics

Kerala School of Mathematics<br/>
1-6 February, 2016<br/>
Kozhikode, Kerala<br/>
Supported by National Center for Mathematics<br/>
www: [www.atmschools.org/2016/atmw/pdem](http://www.atmschools.org/2016/atmw/pdem)

## Topics

Discontinuous Galerkin (DG) method for scalar conservation laws, semi-discrete scheme, numerical flux, L2 stability, entropy condition, basis functions, quadrature, Runge-Kutta scheme, numerical implementation, linear and non-linear examples, TVD and TVB limiter

## Notes

Get a pdf of the notes [here](https://github.com/cpraveen/ncmatmw2016/raw/master/dgnotes.pdf).

## Codes

The following codes are written in C++ using the [deal.II](http://www.dealii.org) library. You need to install deal.II for these codes to work. At the time of this workshop, we used deal.II version 8.3.0.

1. Linear convection equation in 1-D
1. Non-linear conservation law (Burgers equation)
1. Linear convection equation in 2-D

You can read the codes on [github](https://github.com/cpraveen/ncmatmw2016) where some more information is available on how to run the codes. You can also download the code using git

```shell
git clone git@github.com:cpraveen/ncmatmw2016.git
```

Or, download a [zip file](https://github.com/cpraveen/ncmatmw2016/archive/master.zip) of all the code.

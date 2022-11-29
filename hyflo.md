---
layout: default
---

# HyFLO: Hybridizable DG for CNS

DG schemes provide a basis for developing very higher order accurate codes for solving PDEs. However they have more degrees of freedom compared to continuous Galerkin methods. Hybridizable DG (HDG) schemes were developed in order to overcome some of the problems with DG schemes. Apart from the solution inside the cells, HDG schemes make use of an additional solution variable which lives only on the skeleton of the mesh (edges in 2-d and faces in 3-d). The solution in two neighbouring cells is coupled only through the skeleton solution. This allows us to eliminate the cell solutions and form a global problem involving only the skeleton solution, which has fewer degrees of freedom.

HyFLO is a HDG code for compressible Navier-Stokes equations written in C++ and built on top of the [deal.II](http://www.dealii.org) finite element library. It currently has the following features

* 2-d compressible NS
* Quadrilateral meshes
* Isoparametric elements using Winslow equations
* Steady state, BDF1, BDF2 time stepping schemes
* Newton method with exact jacobians using [Sacado](https://trilinos.org/packages/sacado)
* Uses linear solvers from [Trilinos](http://trilinos.sandia.gov)
* MPI-based parallel implementation, [p4est](http://www.p4est.org) for mesh partitioning

Future work will focus on

* Shock capturing using artificial dissipation
* 3-d compressible NS
* Geometry description using [OpenCascade](http://www.opencascade.com) for 3-D problems
* Solution-based grid adaptation
* Large Eddy Simulation

<p style="text-align:center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/P5ngplCZpS8" frameborder="0" allowfullscreen></iframe>
</p>

## References

<ol>

<li>
B. Cockburn, J. Gopalakrishnan, and R. Lazarov, Unified hybridization of discontinuous Galerkin, mixed and continuous Galerkin methods for second order elliptic problems, SIAM J. Numer. Anal. 47 (2009), pp. 1319-1365.
</li>

<li>
Jaime Peraire, Ngoc Nguyen, and Bernardo Cockburn. "A Hybridizable Discontinuous Galerkin Method for the Compressible Euler and Navier-Stokes Equations", 48th AIAA Aerospace Sciences Meeting, 4-7 January 2010, Orlando, Florida.
</li>

<li>
N. C. Nguyen and J. Peraire, Hybridizable discontinuous Galerkin methods for partial differential equations in continuum mechanics, Journal of Computational Physics, Volume 231 Issue 18, July, 2012, pp. 5955-5988.
</li>

</ol>

---
layout: default
---

> Here are some notes and tutorials converted into web books
>
> * [Introduction to Python](https://cpraveen.github.io/python)
> * [Numerical Analysis](https://cpraveen.github.io/numa)
> * [Numerical Linear Algebra](https://cpraveen.github.io/nla)
> * [Spectral Methods](https://cpraveen.github.io/chebpy)

> Teaching: In December 2024, I will be giving some lectures on discontinuous Galerkin methods at the [NCM workshop](teaching/ncm2024.html) to be held in IIPE, Visakhapatnam. From January 2025, I will be teaching the [numerical analysis course](teaching/acm2025.html) at TIFR-CAM for first year master students.

> Postdocs: I do not have postdoc positions at present but if you have good computational skills and are looking for a postdoc position, then [write](contact.html) to me. There are limited positions at TIFR-CAM, and if you have your own funding, e.g., via NPDF, NBHM, etc., I encourage you to write to me and apply for postdoc position at TIFR-CAM.

> Projects/internships: If you are a student looking for internship, project assistant position or postdoc position in the topic of computational PDE, please read [this](forstudents.html) and write to me if you are interested in doing some project.


I am a professor in the [Center for Applicable Mathematics](http://www.math.tifrbng.res.in), Bangalore, which is part of the [Tata Institute of Fundamental Research](http://www.tifr.res.in). This is my personal website while my official page is located [here](http://www.math.tifrbng.res.in/people/praveen).

<p style="text-align:center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/cTRQP6DSaqA" frameborder="0" allowfullscreen></iframe> <br/>
For the details of the numerical scheme, see <a href="http://arxiv.org/abs/1506.06140">here</a>.
</p>

## Latest News

<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <a href="{{ post.url }}">{{ post.date | date_to_string }}: {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

## Experience

* 3'rd Jan, 2005 to 14'th August 2006: Scientist, Computational and Theoretical Fluid Dynamics Division, National Aerospace Laboratories, Bangalore
* 1'st September 2006 to July 2008: Post-doc, Projet OPALE, INRIA, Sophia Antipolis
* 6 August 2008 to July 2011: Fellow (E), Tata Institute of Fundamental Research, Center for Applicable Mathematics, Bangalore.
* July 2011 to June 2018: Reader (F), Tata Institute of Fundamental Research, Center for Applicable Mathematics, Bangalore.
* July 2018 to December 2023: Associate Professor (G), Tata Institute of Fundamental Research, Center for Applicable Mathematics, Bangalore.
* January 2024 to present: Professor (H), Tata Institute of Fundamental Research, Center for Applicable Mathematics, Bangalore.

## Education

* BE, Mechanical Engineering, KREC, Surathkal, 1994-1998
* ME, Aerospace Engineering, IISc, Bangalore, 1998-2000
* PhD, Aerospace Engineering, IISc, Bangalore, 2000-2004

## Research

My primary research interest is CFD and its applications. I am also interested in numerical analysis and numerical solution of PDE in general.

* Computational Fluid Dynamics
* Kinetic schemes for compressible flows
* Meshless method
* Finite volume method
* Finite element and Discontinuous Galerkin Method
* Compressible flows, MHD, Shallow water
* Well-balanced scheme
* Adjoint equations and solvers
* Automatic differentiation
* Shape optimization
* Simplex method
* Particle swarm optimization
* Metamodelling, surrogate models
* Parallel computing

## Organizational activities

<ul>

<li>
<a href="http://math.tifrbng.res.in/~fem2012/Home.html" target="_blank">Instructional workshop on FEM, 2-13 July 2012</a>
</li>

<li>
<a href="https://events.tifrbng.res.in/indico/conferenceDisplay.py?confId=1" target="_blank">International conference on conservation laws and applications, 1-3 July 2013</a>
</li>

<li>
<a href="http://www.math.iisc.ernet.in/~ifcam/school.html" target="_blank">IFCAM Summer school on numerics and control of PDEs, 22 July - 2 August,  2013</a>
</li>

<li>
<a href="http://math.tifrbng.res.in/airbus-chair/Optpde13" target="_blank">Workshop on optimization with PDE constraints, Nov 25 - Dec 6, 2013</a>
</li>

<li>
<a href="http://cpde.tifrbng.res.in/femeet2014" target="_blank">Finite element meet, 18-20 Dec, 2014</a>
</li>

<li>
<a href="http://math.tifrbng.res.in/airbus-chair/Programs/fsi2015-school" target="_blank">Advanced Summer School on Control and Numerics for Fluid-Structure Interaction Problems, 22-26 June, 2015</a>
</li>

<li>
<a href="http://math.tifrbng.res.in/airbus-chair/Programs/fsi2015" target="_blank">Workshop on Control and Numerics for Fluid-Structure Interaction Problems, 29 June - 1 July, 2015</a>
</li>

<li>
<a href="http://cpde.tifrbng.res.in/2015" target="_blank">Conference on Computational PDE, 21-23 Dec, 2015</a>
</li>

<li>
<a href="http://math.tifrbng.res.in/airbus-chair/Programs/cns2016">Compact course on compressible Navier-Stokes equations, May 2016.</a>
</li>

<li>
<a href="https://maths.iitd.ac.in/drupal/node/159">GIAN course on Computational Solution of Hyperbolic PDE at IIT Delhi, 4-15 December, 2017.</a>
</li>

<li>
<a href="https://www.math.tifrbng.res.in/conference-in-honour-of-prof-a-s-vasudeva-murthy">Conference on PDE and Numerical Analysis, 28-30 April 2022, online conference organized in memory of Prof. A. S. Vasudeva Murthy.</a>
</li>

<li>
<a href="https://www.atmschools.org/school/2023/NCMW/fvsmhp">NCM Workshop on Finite Volume and Spectral Methods for Hyperbolic Problems, December 2023.</a>
</li>

</ul>

## Fun in research

<ul>

<li>
<a href="cfd/future.html">Will the wind tunnel replace the computer ?</a>
</li>

<li>
<a href="cfd/wine.html">The Wine Snobs Guide To Flux Functions</a>
</li>

<li>
<a href="cfd/fitted.html">The Fitted Mesh Story...,</a>
</li>

<li>
<a href="cfd/view.html">A one-sided view</a>
</li>

<li>
<a href="cfd/history.html">The Turbulent History of Fluid Mechanics</a>
</li>

</ul>

## Computing

<ul>

<li>
<a href="comp/macosx.html">Computing on Mac OSX</a>
</li>

<li>
<a href="comp/amrex.html">Amrex</a> |
<a href="comp/bash.html">Bash</a> |
<a href="comp/cchpc19.html">cchpc19</a> |
<a href="comp/clawpack.html">Clawpack</a> |
<a href="comp/debian.html">Debian</a> |
<a href="comp/docker.html">Docker</a> |
<a href="comp/fenics.html">Fenics</a> |
<a href="comp/githowto.html">Git HowTo</a> |
<a href="comp/gnuplot.html">Gnuplot</a> |
<a href="comp/brew.html">Homebrew</a> |
<a href="comp/julia.html">Julia</a> |
<a href="comp/jupyter.html">Jupyter</a> |
<a href="comp/latex.html">Latex</a> |
<a href="comp/lftp.html">LFTP</a> |
<a href="comp/matplotlib.html">Matplotlib</a> |
<a href="comp/suse.html">OpenSuse</a> |
<a href="comp/pbs.html">PBS</a> |
<a href="comp/conda.html">Python</a> |
<a href="comp/screen.html">Screen</a> |
<a href="comp/spack.html">Spack</a> |
<a href="comp/ssh.html">SSH</a> |
<a href="comp/texmacs.html">TeXMacs</a> |
<a href="comp/vim.html">Vim</a> |
<a href="comp/visit.html">VisIt</a> |
<a href="comp/wsl.html">WSL</a> |
<a href="comp/xmgrace.html">xmgrace</a>
</li>

<li>
<a href="comp/comp.html">Computers at TIFR-CAM</a>
</li>

</ul>

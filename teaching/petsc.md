---
layout: default
---

# PETSc

[PETSc](https://www.mcs.anl.gov/petsc) is a library for large scale numerical linear algebra but it also has support for finite elements, time stepping schemes, mesh management, etc. The three main methods for solving equations are

1. KSP: Methods for solving matrix equations, i.e., linear solvers
1. SNES: Newton method for solving non-linear equations
1. TS: Time stepping schemes

You should subscribe to the [mailing list](https://lists.mcs.anl.gov/mailman/listinfo/petsc-users) if you want help, and the PETSc developers are incredibly helpful (of course, please do your homework first before asking questions).

## Tutorials and examples

If you download the PETSc source code and extract it to some place, you can access example codes which are well documented. You can access an index page that links to examples and documentation here [(online version)](https://www.mcs.anl.gov/petsc/documentation/index.html).

```text
docs/index.html
```

The location of the example source codes is

```text
src/ksp/ksp/examples/tutorials
src/snes/examples/tutorials
src/ts/examples/tutorials
```

It is easier to view the examples through the html index which gives better documentation, see

```text
src/ksp/ksp/examples/tutorials/index.html
src/snes/examples/tutorials/index.html
src/ts/examples/tutorials/index.html
```

For a quick introduction to some of the methods, see the [Hands on Exercises](https://www.mcs.anl.gov/petsc/documentation/tutorials/HandsOnExercise.html).

## Other resources

1. [Book on PETSc for PDEs](https://my.siam.org/Store/Product/viewproduct/?ProductId=32850137), [codes used in the book](https://github.com/bueler/p4pdes)
1. [Lid-driven cavity](https://github.com/xsdk-project/xsdk-examples/tree/master/petsc)

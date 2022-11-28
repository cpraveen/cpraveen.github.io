---
layout: default
---

# Gnuplot tips

## Simple animation

This example shows how to directly pipe data to gnuplot to get an animation.

```fortran
      program main
      implicit none

      integer it, i, np
      real*8  t, dt, dx, x, PI
      parameter(PI=4.0d0*datan(1.0d0))

      dt = 0.1d0
      t  = 0.0d0
      np = 100
      dx = 1.0d0/(np-1)

      do it=1,100
         t = t + dt
         print*,"set title 'Iter=",it,"  Time =",t,"'"
         print*,"set xlabel 'x'"
         print*,"set ylabel 'f'"
         print*,"plot [0:1][-1.1:1.1] '-' w l lw 2"
         do i=1,np
            x = (i-1)*dx - t
            print*,(i-1)*dx,dsin(2.0d0*PI*x)
         enddo
         print*,"e"
         print*,"pause 0.2"
      enddo

      stop
      end
```

Compile the fortran program and run it as follows

```shell
gfortran anim.f
./a.out | gnuplot
```

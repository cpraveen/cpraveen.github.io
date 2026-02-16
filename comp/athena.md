# Athena code

Get the code

```shell
git clone https://github.com/PrincetonUniversity/athena
```

## Compile for Riemann problem

```shell
cd athena
./configure.py --prob shock_tube \
               --coord cartesian \
               --eos adiabatic \
               --flux hlld \
               -b
make
```

## Run Brio-Wu example

```shell
mkdir brio-wu
cp inputs/mhd/athinput.bw brio-wu
cd brio-wu
../bin/athena -i athinput.bw
```

Plot solution at final time

```gnuplot
gnuplot> p 'Brio-Wu.block0.out1.00040.tab' u 2:3 w lp
```

Look into the input file `athinput.bw` and change grid size, domain, final time, Riemann data, etc.

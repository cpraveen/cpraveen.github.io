---
layout: default
---

# cchpc19

The overview of hardware specification of the cchpc19 cluster is given below:

Overview:

```text
Computational servers (NODE1-NODE20)
GPU computational Server (GPU01)
Storage system (DELL EMC ME4024 )
Dell Networking Switch S4048 10GbE (10Gb x 48 ports)
```

Head node server:

```text
Head node based on a Dell PowerEdge R540 Server
16 cores, 2.1Ghz
96GB memory
Lustre Parallel File System
```

Computational servers:

```text
Compute nodes based on Dell PowerEdge C6420
32 cores, 2.1GHz CPUs per node
96 GB memory
Ethernet interfaces
Dedicated storage system
Dedicate storage of 34TB
```

Software installed:

```text
Operating System - RHEL 7.4
Job scheduler PBS PBSpro 19.1.1
GCC Compiler
Gaussian 9Dc.01
MPI
```

GUP01 server:

```text
Dell PowerEdge R740 Server
16 cores, 2.1Ghz
96GB memory
NVIDIA Tesla V100 16GB
```

Available queues:

```text
----------------------------
Queue  nodes  cores   time
----------------------------
small    1      32     96 h
large    4     128     48 h
long     1      32    720 h
```

Available RAM:

```text
-----------------------
Node    Max    Useable
-----------------------
1-17    96 gb   72 gb
18-20  124 gb   92 gb
```

---
layout: default
---

# PBS

See available compute nodes

```shell
pbsnodes -a
```

See available queues

```shell
qstat -Qf
```

Submit a job

```shell
qsub pbs.sh
```

See list of jobs in queue

```shell
qstat
```

Detailed info of all running jobs, per line

```shell
qstat -n -1
```

List of jobs for USER

```shell
qstat -u USER
```

Detailed info for all jobs

```shell
qstat -f
```

Detailed info for one job

```shell
qstat -f JOBID
```

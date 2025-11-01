---
layout: default
---

# Chapel

## Controlling number of threads

By default Chapel programs will use as many threads as the number of available physical cores. On Apple cpus, only the performance cores seems to be used.

To control the number of threas, set the environment variables

```shell
export CHPL_RT_NUM_THREADS_PER_LOCALE=#
```

or specify if as an argument

```shell
./exe --dataParTasksPerLocale #
```

See the Chapel [documentation](https://chapel-lang.org/docs/usingchapel/executing.html#controlling-degree-of-data-parallelism) for more on this.

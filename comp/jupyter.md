---
layout: default
---

# Jupyter notebooks

Jupyter can be used either as `jupyter-notebook` or `jupyter-lab`.

See list of kernels

```shell
jupyter kernelspec list
```

Delete unwanted kernel

```shell
jupyter kernelspec uninstall julia-1.7
```

Use svg image format

```text
%config InlineBackend.figure_format = 'svg'
```

For more line magics and cell magics, see [this page](https://ipython.readthedocs.io/en/stable/interactive/magics.html)

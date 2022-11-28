---
layout:: default
---

# Plotting with Matplotlib

See [here](http://nbviewer.jupyter.org/github/cpraveen/python/blob/master/04_matplotlib.ipynb) for some examples. The codes [here](https://github.com/cpraveen/cfdlab/tree/master/python) show how to set plot parameters in one place and use it in other scripts.

## Matplotlib settings

```python
from matplotlib import rcParams
rcParams['font.size'] = 14
rcParams['font.family'] = 'serif'
rcParams['figure.autolayout'] = True
rcParams['lines.linewidth'] = 2
rcParams['lines.markersize'] = 6
rcParams['axes.titlesize'] = 14
rcParams['axes.labelsize'] = 14
rcParams['text.usetex'] = True    # This will use Latex fonts (slow)
```

## Line width and marker size

```python
lw = 3 # linewidth
ms = 8 # marker size
plt.plot(x,y,'o-',lw=lw,ms=ms)
```

## Tight axis

To make both axes tight

```python
plt.axis('tight')
```

Make x axis tight

```python
plt.autoscale(enable=True, axis='x', tight=True)
```

## Set axes range

To set both axes

```python
plt.axis([0, 1, -1, 1])
```

To set independently

```python
plt.xlim(0,1)
plt.ylim(-1,1)
```

## Plotting backend

Plotting backends might create problems on mac. If this happens, then try this

```python
import matplotlib
matplotlib.use("TkAgg")
import matplotlib.pyplot as plt
```

NOTE: You must set the backend before importing pyplot.

You can set this as default; for example in anaconda, I create a file

```text
/path/to/anaconda/lib/python3.6/site-packages/sitecustomize.py
```

and in this put the following

```python
import matplotlib
matplotlib.use("TkAgg")
```

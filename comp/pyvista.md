---
layout:: default
---

# Plotting with PyVista

## Saving to file

```python
import pyvista as pv

p = pv.Plotter(window_size=(1024,1024))
// plot the figure
p.view_xy()
p.camera.zoom(value) # may need to adjust window size and zoom level for each plot
p.save_graphic("sol.pdf") # pdf, eps, ps, svg
p.screenshot("sol.png") # png,  jpeg, jpg, bmp, tif
p.show() # show plot in a window
```

`save_graphic`: File sizes of pdf, eps,ps it too large, svg size is ok and very good quality, but I dont know if journals accept svg.  The figure saved to file does not look exactly same as what you see in the plot window, this is not good.

`screenshot`: File sizes are ok, figure saved looks same as what you see in the plot window.  Saving in png seems best option for journal submission.

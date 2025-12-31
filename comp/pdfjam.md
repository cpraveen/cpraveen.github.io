---
layout:: default
---

# pdfjam

Extract selected pages

```shell
pdfjam in.pdf 10-20 -o out.pdf
pdfjam in.pdf '10-20,30,40' -o out.pdf
pdfjam in.pdf '10-20,{},30,{},40' -o out.pdf  # {} puts blank pages
pdfjam in.pdf 10- -o out.pdf                  # pages 10 up to end
```

Remove author info

```shell
pdfjam --no-keepinfo in.pdf -o out.pdf
```

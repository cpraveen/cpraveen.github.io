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

Extract and merge first page from multiple pdfs

```shell
pdfjam foo1.pdf 1 foo2.pdf 1 foo3.pdf 1 -o out.pdf
```

Remove author info

```shell
pdfjam --no-keepinfo in.pdf -o out.pdf
```

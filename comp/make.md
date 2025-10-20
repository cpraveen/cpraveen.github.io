---
layout: default
---

# Make files

Create `.o` from `.c` file

```make
%.o: %.c
    $(CC) -c $<
```

Specify dependency on some include files

```make
%.o: %.c a.h b.h c.h
    $(CC) -c $<
```

Per file dependency can be specified

```make
a.o: a.c x.h y.h
b.o: b.c y.h z.h
```

Create executable from each `.c` file

```make
%: %.c
    $(CC) $< -o $@
```

Compile several files into an executable (not optimal as it compiles all files each time)

```make
exe: a.c b.c c.c
    $(CC) $^ -o $@
```

List of all `.c` files

```make
SRC = $(wildcard *.c)
```

Create list of `.o` files for each `.c` file

```make
OBJ = $(SRC:.c=.o)
```

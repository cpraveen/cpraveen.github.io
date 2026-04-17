---
layout: default
---

# Make files

Create `.o` from `.c` file

```text
%.o: %.c
    $(CC) -c $<
```

Specify dependency on some include files

```text
%.o: %.c a.h b.h c.h
    $(CC) -c $<
```

Per file dependency can be specified

```text
a.o: a.c x.h y.h
b.o: b.c y.h z.h
```

Create executable from each `.c` file

```text
%: %.c
    $(CC) $< -o $@
```

Compile several files into an executable (not optimal as it compiles all files each time)

```text
exe: a.c b.c c.c
    $(CC) $^ -o $@
```

List of all `.c` files

```text
SRC = $(wildcard *.c)
```

Create list of `.o` files for each `.c` file

```text
OBJ = $(SRC:.c=.o)
```

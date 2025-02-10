---
layout: default
---

# Xmgrace

Copy template file from

```text
/opt/homebrew/Cellar/grace/###/templates/Default.agr
```

to `$HOME/.grace/templates` and modify it to your needs.

## Single file

Plot first vs second column

```shell
xmgrace -block file -bxy 1:2
```

Plot first vs second, first vs third

```shell
xmgrace -block file -bxy 1:2 -bxy 1:3
```

Plot all columns in file vs first column

```shell
xmgrace -nxy file
```

## Multiple files

Plot three graphs from three different files

```shell
xmgrace -block file1 -bxy 1:3 -block file2 -bxy 1:3 -block file3 -bxy 1:3
```

Plot a column from all files

```shell
xmgrace -block file* -bxy 1:2
```

Plot all columns from all files

```shell
xmgrace -nxy file*
```

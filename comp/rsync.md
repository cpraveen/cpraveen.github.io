---
layout: default
---

# Rsync

Sync the contents of `src` to `dst`

```shell
rsync -avP --delete /path/to/src/ /path/to/dst
```

If the destination is on a different machine over a network

```shell
rsync -avzP --delete /path/to/src/ username@hostname:/path/to/dst
```

In fact, rsync is a modern replacement for scp.

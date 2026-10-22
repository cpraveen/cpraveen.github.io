---
layout: default
---

# OpenCode

## About background service

Start without background service

```shell
opencode --standalone
```

Check status of background service

```shell
opencode service status
```

Stop running background service

```shell
opencode service stop
```

Disable background service

```shell
opencode service set disabled true
```

To re-enable background service

```shell
opencode service unset disabled
```

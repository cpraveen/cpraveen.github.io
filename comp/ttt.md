---
layout: default
---

# ttt editor

## Installation

On mac

```shell
brew tap eugenioenko/ttt
brew trust eugenioenko/ttt
brew install ttt
```

For Linux, download the [binary](https://github.com/eugenioenko/ttt/releases) and copy it somewhere like `~/.local/bin`.

## Vim mode

```shell
mkdir -p ~/.config/ttt/plugins/vim
cd ~/.config/ttt/plugins/vim
wget https://raw.githubusercontent.com/eugenioenko/ttt-vim/refs/heads/main/plugin.ttt.json
wget https://raw.githubusercontent.com/eugenioenko/ttt-vim/refs/heads/main/init.lua
```

and start `ttt` and accept permissions.

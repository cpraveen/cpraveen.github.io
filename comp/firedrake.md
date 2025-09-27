---
layout: default
---

# Firedrake

[Firedrake](https://www.firedrakeproject.org) is a finite element software.

## Install inside a docker image

Pull debian

```shell
docker pull debian:stable
```

Start it

```shell
docker run -it --name debian debian:stable
```

Inside the container, run the commands given [here](https://github.com/cpraveen/cfdlab/blob/master/bin/firedrake_debian.sh) to install firedrake and some other needed softwares.

Add some settings in `.bashrc` file

```shell
PS1="$ "

# Git branch in prompt.
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

PROMPT_COMMAND='echo -ne "\033]0;@docker:${PWD/$HOME/\~}$(parse_git_branch)\007"'

export LS_OPTIONS='--color=auto'
alias ls='ls $LS_OPTIONS'
export OMP_NUM_THREADS=1
export VIRTUAL_ENV_DISABLE_PROMPT=1
```

Subsequently, you can start and attach to this container

```shell
docker start debian
docker attach debian
```

Activate the env

```shell
. /root/firedrake/bin/activate
```

Now you can run firedrake programs inside the container.

## Create an image from this container

You can create an image out of this container.

```shell
docker commit debian firedrake
```

Run the image

```shell
docker run -it --name firedrake -p 8888:8888 \
           -v $(pwd):/root/shared -w /root/shared \
           firedrake:latest
```

You can start jupyter inside container

```shell
. /root/firedrake/bin/activate
jupyter-lab --ip 0.0.0.0 --port 8888 --no-browser --allow-root
```

and access it from the host at displayed url. Subsequently you can join this container

```shell
docker start firedrake
docker attach firedrake
```


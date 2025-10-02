---
layout: default
---

# Firedrake

[Firedrake](https://www.firedrakeproject.org) is a finite element software.

## Install inside a docker image

Firedrake does not provide a Docker image for arm, so we build it ourselves.

Pull Debian image

```shell
docker pull debian:stable
```

Start it

```shell
docker run -it --name debian debian:stable
```

Inside the container, run the commands given [here](https://github.com/cpraveen/cfdlab/blob/master/bin/firedrake_debian.sh) to install firedrake and some other needed softwares.

Add some settings in `~/.bashrc` file

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

Subsequently, if you exit the container, you can start and attach to it like this

```shell
docker start debian
docker attach debian
```

Activate the env

```shell
. /root/firedrake/bin/activate
```

Now you can run firedrake programs inside the container.

## Create an image

Create an image called `firedrake` out of the `debian` container.

```shell
docker commit debian firedrake
```

`cd` to the directory you want to share with the container (dont do this from your `HOME` directory) and run the `firedrake` image (it likely has tag `latest`)

```shell
docker run -it --name firedrake -p 8888:8888 \
           -v $(pwd):/root/shared -w /root/shared \
           firedrake:latest
```

That directory will now be accessible inside the container at `/root/shared`.

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

You can also upload the `firedrake` image to your docker hub and you can use it from another computer and others can also use it.

```shell
security unlock-keychain                # only needed if logged into mac via ssh
docker login -u cpraveen
docker tag firedrake:latest cpraveen/firedrake:latest
docker push cpraveen/firedrake:latest
```

You can see the image in [my docker hub](https://hub.docker.com/r/cpraveen/firedrake/tags). Since I have a free account, images may get deleted after some days.

---
layout: default
---

# Docker on Linux

Once docker is started, enable it to start automatically

```shell
sudo systemctl enable docker
```

If you are behind a proxy, you need to set the proxy server 

```shell
sudo mkdir -p /etc/systemd/system/docker.service.d
sudo vi /etc/systemd/system/docker.service.d/http-proxy.conf
```

Put the following in this file

```text
[Service]
Environment="HTTP_PROXY=http://192.168.1.1:3128"
```

Now restart to take effect

```shell
sudo systemctl daemon-reload
sudo systemctl restart docker
systemctl show --property=Environment docker
```

The last command should show the proxy server. Now test that docker is working

```shell
docker run hello-world
```

For a non-root user to run docker, you must add them to docker group

```shell
sudo usermod -aG docker USERNAME
```

See installed docker images

```shell
docker images
```

Delete an image

```shell
docker rmi <IMAGE ID>
```

To see all containers

```shell
docker ps -a
```

To remove a container

```shell
docker rm <CONTAINER ID>
```

Stop and remove all docker containers

```shell
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

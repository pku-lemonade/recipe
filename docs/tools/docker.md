# Docker

## docker/podman

`docker`是容器工具，可以用来构建可重现的开发环境。

`podman`是`docker`的替代工具，与`docker`的命令**兼容**，可以在不需要`root`权限的情况下使用。

```bash
alias docker=podman
```

## docker 镜像选择

在配置环境时，如果需要特定版本的操作系统，可以在 [Docker Hub](https://hub.docker.com/)或者[AWS ECR](https://gallery.ecr.aws)上搜索对应操作系统的 tag。

```bash
docker pull ubuntu:18.04
```

如果需要特定软件的安装环境，也可以在上述网站搜索对应软件的镜像。这些镜像内通常都安装了对应的依赖，使用起来比较方便。比如，[这个](https://hub.docker.com/_/python)页面上可以找到不同版本的`python`镜像。

```bash
docker pull python:3.12
```

如果需要使用 GPU，可以在[NVIDIA NGC](https://ngc.nvidia.com/catalog/containers)上搜索镜像，找到安装好`PyTorch`或`Tensorflow`的镜像。比如，[这个](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/pytorch/tags)页面上可以找到不同版本`PyTorch`的镜像。

```bash
docker pull nvcr.io/nvidia/pytorch:24.12-py3
```

如果这些基础镜像都不满足需求，可以使用自己构建镜像。方法可以参考[这里](https://docs.docker.com/engine/reference/builder/)。因为这个相对复杂，最快的方法是向有经验的同学描述自己的问题，请他帮忙写`Dockerfile`。

下面是一个`zsim`镜像的例子。

```Dockerfile
FROM public.ecr.aws/ubuntu/ubuntu:18.04_stable

RUN apt-get update; \
    apt-get install -y --no-install-recommends \
    gcc \
    g++ \
    scons \
    libelf-dev; \
    rm -rf /var/lib/apt/lists/*

ENV LIBCONFIGPATH /libconfig
ENV HDF5PATH /hdf5
ENV PINPATH /pin-2.14-71313-gcc.4.4.7-linux

COPY ./deps /

WORKDIR /zsim
```

## docker 基本操作

具体操作见`tldr docker`命令的输出。这里只强调一下使用 GPU 的命令。

```bash
docker run --gpus all -it --rm –v local_dir:container_dir nvcr.io/nvidia/pytorch:21.02-py3
```

其中，`--gpus all`表示使用所有 GPU。`-v`将本地目录挂载到容器内的目录。

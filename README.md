
*adegenet* docker images
========================

What is this?
-------------

[Docker](https://www.docker.com/what-docker) provides a robust, lightweight way
to ship applications within a small, self-sufficient operating system, which
includes all the dependencies and tools required for the app the run
smoothly. This structure is called a *container*, and different versions of a
container are referred to as *images*.

*adegenet* docker images are meant first for testing, but can also be used for
 data analysis.



How can I use it?
-----------------

### Installing docker

First of all, you need docker installed on your computer. Follow [this
link](https://www.docker.com/community-edition#/download) for guidelines to
install Docker Community Edition.

Then you need to choose the *adegenet* docker image you want to use (see next
sections on available images), and choose how you want to use the image. There
are **two recommended ways** to use *adegenet* docker images: starting a **Rstudio
server**, or starting a **bash session**.


### Rstudio server 

This approach is aimed at regular users, is the use the image to start a Rstudio
server, which enable the user to start a Rstudio session within a web browser,
with the devel version of *adegenet* and its dependencies pre-installed.

This image is started by typing:
```
docker run -d -p 8787:8787 thibautjombart/adegenet
```

A Rstudio session can then be started by opening a web browser and going to the
URL `127.0.0.1:8787` (or `localhost:8787`). The login and password are
'rstudio'.




### `bash` session

This approach is recommended for developers, and is especially useful for
testing. It will open a `bash` shell logged as `guest` within the
`/home/guest`. A folder `/home/guest/dev` will contain git clones of the various
installed packages. A R session can be started (without support for graphics)
simply by typing `R`.

To start the docker image with a `bash` shell, type:
```
docker run --rm -it --user guest thibautjombart/adegenet /bin/bash
```



Building the docker image
-------------------------

To build this image, you first need to download the `Dockerfile`
(`docker/testing/Dockerfile`), and then type:

```
docker build -t adegenet_devel testing/
```

To tag the image, then use:
```
docker tag adegenet_devel thibautjombart/adegenet:latest
```

To publish the image:
```
docker push thibautjombart/adegenet:latest
```

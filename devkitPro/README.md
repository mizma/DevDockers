# devkitPro build dockerfile

Simple archlinux based Dockerfile to setup basic devkitPro
compilation and editing environment.

## Build Image

~~~bash
docker buildx build --tag name:tag .
~~~

## run image

~~~bash
docker run --name devkitpro -it -v /path/to/devRepo:/root/devRepo name:tag
~~~

## compile

~~~bash
cd /path/to/devRepo && make
~~~

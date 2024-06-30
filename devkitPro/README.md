# devkitPro build dockerfile

Simple archlinux based Dockerfile to setup basic devkitPro
compilation and editing environment.

## Build Image

~~~bash
docker build --tag name:tag .
~~~

## run image

~~~bash
docker run -it -v /path/to/devRepo:/root/devRepo name:tag
~~~

## compile

~~~bash
cd /path/to/devRepo && make
~~~

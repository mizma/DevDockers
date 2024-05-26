# GP2040 build dockerfile

Simple archlinux based Dockerfile to setup basic GP2040-ce
compilation and editing environment.

## Build Image

~~~bash
docker build --tag name:tag .
~~~

## run image

~~~bash
docker run -it -v /path/to/GP2040-ce:/root/GP2040-ce name:tag
~~~

## compile

1. set the environment variable GP2040_BOARDCONFIG accordingly
2. cd into /root/GP2040-ce/build and run `cmake .. && make`


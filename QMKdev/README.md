# GP2040 build dockerfile

Simple archlinux based Dockerfile to setup basic QMK compilation and editing environment.

## Build Image

~~~bash
docker build --tag name:tag .
~~~

## run image

~~~bash
docker run --name qmkdev -it name:tag
~~~

## compile/develop

* If using git inside, configure git user.name and user.email, setup SSH
* set the origin URL to your own repo
* Follow instructions on [qmk documentation site](doc.qmk.fm)

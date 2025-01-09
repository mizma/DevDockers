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

### vial

* run `cd /root/vial-qmk && make git-submodule` to prepare environment.
  * check `qmk doctor` afterwards
* build the firmware with the vial keymap using `make your/keyboard:vial`

### Copy the build file

* `docker cp qmkdev:/root/qmk-firmware/mzmkb_slimdash_rev1_default.uf2 .`
* `docker cp qmkdev:/root/vial-qmk/mzmkb_slimdash_rev1_vial.uf2 .`

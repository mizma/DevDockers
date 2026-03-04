# Hyprland build dockerfile

Simple archlinux based Dockerfile to setup basic Hyrpland
compilation and editing environment.

## Build Image

~~~bash
docker buildx build --tag name:tag .
~~~

replace `name:tag` with whatever is appropriate.

## run image

~~~bash
docker run --name hyprdev -it -v /path/to/Hyprland:/root/Hyprland name:tag
~~~

name:tag should be whatever you selected at build-time.

For rest of the use, refer to the [docker documentation](https://docs.docker.com/),
or refer to something like [tldr](https://github.com/dbrgn/tealdeer)

## compile

`make debug` for debug, `make all` for normal build

## Note on use

* This image assumes you have the Hyprland repository on the host and use -v to mount the repo inside the container
* Any new file you create inside the container may have permission set to root so you may need to `sudo chown -R user:user <repo>` on host to fix permissions.
* This Dockerfile uses a personalized nvim config (based on LazyVim) which may have some unnecessary things.  Replace with your desired configs as necessary.
  * dockerfile installs some pre-requisites for this LazyVim plugins to work.

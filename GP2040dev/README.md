# GP2040 build dockerfile

Simple archlinux based Dockerfile to setup basic GP2040-ce
compilation and editing environment.

## Build Image

~~~bash
docker buildx build --tag name:tag .
~~~

replace `name:tag` with whatever is appropriate.

## run image

~~~bash
docker run --name gp2040ce -it -v /path/to/GP2040-ce:/root/GP2040-ce name:tag
~~~

name:tag should be whatever you selected at build-time.

For rest of the use, refer to the [docker documentation](https://docs.docker.com/),
or refer to something like [tldr](https://github.com/dbrgn/tealdeer)

## compile

1. set the environment variable GP2040_BOARDCONFIG accordingly
2. `mkdir /root/GP2040-ce/build`
3. `cd /root/GP2040-ce/build && cmake .. && make`

## Note on use

* This image assumes you have the GP2040-ce repository on the host and use -v to mount the repo inside the container
* Any new file you create inside the container may have permission set to root so you may need to `sudo chown -R user:user <repo>` on host to fix permissions.
* This Dockerfile uses a personalized nvim config (based on LazyVim) which may have some unnecessary things.  Replace with your desired configs as necessary.
  * dockerfile installs some pre-requisites for this LazyVim plugins to work.

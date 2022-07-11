# Mad Science Lab C Unit Testing Docker Image
C unit testing environment with Unity, CMock, and Ceedling. The purpose of this docker
image is to create an easy-to-install portable system for running unit tests with Ceedling.

## Contents
* Testing tools
  * [Ceedling](http://www.throwtheswitch.org/ceedling) 0.31.0
  * [CMock](http://www.throwtheswitch.org/cmock) 2.5.2
  * [Unity](http://www.throwtheswitch.org/unity) 2.5.1
* C support
  * [CException](http://www.throwtheswitch.org/cexception) 1.3.2
  * [libc-dev 0.7.2](https://pkgs.alpinelinux.org/package/v3.11/main/x86/libc-dev)
* Environment
  * [coreutils 8.31](https://pkgs.alpinelinux.org/package/v3.11/main/x86/coreutils)
  * gcc 9.3.0
  * gcov 9.3.0
  * gdb 8.3.1
  * valgrind 3.15.0
  * Ruby 2.7.1

## Usage

```bash
docker run -it --rm -v <local project path>:/project throwtheswitch/madsciencelab[:tag]
```
But a better solution is a .bashrc function that automatically maps your pwd to project and sets the user and group to the current user.
This avoids file creation as root when doing a ceedling:create .

```bash
ceed_here() { docker run --user $(id -u):$(id -g) -it --rm -v $(pwd):/project bd2357/ceedling_withgdb; }
```

## Basic Articles Discussing Unit Testing
  * This docker image uses Ceedling to build "native" code as described [here](http://www.throwtheswitch.org/build/which)
  * For additional help and tips for building native tests, read [this](http://www.throwtheswitch.org/build/native)
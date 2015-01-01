Arch Linux based OpenWrt Buildroot
==================================

This is an Arch Linux based docker container for the OpenWrt buildroot.

Derived from [noonien](https://github.com/noonien/docker-openwrt-buildroot)

Because the build system requires that its commands are not executed by root, the user openwrt was created. 
The buildroot can be found in /home/openwrt/openwrt.

## Installation
### Clone this repository
```sh
git clone https://github.com/jannispinter/arch-openwrt-buildroot.git
```
### Build the docker image
```sh
cd arch-openwrt-buildroot
docker build -t="arch-openwrt-buildroot:trunk" .
```

The dot at the end indicates that =docker build= will use the current directory to find the `Dockerfile`.

## Usage
### 1. Run the docker image
```sh
docker run -i -t arch-openwrt-buildroot:trunk
```
### 2. You might want to install all the feeds
```sh
./scripts/feeds install -a
```

### 3. Configure your OpenWrt image

```sh
make menuconfig
```
Follow the official OpenWrt Buildroot instructions: http://wiki.openwrt.org/doc/howto/build

### Copy OpenWrt images to host system
You can use `docker cp` to copy the binary image out of the container to your host system.
```sh
docker cp <containerId>:/home/openwrt/openwrt/bin/<arch>/<imagefile.bin> /host/path/target
```


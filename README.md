# termux-nginx-rtmp

This is an `nginx` build for Termux that includes `nginx-rtmp-module`.

## Pre-Requirements
+ libssl
+ termux-services
```sh
apt install termux-services
```

## Installation

```sh
apt remove nginx # remove any existing nginx installation.
echo "deb [trusted=yes] https://moo-the-cow.github.io/termux-nginx-rtmp/ termux extras" > $PREFIX/etc/apt/sources.list.d/nginx-rtmp.list
apt update
apt install nginx-rtmp
```

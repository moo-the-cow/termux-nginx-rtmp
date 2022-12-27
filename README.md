# termux-nginx-rtmp

This is an `nginx` build for Termux that includes `nginx-rtmp-module`.

## Pre-Requirements
+ termux-services
+ openssl-1.1 (legacy)
```sh
apt install termux-services openssl-1.1
ln -s $PREFIX/lib/openssl-1.1/libssl.so.1.1 $PREFIX/lib/libssl.so.1.1
ln -s $PREFIX/lib/openssl-1.1/libcrypto.so.1.1 $PREFIX/lib/libcrypto.so.1.1
```

## Installation

```sh
apt remove nginx # remove any existing nginx installation.
echo "deb [trusted=yes] https://moo-the-cow.github.io/termux-nginx-rtmp/ termux extras" > $PREFIX/etc/apt/sources.list.d/nginx-rtmp.list
apt update
apt install nginx-rtmp
```

# Tweak nginx.conf
```sh
curl wget https://raw.githubusercontent.com/moo-the-cow/streaming/main/mobile-streaming/nginx.conf > $PREFIX/etc/nginx/nginx.conf
```

## Enable and Start Service
```sh
sv-enable nginx
sv up nginx
```

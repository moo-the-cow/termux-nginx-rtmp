# termux-nginx-rtmp

This is an `nginx` build for Termux that includes `nginx-rtmp-module`.

## Pre-Requirements
+ termux from f-droid repo (google play is outdated)
+ termux-services
+ openssl-1.1 (legacy)
+ gettext (to inject env variables into nginx config)
```sh
apt install termux-services openssl-1.1 gettext
ln -s $PREFIX/lib/openssl-1.1/libssl.so.1.1 $PREFIX/lib/libssl.so.1.1
ln -s $PREFIX/lib/openssl-1.1/libcrypto.so.1.1 $PREFIX/lib/libcrypto.so.1.1
```

## Installation

```sh
apt remove nginx # remove any existing nginx installation.
mkdir -p $PREFIX/etc/apt/sources.list.d
echo "deb [trusted=yes] https://moo-the-cow.github.io/termux-nginx-rtmp/ termux extras" > $PREFIX/etc/apt/sources.list.d/nginx-rtmp.list
apt update
apt install nginx-rtmp
```

# Tweak nginx.conf
```sh
curl https://raw.githubusercontent.com/moo-the-cow/termux-nginx-rtmp/main/nginx-custom.conf > $PREFIX/etc/nginx/nginx.conf.template
envsubst < $PREFIX/etc/nginx/nginx.conf.template > $PREFIX/etc/nginx/nginx.conf
mkdir -p $PREFIX/www/static/ && curl https://raw.githubusercontent.com/moo-the-cow/termux-nginx-rtmp/main/stat.xsl > $PREFIX/www/static/stat.xsl
```

## Enable and Start Service
```sh
sv-enable nginx
sv up nginx
```
Hint: first time I had to restart the phone and then it worked

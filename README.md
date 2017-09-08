# NGINX + PHP-FPM Demo

Quick demo of NGINX and PHP-FPM created using docker-compose,

I was recently upgrading an out dated NGINX docker container. The container was based on Ubuntu Trusty and when using `apt-get` to install NGINX would result in version 1.4.6 being installed.

Attempting to use the official NGINX v1.13.5 docker container resulted in me getting a white screen of death.

Tried even upgrading my own image by changing the base image to Ubuntu Xenial, same result.

By going back to basics with this simply demo, I established that older versions of NGINX have the fastcig_param for "SCRIPT_FILENAME" defined in `/etc/nginx/fastcgi_params`. Newer versions do not, and you must specify it yourself.

A sample value would be:
```
fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
include fastcgi_params;
```

If nothing else, it serves as a simple starting point for debugging.

To get it running, simple clone this repo then:

```bash
$ docker-compose -p demo build
$ docker-compose -p demo up -d
```

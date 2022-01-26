# nginx-docker-secure

Jenkins project for building new NGINX dockerimage with extra modules like **headers-more** module. Using original NGINX docker image and UBI8 NGINX image.
Read the **Dockerfile** for how they are build. 

Use of **nginx/nginx.conf** and **nginx/default.conf** as an example. Works in most cases.

## nginx-stable-alpine branch

This one uses the dockerimage from NGINX, version stable-alpine

## ubi8-nginx-120 branch

This one uses the dockerimage from Redhat, UBI8 nginx-120

## extra modules

* [headers_more](https://github.com/openresty/headers-more-nginx-module) => needed for remove "nginx" from header

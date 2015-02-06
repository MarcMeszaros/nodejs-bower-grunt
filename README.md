## Node.js w/ Bower & Grunt Dockerfile


This repository contains **Dockerfile** of [Node.js](http://nodejs.org/) w/ [Bower](http://bower.io/) & [Grunt](http://gruntjs.com/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/nodejs-bower-grunt/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [dockerfile/nodejs](http://dockerfile.github.io/#/nodejs)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/dockerfile/nodejs-bower-grunt/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull dockerfile/nodejs-bower-grunt`

   (alternatively, you can build an image from Dockerfile: `docker build -t="dockerfile/nodejs-bower-grunt" github.com/dockerfile/nodejs-bower-grunt`)


### Usage

    docker run -it --rm dockerfile/nodejs-bower-grunt

#### Run `node`

    docker run -it --rm dockerfile/nodejs-bower-grunt node

#### Run `npm`

    docker run -it --rm dockerfile/nodejs-bower-grunt npm

#### Run `bower`

    docker run -it --rm dockerfile/nodejs-bower-grunt bower

#### Run `grunt`

    docker run -it --rm dockerfile/nodejs-bower-grunt grunt

### Volume

You can mount a volume if you would like to output the results of a command back to your local disk. This is useful if you want to share the output of your commands with another container via a shared mounted volume.

    // install grunt-contrib-watch to volume, then use it to watch for changes to the files specified in your Gruntfile
    docker run -it --rm -v <local_path>:/data dockerfile/nodejs-bower-grunt npm install grunt-contrib-watch --save-dev
    docker run -it --rm -v <local_path>:/data dockerfile/nodejs-bower-grunt grunt watch

    // your custom app container that needs assets to be regenerated as you edit
    docker run -it --rm -v <local_path>:<your_custom_mount_point> <your_custom_container> <your_run_cmd>
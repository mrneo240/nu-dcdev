# A Docker Image for Dreamcast Development

[![](https://images.microbadger.com/badges/image/haydenkow/nu-dcdev.svg)](https://microbadger.com/images/haydenkow/nu-dcdev)
[![](https://img.shields.io/docker/pulls/haydenkow/nu-dcdev.svg?maxAge=604800)](https://hub.docker.com/r/haydenkow/nu-dcdev/)

Cross-compile your Dreamcast homebrew projects inside a Docker container based on [KallistiOS](https://github.com/pspdev/psptoolchain).

## Quick Start

Run this command in your project's root folder to build it inside a Docker container:

```bash
docker run --rm -v "$PWD:/src" haydenkow/nu-pspdc make
```

This will mount the current folder to `/src` in the container and then run `make` inside `/src`. You may execute other commands, of course.

Omit the command to get a login shell (`/bin/bash`) in the running container:

```bash
docker run -it --rm -v "$PWD:/src" haydenkow/nu-dcdev
```

## Continuous Integration

With the Docker image in hand, you can also build and test your Dreamcast applications on CI platforms. Here's an example configuration for Travis CI:

```yaml
# .travis.yml
language: c

sudo: required

services:
  - docker

script: docker run  --rm -v "$PWD:/src" haydenkow/nu-dcdev make test
```

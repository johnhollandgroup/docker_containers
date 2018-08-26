# docker_containers

Please check out the different branches. This repository is used for automatic builds of docker images on docker Hub.

Check [https://hub.docker.com/u/davidobrien/](https://hub.docker.com/u/davidobrien/) for more info.

## alpine_azure_tools

This image builds

* alpine linux
  * Azure `az` cli
    * requires `bash` and `python`
  * `terraform`
  * `helm`
  * `kubectl` for Kubernetes k8s

Likely one of the smallest toolset images for Azure you might come across.
# Packer in Docker

This Dockerfile is used to build a docker image containing the following applications:

* CentOS
* boto
* [packer](http://packer.io) - currently version 1.0.2
* latest AWS CLI
* Microsoft PowerShell v6.0.0-beta.1
* AWSPowerShell dotnetCore PowerShell module

## local build

You can clone this repository locally and build the docker image on your own machine. You just need a local docker client for your OS.

`docker build -t packer-on-centos .`

This will build a docker image called `packer-on-centos` from the `Dockerfile`.

## docker hub

This image is also available on the Docker Hub and can be run by calling
`docker run -it davidobrien/centos_packer powershell`
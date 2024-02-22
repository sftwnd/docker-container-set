# Centos latest

Centos container based on centos:latest docker hub container

## Container changes

* yum repository changed
* man pages installed
* langpack installed
* curl installed
* wget installed
* sudo installed

## User changes

* User is named as host os user
* User id likes os user id
* User group id likes os user group
* User is in sudoers
* User password is empty
* Root password is empty
* PS1 is defined

## Mounts

* _**~/Desktop**_: this path will be access point to your Desktop
* _**~/Documents**_: this path will be access point to your Document

## Usage

### Link as binary

_**./centos link**_: link centos as /usr/local/bin/centos
_**./centos unlink**_: unlink centos from /usr/local/bin/centos

### Run linux in container

_**./centos**_: run centos container and save it on exit
_**./centos --rm**_: run centos container and remove it on exit

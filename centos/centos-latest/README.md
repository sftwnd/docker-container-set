# Centos latest

Centos container based on centos:latest docker hub container

## Container changes

* yum repository changed
* man pages installed
* langpack installed
* yum-utils
* passwd
* sudo
* curl installed
* wget installed
* sudo installed
* openssh client/server
* ftp
* rsync
* zip/unzip
* nano
* vim
* curl
* libGL

## User changes

* User is named as host os user
* User id likes os user id
* User group id likes os user group
* User is in sudoers
* User password is empty
* Root password is empty
* PS1 is defined
* ssh keys installed in user and root home

## Mounts

* _**~/Desktop**_: this path will be access point to your Desktop
* _**~/Documents**_: this path will be access point to your Document
* _**~/Work**_: in the case of -cw flag current path will be mounted to ~/Work
* _**/tmp/.X11-unix**_: to use X11


## Usage

### Link as binary

* _**./centos link**_: link centos as /usr/local/bin/centos   
* _**./centos unlink**_: unlink centos from /usr/local/bin/centos

### Run/Start linux in container

* _**./centos [-p|--persistent]**_: run centos container and save it on exit  
* _**./centos**_: run centos container and remove it on exit    
* _**./centos** ... -cw**_: run centos container, mount current folder to ~/Work and set ~/Work as workdir

### Remove linux in container

* _**./centos [rm|rmi]**_: remove image and container (if stopped)  
* _**./centos [rmc]**_: remove container (if stopped)  
* _**./centos [rm|rmi|rmc] [-f|--force]**_: force stop and remove

## F.Y.I.

* You have to enable X11 connect to host server before start X11 application: _**xhost +**_

## Use ssh to host login

* _**ssh** docker.for.mac.host.internal_ or _**ssh** host.docker.internal_ _(Depends on host alias support in docker)_

## Start FireFox

* install firefox by: _**sudo yum install -y firefox**_
* run _**xhost +**_ on host os
* start firefox: _**firefox**_ or _** firefox >**/dev/null 2**>**/dev/null **&**_

## Use Subline text

* _**sudo rpm** -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg_
* _**sudo yum-config-manager** --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo_
* _**sudo yum install** -y **sublime-text**_
* run _**xhost +**_ on host os
* _**subl**_

ARG VERSION=latest
FROM centos:${VERSION}
ARG USERNAME=linux
ARG USERID=501
ARG GROUPNAME=staff
ARG GROUPID=20
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* \
 && sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* \
 && yum install -y man-pages man-db man glibc-langpack-en glibc-langpack-ru passwd openssh-clients openssh-server ftp rsync zip nano vim unzip curl wget sudo \
 && yum clean all \
 && usermod -p "" root \
 && groupadd -g 20 -f ${GROUPNAME} \
 && useradd -m -d /home/${USERNAME} -u ${USERID} -g ${GROUPID} ${USERNAME} \
 && usermod -aG wheel -p "" ${USERNAME} \
 && echo ${USERNAME} ALL=\(ALL:ALL\) ALL >> /etc/sudoers \
 && echo "export PS1='\[\e[0;33m\]\u\[\e[0m\]@\[\e[0;32m\]\h\[\e[0m\]:\[\e[0;34m\]\w\[\e[0m\]\$ '" >> /home/${USERNAME}/.bashrc \
 && echo "export PS1='\[\e[0;32m\]\h\[\e[0m\]:\[\e[0;34m\]\w\[\e[0m\]# '" >> /root/.bashrc \
 && ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' \
 && ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key -N '' \
 && ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N '' \
 && ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N '' \
 && rm -rf /tmp/*
ENV LOCALE=en_RU.UTF-8
USER ${USERNAME}
WORKDIR /home/${USERNAME}
EXPOSE 22 80 8080

ARG VERSION=latest
FROM centos:${VERSION}
ARG USERNAME=linux
ARG USERID=501
ARG GROUPNAME=staff
ARG GROUPID=20
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* \
 && sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* \
 && yum install -y man-pages man-db man glibc-langpack-en glibc-langpack-ru passwd openssh-clients openssh-server ftp rsync zip nano vim unzip curl wget sudo libGL \
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
 && dbus-uuidgen > /var/lib/dbus/machine-id \
 && ssh-keygen -t ed25519 -b 4096 -C "${USERNAME}@centos-linux" -f /tmp/id_ed25519 -N '' \ 
 && mkdir "/home/${USERNAME}/.ssh" \
 && mv /tmp/id_ed25519 "/home/${USERNAME}/.ssh" \ 
 && chmod -R 700 "/home/${USERNAME}/.ssh" \
 && chown -R $USERID:$GROUPID "/home/${USERNAME}/.ssh" \
 && ssh-keygen -t ed25519 -b 4096 -C "root@centos-linux" -f ~/.ssh/id_ed25519 -N '' \ 
 && rm -rf /tmp/*
ENV LOCALE=en_RU.UTF-8
# gateway.docker.internal, docker.for.mac.host.internal, host.docker.internal , docker.for.mac.host.internal, docker.for.mac.localhost
ENV DISPLAY=docker.for.mac.host.internal:0
USER ${USERNAME}
WORKDIR /home/${USERNAME}
EXPOSE 22 80 8080

# root password:    unifield
# docker user:      docker
# docker password:  docker
# psql user:        docker
# psqlpassword:     docker
#
FROM ubuntu:10.04

MAINTAINER Vincent GREINER, vg@tempo-consulting.fr

# get noninteractive frontend for Debian to avoid some problems:
#    debconf: unable to initialize frontend: Dialog
ENV DEBIAN_FRONTEND noninteractive


# UTF-8 locale
RUN locale-gen en_US.UTF-8
RUN echo 'LANG="en_US.UTF-8"' > /etc/default/locale
ENV LANGUAGE en_US.UTF-8
ENV LANG en_US:en
ENV LC_ALL en_US.UTF-8

# OVH mirror list to update Ubuntu 10.04 to the last version.
# WARNING: Use of udev hold and initscripts hold and upstart hold will prevent:
#    dpkg: error processing udev
#    mount: permission denied
RUN echo "deb http://mirror.ovh.net/ubuntu lucid main restricted" > /etc/apt/sources.list; \
 echo "deb http://mirror.ovh.net/ubuntu/ lucid-updates main restricted" >> /etc/apt/sources.list; \
 echo "deb http://mirror.ovh.net/ubuntu/ lucid multiverse" >> /etc/apt/sources.list; \
 echo "deb http://mirror.ovh.net/ubuntu/ lucid-updates multiverse" >> /etc/apt/sources.list; \
 echo "deb http://mirror.ovh.net/ubuntu/ lucid universe" >> /etc/apt/sources.list; \
 echo "deb http://mirror.ovh.net/ubuntu/ lucid-updates universe" >> /etc/apt/sources.list; \
 echo udev hold | dpkg --set-selections; \
 echo initscripts hold | dpkg --set-selections; \
 echo upstart hold | dpkg --set-selections; \
 apt-get update; \
 apt-get upgrade -y
 
# base packages
RUN apt-get install -y \
    nano \
    tree \
    vim

# USERS
RUN echo 'root:unifield' |chpasswd  # change default root password
RUN useradd -m docker # docker user with home directory (-m option)
RUN echo "docker:docker" | chpasswd  # change default docker password
USER docker
COPY vimrc /home/docker/.vimrc
WORKDIR /home/docker


CMD [ "/bin/bash" ]

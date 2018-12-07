FROM centos:latest
MAINTAINER soops@ucla.edu

RUN yum update -y

# basic tools to make using docker livable
RUN yum install -y man wget git less netutils net-tools openssh-server openssh-clients initscripts sudo chkconfig tar

# add use case specific packages here

# EXPOSE ports here as needed

# replace systemctl to work around dbus issue
RUN git clone https://github.com/gdraheim/docker-systemctl-images.git
RUN cp docker-systemctl-images/files/docker/systemctl.py /bin/systemctl
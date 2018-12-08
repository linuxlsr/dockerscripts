FROM soops/centos6base
MAINTAINER soops@ucla.edu

WORKDIR /root
RUN yum install -y freeradius freeradius-mysql freeradius-utils mysql-server

CMD service radiusd start

EXPOSE 1812/udp
EXPOSE 1813/udp
EXPOSE 1645/udp
EXPOSE 1646/udp
EXPOSE 1812/tcp
EXPOSE 1813/tcp
EXPOSE 1645/tcp
EXPOSE 1646/tcp
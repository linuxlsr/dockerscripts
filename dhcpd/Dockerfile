FROM soops/centosbase
MAINTAINER soops@ucla.edu

WORKDIR /root
RUN yum install -y dhcp

CMD service dhcpd start

EXPOSE 67/udp
EXPOSE 68/udp
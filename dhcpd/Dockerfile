FROM soops/centosbase
MAINTAINER soops@ucla.edu

WORKDIR /root
RUN yum update -y && install -y dhcp

EXPOSE 67/udp
EXPOSE 68/udp

ENTRYPOINT ['/usr/sbin/dhcpd -4 -f -d --no-pid -cf "/etc/dhcp/dhcpd.conf" -lf "/etc/dhcp/dhcpd.leases" eth0']
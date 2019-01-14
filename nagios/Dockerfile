FROM soops/centosbase
MAINTAINER soops@ucla.edu

# from: https://support.nagios.com/kb/article/nagios-core-installing-nagios-core-from-source-96.html#CentOS

WORKDIR /root
RUN yum install -y gcc make unzip glibc glibc-common httpd php gd gd-devel perl postfix
RUN wget -O /root/nagioscore.tar.gz https://github.com/NagiosEnterprises/nagioscore/archive/nagios-4.4.1.tar.gz
RUN ls -al
RUN tar -zxvf /root/nagioscore.tar.gz
WORKDIR /root/nagioscore-nagios-4.4.1
RUN ./configure
RUN make all
RUN make install-groups-users
RUN usermod -a -G nagios apache
RUN make install
RUN make install-daemoninit
RUN chkconfig --level 2345 httpd on
RUN make install-commandmode
RUN make install-config
RUN make install-webconf

# adds nagiosadmin:password
RUN echo "nagiosadmin:\$apr1\$k.dy5xrT\$QUbNRLhX01U4tTvt6r8hd1" > /usr/local/nagios/etc/htpasswd.users  

# these are not working, add service start commands to docker run command?
#CMD systemctl restart httpd & 
#CMD systemctl restart nagios & 

#plugin installation
WORKDIR /tmp
RUN yum install -y gcc glibc glibc-common make gettext automake autoconf wget openssl-devel net-snmp net-snmp-utils epel-release
RUN yum install -y perl-Net-SNMP

# adding dev tools because "no gnu make" error
#RUN yum group install "Development Tools"
RUN yum install -y which
RUN wget --no-check-certificate -O nagios-plugins.tar.gz https://github.com/nagios-plugins/nagios-plugins/archive/release-2.2.1.tar.gz

RUN tar zxf nagios-plugins.tar.gz
RUN cd /tmp/nagios-plugins-release-2.2.1/

WORKDIR /tmp/nagios-plugins-release-2.2.1
RUN ./tools/setup
RUN ./configure
RUN make
RUN make install
#RUN systemctl start httpd &
#RUN systemctl start nagios &

EXPOSE 80


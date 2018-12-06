FROM soops/centosbase
MAINTAINER soops@ucla.edu

RUN yum install -y gcc make unzip glibc glibc-common httpd php gd gd-devel perl postfix

RUN wget -O /root/nagioscore.tar.gz https://github.com/NagiosEnterprises/nagioscore/archive/nagios-4.4.1.tar.gz
RUN tar zxv /root/nagios.tar.gz
RUN cd /root/nagioscore-nagios-4.4.1
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
RUN firewall-cmd --zone=public --add-port=80/tcp
RUN firewall-cmd --zone=public --add-port=80/tcp --permanent
# need to run at cli to set up user. htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
RUN service httpd start
run service nagios start

EXPOSE 80


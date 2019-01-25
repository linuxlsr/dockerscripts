FROM ubuntu

LABEL maintainer="soops@ucla.edu"

run apt-get update -y && apt-get install mysql-server net-tools openjdk-8-jdk -y

CMD service start mysql
CMD mysqladmin -uroot create jamfsoftware

WORKDIR /root

COPY jamfproinstaller.run /root/jamfproinstaller.run

CMD chmod 755 /root/jamfproinstaller.run



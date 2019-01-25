FROM centos

LABEL maintainer="soops@ucla.edu"

# basic tools plus ansible
RUN yum install -y epel-release man python-pip wget gzip unzip git tar ansible
WORKDIR /root

# install jenkins
RUN yum install -y java-1.8.0-openjdk-devel 
RUN wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
RUN rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
RUN yum update -y
RUN yum install -y jenkins 
#update to latest jenkins
RUN wget http://updates.jenkins-ci.org/download/war/latest/jenkins.war -O /var/lib/jenkins/jenkins.war

# install terraform
WORKDIR /tmp
RUN wget https://releases.hashicorp.com/terraform/0.11.11/terraform_0.11.11_linux_amd64.zip && unzip terraform_0.11.11_linux_amd64.zip && mv terraform /usr/bin/terraform

# install awscli
RUN wget https://s3.amazonaws.com/aws-cli/awscli-bundle.zip && unzip awscli-bundle.zip && python awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws

# install docker
RUN yum install openssh-server net-tools yum-utils device-mapper-persistent-data -y
RUN yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
RUN yum update -y
RUN yum install docker-ce -y
RUN usermod -aG docker jenkins


#ENTRYPOINT [ "exec java -jar /usr/lib/jenkins/jenkins.war"]
#RUN cat /root/.jenkins/secrets/initialAdminPassword
FROM centos

LABEL maintainer="soops@ucla.edu"

RUN yum install -y epel-release man python-pip wget gzip unzip git tar 
WORKDIR /root

# install jenkins
RUN yum install -y java-1.8.0-openjdk-devel 
RUN wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
RUN rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
RUN yum update -y
RUN yum install -y jenkins && systemctl enable jenkins

# install terraform
RUN wget https://releases.hashicorp.com/terraform/0.11.11/terraform_0.11.11_linux_amd64.zip && unzip terraform_0.11.11_linux_amd64.zip && mv terraform /usr/bin/terraform

# install awscli
RUN wget https://s3.amazonaws.com/aws-cli/awscli-bundle.zip && unzip awscli-bundle.zip && python awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws

ENTRYPOINT [ "systemctl start jenkins" ]
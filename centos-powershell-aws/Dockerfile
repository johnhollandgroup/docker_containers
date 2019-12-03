FROM centos:latest

RUN yum -y update && yum -y install epel-release && yum -y groupinstall "Development Tools"
RUN yum -y install python3-pip && pip3 install --upgrade pip && pip install awscli boto3

RUN curl https://packages.microsoft.com/config/rhel/7/prod.repo | tee /etc/yum.repos.d/microsoft.repo
RUN yum install -y powershell

RUN pwsh -command "Install-Module -Name AwsPowerShell.NetCore -Force -Verbose"

# Install Node
RUN curl -sL https://rpm.nodesource.com/setup_10.x | bash -
RUN yum install -y nodejs

# Install Ansible
RUN yum -y install ansible which
RUN pip3.6 install --upgrade pip && pip3.6 install boto3
RUN ln -s $(which python3.6) /usr/local/bin/python3
RUN ln -s $(which python3.6) /usr/local/bin/python

# Install SAM Local
RUN pip3.6 install aws-sam-cli

RUN yum clean packages && yum clean all

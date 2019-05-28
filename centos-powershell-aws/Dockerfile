FROM centos:latest

RUN yum -y update && yum -y install epel-release && yum -y groupinstall "Development Tools"
RUN yum -y install python-pip && pip install --upgrade pip && pip install awscli boto3

# Change this URL to the exact version you want to install
ENV POWERSHELL_DOWNLOAD_URL https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-beta.1/powershell-6.0.0_beta.1-1.el7.centos.x86_64.rpm
RUN curl -L $POWERSHELL_DOWNLOAD_URL --output powershell_linux.rpm
RUN yum -y install powershell_linux.rpm https://centos7.iuscommunity.org/ius-release.rpm
RUN rm powershell_linux.rpm --force
RUN powershell -command "Install-Module -Name AwsPowerShell.NetCore -Force -Verbose"

# Install Node
RUN curl -sL https://rpm.nodesource.com/setup_10.x | bash -
RUN yum install -y nodejs

# Install Ansible
RUN yum -y install ansible which python36u python36u-libs python36u-devel python36u-pip
RUN pip3.6 install --upgrade pip && pip3.6 install boto3
RUN ln -s $(which python3.6) /usr/local/bin/python3

RUN yum clean packages && yum clean all
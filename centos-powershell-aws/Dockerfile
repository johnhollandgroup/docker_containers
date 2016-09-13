From centos:latest

RUN yum install -y epel-release
RUN yum update -y
RUN yum -y install python-pip
RUN yum group install -y "Development Tools"
RUN pip install --upgrade pip
RUN pip install awscli
RUN pip install boto
RUN rpm -ivh https://github.com/Versent/unicreds/releases/download/v1.5.0/unicreds-1.5.0_1.rpm
# Change this URL to the exact version you want to install
ENV POWERSHELL_DOWNLOAD_URL https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-alpha.9/powershell-6.0.0_alpha.9-1.el7.centos.x86_64.rpm

RUN curl -L $POWERSHELL_DOWNLOAD_URL --output powershell_linux.rpm
RUN yum -y install powershell_linux.rpm
RUN git clone https://github.com/PowerShell/PowerShell.git
RUN mv PowerShell/src/Modules/Shared/PowerShellGet/PSModule.psm1 /opt/microsoft/powershell/6.0.0-alpha.9/Modules/PowerShellGet/PSModule.psm1
RUN rm -rf PowerShell
RUN rm powershell_linux.rpm --force
RUN powershell -command "Install-Module -Name AwsPowerShell.NetCore -Force -Verbose"
RUN yum clean packages
RUN yum clean all
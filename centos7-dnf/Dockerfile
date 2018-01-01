FROM centos:centos7
MAINTAINER Alexander Usov

ENV HOME=/usr/local/src/dnf

RUN yum clean all && \
    yum -y install epel-release @'Development Tools' git && \
    mkdir ${HOME}

WORKDIR ${HOME}

RUN git clone -b maint-epel7 https://github.com/rpm-software-management/dnf.git ${HOME} && \
    yum-builddep -y dnf.spec && \
    cmake . && \
    make 

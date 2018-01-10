FROM centos:centos7
MAINTAINER Alexander Usov

RUN yum -y update && \
    yum -y install epel-release && \
    yum -y install @'Development Tools' Lmod python-setuptools which && \
    useradd eb -m

ENV EASYBUILD_PREFIX /home/eb/.local/easybuild

USER eb
WORKDIR /home/eb/

# install EasyBuild
RUN curl -O https://raw.githubusercontent.com/easybuilders/easybuild-framework/develop/easybuild/scripts/bootstrap_eb.py && \
    source /usr/share/lmod/lmod/init/profile && \
    python bootstrap_eb.py $EASYBUILD_PREFIX && \
    module use $EASYBUILD_PREFIX/modules/all && \
    module load EasyBuild && \
    echo -e ". /usr/share/lmod/lmod/init/profile\nmodule use /home/eb/.local/easybuild/modules/all\nmodule load EasyBuild" > ~/.bashrc

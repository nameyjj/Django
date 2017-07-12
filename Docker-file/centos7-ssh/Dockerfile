FROM centos:centos7
MAINTAINER Feng Honglin <hfeng@tutum.co>
RUN rm -f /etc/yum.repos.d/*
ADD ql-oa-el7.repo /etc/yum.repos.d/ql-oa-el7.repo
RUN yum -y install openssh-server epel-release && \
    yum -y install pwgen && \
    rm -f /etc/ssh/ssh_host_dsa_key /etc/ssh/ssh_host_rsa_key && \
    ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key && \
    ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key && \
    sed -i "s/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && \
    sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config
RUN echo "root:chengce.1" | chpasswd
#ADD set_root_pw.sh /set_root_pw.sh
#ADD run.sh /run.sh
#RUN chmod +x /*.sh

#ENV AUTHORIZED_KEYS **None**

EXPOSE 22
#CMD ["/run.sh"]
CMD ["/usr/sbin/sshd","-D"]

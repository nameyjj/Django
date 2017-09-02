FROM centos:centos7
MAINTAINER Yang <nameyjj@gmail.com>
RUN rm -f /etc/yum.repos.d/*
ADD base-epel.repo /etc/yum.repos.d/base-epel.repo
RUN yum -y install openssh-server  && \
    yum -y install pwgen && \
    rm -f /etc/ssh/ssh_host_dsa_key /etc/ssh/ssh_host_rsa_key && \
    ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key && \
    ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key && \
    sed -i "s/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && \
    sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config
RUN echo "root:chengce321dedewewdw23re" | chpasswd
COPY authorized_keys /root/.ssh/authorized_keys
RUN chmod 644 /root/.ssh/authorized_keys
#ADD set_root_pw.sh /set_root_pw.sh
#ADD run.sh /run.sh
#RUN chmod +x /*.sh

#ENV AUTHORIZED_KEYS **None**

EXPOSE 22
#CMD ["/run.sh"]
CMD ["/usr/sbin/sshd","-D"]

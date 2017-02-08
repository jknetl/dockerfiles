FROM centos:7

# install java and ssh server
RUN yum -y update && \
    yum -y install openssh-server openssh-clients && \
    yum -y install sudo && \
    yum -y install vim && \
    yum -y clean all

# generate ssh keys
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' && \
    ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N '' && \
    ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N ''

# add centos user with no password and sudo privileges
RUN useradd centos && echo centos: | chpasswd ; usermod -aG wheel centos

# enabling passwordless ssh login, sudo without password, and sudo over ssh
RUN echo '%wheel ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers && \
    sed -i 's/.*requiretty$/Defaults !requiretty/' /etc/sudoers && \
    sed -i 's/#PermitEmptyPasswords no/PermitEmptyPasswords yes/;s/#UseDNS yes/UseDNS no/' /etc/ssh/sshd_config

# expose ssh and Fuse ports
EXPOSE 22

# run sshd
CMD ["/usr/sbin/sshd", "-D"]


FROM jknetl/centos-ssh:latest

RUN yum -y update && \
    yum -y install java-1.8.0-openjdk-devel && \
    yum -y install maven && \
    yum -y install git && \
    yum -y install unzip && \
    yum -y clean all

# add fuse user
RUN useradd fuse && echo fuse:fuse | chpasswd && usermod -aG wheel fuse

EXPOSE 8101 8181 44444 1099 61616


FROM jknetl/centos-ssh:latest

RUN yum -y update && \
    yum -y install java-1.8.0-openjdk-devel && \
    yum -y install maven && \
    yum -y install git && \
    yum -y clean all

# add hudson user for jenkins
RUN useradd hudson && echo hudson:hudson | chpasswd

# configure git for hudson user
RUN runuser -l hudson -c "git config --global user.email hudson@docker-host"
RUN runuser -l hudson -c "git config --global user.name Hudson Localhost"
RUN runuser -l hudson -c "git config --global http.sslVerify false"

FROM jknetl/fuse-base:latest

ADD fuse.zip /home/fuse/
RUN unzip -d /home/fuse/tmp /home/fuse/fuse.zip && \
    mv /home/fuse/tmp/jboss-fuse-* /home/fuse/fuse && \
    echo "admin=admin,admin,manager,viewer,Monitor, Operator, Maintainer, Deployer, Auditor, Administrator, SuperUser" >> /home/fuse/fuse/etc/users.properties && \
    chown fuse:fuse -cR /home/fuse/fuse

CMD /bin/bash -c 'runuser -l fuse -c "/home/fuse/fuse/bin/start" ; /usr/sbin/sshd -D'

EXPOSE 2181

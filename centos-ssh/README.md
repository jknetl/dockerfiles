# centos-ssh image 

This image provides centos environment with sshd enabled. You can launch a container using:

    docker run -d jknetl/centos-ssh

If you want to log in into container using sshd service you may use _centos_ user with empty password:

    # replace <ip-address-of-container> with address assigned by docker
    ssh centos@<ip-address-of-container>

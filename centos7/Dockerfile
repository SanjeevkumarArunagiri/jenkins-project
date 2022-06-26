FROM centos

RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-Linux-*

RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-Linux-*

RUN yum -y install openssh-server

RUN yum install -y passwd

RUN useradd remote_user && \
    echo "1234" | passwd remote_user --stdin && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY remote-key.pub /home/remote_user/.ssh/authorised_keys

RUN chown remote_user:remote_user -R /home/remote_user/.ssh/ && \
    chmod 600 /home/remote_user/.ssh/authorised_keys

RUN ssh-keygen -A

RUN yum -y install mysql

RUN yum install -y python3

RUN curl -O https://bootstrap.pypa.io/pip/3.6/get-pip.py && \
    python3 get-pip.py && \
    yum update -y && \
    pip3 install awscli --upgrade

EXPOSE 22

RUN rm -rf /run/nologin

CMD /usr/sbin/sshd -D

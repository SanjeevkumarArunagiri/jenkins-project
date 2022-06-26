FROM jenkins/jenkins
USER root
RUN apt-get update -y
RUN apt-get install -y python3
RUN apt-get install -y python3-distutils
RUN apt-get install -y python3-apt
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py && \
    pip3 install ansible --upgrade
RUN apt-get install sshpass
RUN apt-get update && apt-get install -y iputils-ping

# FROM jenkins/jenkins
# USER root
# RUN apt-get update && apt-get -y install ansible

USER jenkins

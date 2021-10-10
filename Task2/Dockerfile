#Base image that was chosen. Probably not the most interesting one
FROM ubuntu:16.04

#Install necessary packages
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd

#Add a new user so that root user need not be used
RUN useradd -m -s /bin/bash sshuser
RUN echo 'sshuser:sshtask' | chpasswd
RUN sed -i 's/PeritRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

#Services to run after docker container is created
ENTRYPOINT service ssh start && bash

#SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

#Expose SSH Port
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]


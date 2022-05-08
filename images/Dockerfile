FROM ubuntu:latest
RUN apt update && apt install openssh-server sudo nano net-tools iputils-ping dnsutils ufw gnupg -y
COPY ./keys /root/keys
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
RUN sed -i 's/#PubkeyAuthentication yes/PubkeyAuthentication yes/g' /etc/ssh/sshd_config
RUN service ssh start
EXPOSE 22
RUN mkdir /root/.ssh
RUN for i in `ls /root/keys`; do cd /root/keys && cat $i >> /root/.ssh/authorized_keys; done;
CMD ["/usr/sbin/sshd","-D"]
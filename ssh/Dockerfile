FROM ubuntu:noble

RUN apt-get update && apt-get install openssh-server -y
RUN useradd -ms /bin/bash carlos
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin no/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config

RUN mkdir /home/carlos/.ssh
COPY keywin.pub /home/carlos/.ssh/authorized_keys

RUN chmod 700 /home/carlos/.ssh
RUN chmod 644 /home/carlos/.ssh/authorized_keys
RUN chown -R carlos:carlos /home/carlos/.ssh

CMD ["sh", "-c", "service ssh start; tail -f /dev/null"]

FROM ubuntu:18.04

ENV ROOT_PASS 'abcd1234'
ENV USER_NAME 'level11'
ENV USER_PASS "level11"
ENV FLAG 'The flag is the root password. Good luck ;)'
ENV TZ=Europe/Paris
ENV DEBIAN_FRONTEND=noninteractive
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update -y
RUN apt-get install -yq tzdata openssh-server sudo php lua5.3 python
RUN mkdir /var/run/sshd
RUN echo "root:${ROOT_PASS}" | chpasswd
RUN useradd -m -d "/home/${USER_NAME}" ${USER_NAME} -s /usr/bin/python
RUN echo "${USER_NAME}:${USER_PASS}" | chpasswd
RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin no/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN mkdir /root/.ssh
RUN echo "root ALL=(ALL) ALL" > /etc/sudoers && \
    echo "${USER_NAME} ALL = (root) NOPASSWD: /bin/cat /home/${USER_NAME}/*" >> /etc/sudoers && \
    echo "" >> /etc/sudoers
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN echo ${FLAG} > /root/flag

RUN mv /bin/bash /bin/.bash
RUN echo "php -a" > /bin/bash && chmod +x /bin/bash

RUN mv /bin/ls /bin/.ls 
RUN echo "cd .. && echo \"Hello Loco !\"" > /bin/ls && chmod +x /bin/ls

RUN mv /usr/bin/sudo /usr/bin/.sudo 
RUN echo "/usr/bin/lua5.3" > /usr/bin/sudo && chmod +x /usr/bin/sudo

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

FROM centos:7

RUN yum -y install openssh-server
RUN useradd remote_user && \
    echo "1234" | passwd remote_user  --stdin && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY remote-key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user   -R /home/remote_user && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen

RUN yum -y install mysql

RUN yum install gcc openssl-devel bzip2-devel libffi-devel -y

RUN curl -O https://www.python.org/ftp/python/3.8.1/Python-3.8.1.tgz

RUN tar -xzf Python-3.8.1.tgz

RUN cd Python-3.8.1/ && \
    ./configure --enable-optimizations && \
    yum -y install make && \
    make altinstall

RUN python3.8 --version

RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python3.8 get-pip.py && \
    pip3 install awscli --upgrade

RUN yum install -y vim

CMD /usr/sbin/sshd -D

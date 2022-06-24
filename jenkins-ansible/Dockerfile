FROM jenkins/jenkins

USER root

RUN apt update -y 

# RUN apt install -y software-properties-common

RUN apt install -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget

# RUN add-apt-repository -y ppa:deadsnakes/ppa

RUN cd /tmp

RUN wget https://www.python.org/ftp/python/3.8.2/Python-3.8.2.tgz

RUN tar -xf Python-3.8.2.tgz

RUN ls 

# RUN cd Python-3.8.2

# RUN ls 

RUN ./Python-3.8.2/configure --enable-optimizations

RUN apt install -y make

RUN  make install
# RUN apt update 

# RUN apt install -y python3.8

RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python3.8 get-pip.py && \
    pip3 install ansible --upgrade

USER jenkins
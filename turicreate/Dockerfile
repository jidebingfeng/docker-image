FROM       nvidia/cuda:8.0-cudnn5-devel-ubuntu16.04
MAINTAINER zlong "jidebingfeng@126.com"

RUN apt-get update

#### tools
RUN apt-get install -y openssh-server net-tools iputils-ping vim proxychains
RUN mkdir /var/run/sshd

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config


# config proxychains
RUN sed -ri 's/socks4/#socks4/g' /etc/proxychains.conf
RUN echo socks5  127.0.0.1 1080 >> /etc/proxychains.conf


#### turicreate
RUN apt-get install -y python-pip
RUN pip install --upgrade pip
#RUN pip install turicreate

RUN echo export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH >> ~/.bashrc
RUN pip uninstall -y mxnet
RUN pip install mxnet-cu80==1.1.0

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]

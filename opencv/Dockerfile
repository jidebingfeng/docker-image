FROM       valian/docker-python-opencv-ffmpeg:y3-cuda
MAINTAINER zlong "jidebingfeng@126.com"


RUN apt-get install -y openssh-server net-tools iputils-ping curl wget vim proxychains
RUN mkdir /var/run/sshd

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config


# config proxychains
RUN sed -ri 's/socks4/#socks4/g' /etc/proxychains.conf
RUN echo socks5  127.0.0.1 1080 >> /etc/proxychains.conf

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]

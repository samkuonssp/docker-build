## Modified by Sam KUON - 25/07/17
FROM centos:latest
MAINTAINER Sam KUON "sam.kuonssp@gmail.com"

# System timezone
ENV TZ=Asia/Phnom_Penh
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# install main packages:
RUN yum -y install bind-utils bind && \
    yum clean all

ADD conf.d/* /

# set up the BIND env and gen rndc key
RUN rndc-confgen -a -c /etc/rndc.key && \
    chown named:named /etc/rndc.key && \
    chmod 755 /entrypoint.sh

EXPOSE 53/udp 53/tcp

# Volumes:
# this is where all the named data lives
#VOLUME [ "/named" ]

# start services:
ENTRYPOINT [ "/entrypoint.sh"]
CMD [ "/usr/sbin/named" ]

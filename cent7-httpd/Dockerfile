## Modified by Sam KUON - 28/05/17
FROM centos:latest
MAINTAINER Sam KUON "sam.kuonssp@gmail.com"

# System timezone
Env TZ=Asia/Phnom_Penh
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Install HTTP package
RUN yum clean all && \
    yum -y update && \
    yum -y install httpd


# Copy running script
ADD ./conf.d/run-httpd.sh /run-httpd.sh
RUN chmod -v +x /run-httpd.sh

# Open ports
EXPOSE 80

CMD ["/run-httpd.sh"]

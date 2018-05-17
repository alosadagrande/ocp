#FROM registry.access.redhat.com/rhel7
FROM docker.io/centos:7
USER default
MAINTAINER John Doe <jdoe@example.com>
EXPOSE 8080
USER root
#COPY ./training.repo /etc/yum.repos.d/training.repo
RUN yum -y install httpd && yum clean all -y
RUN sed -i 's/Listen 80/Listen 8080/' /etc/httpd/conf/httpd.conf
RUN echo "Bienvenidos al workshop" > /var/www/html/index.html
RUN chmod -R a+rwx /run/httpd /etc/httpd/logs
# OpenShift ignores uid. Image should work with any, that's why rwx above
USER 1001
# should change apache config to log to stdout
EXPOSE 8080
CMD /usr/sbin/httpd -DFOREGROUND

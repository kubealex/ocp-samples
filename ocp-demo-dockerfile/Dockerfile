FROM registry.access.redhat.com/ubi8-minimal

RUN microdnf --nodocs -y install httpd \
  && microdnf clean all

RUN sed -i 's/Listen 80/Listen 8080/' /etc/httpd/conf/httpd.conf \
  && chgrp -R 0 /var/log/httpd /var/run/httpd /etc/httpd/ \
  && chmod -R g=u /var/log/httpd /var/run/httpd /etc/httpd
  
EXPOSE 8080

USER 1001

ENTRYPOINT httpd -D FOREGROUND
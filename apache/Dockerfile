# ./apache/Dockerfile
FROM httpd:2.4.51

COPY web.apache.conf /usr/local/apache2/conf/web.apache.conf

RUN echo "Include /usr/local/apache2/conf/web.apache.conf" \
    >> /usr/local/apache2/conf/httpd.conf
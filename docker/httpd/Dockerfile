FROM httpd:2.4.41-alpine
LABEL maintainer="TSEF ROGER Xavier <xavier.roger@intradef.gouv.fr>"
LABEL name="Apache HTTP 2.4.38" \
      description="Apache HTTP 2.4.38 securisé" \
      vendor="CDADT" \
      version="1.0" \
      schema-version="1.1"

# Add repos
RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories
RUN apk update && apk upgrade
RUN apk add krb5-conf krb5-server krb5 apache-mod-auth-kerb krb5-libs ca-certificates
RUN mkdir /usr/share/ca-certificates/extra
COPY httpd.conf /usr/local/apache2/conf/httpd.conf

# Active des modules et securise le serveur .
RUN sed -i 's@^#LoadModule deflate_module modules/mod_deflate.so@LoadModule deflate_module modules/mod_deflate.so@g' /usr/local/apache2/conf/httpd.conf && \
    sed -i 's@^#LoadModule expires_module modules/mod_expires.so@LoadModule expires_module modules/mod_expires.so@g' /usr/local/apache2/conf/httpd.conf && \
    sed -i 's@^#LoadModule ssl_module modules/mod_ssl.so@LoadModule ssl_module modules/mod_ssl.so@g'                 /usr/local/apache2/conf/httpd.conf && \
    sed -i 's@^#LoadModule rewrite_module modules/mod_rewrite.so@LoadModule rewrite_module modules/mod_rewrite.so@g' /usr/local/apache2/conf/httpd.conf && \
    sed -i 's@^#LoadModule proxy_module modules/mod_proxy.so@LoadModule proxy_module modules/mod_proxy.so@g'         /usr/local/apache2/conf/httpd.conf && \
    sed -i 's@^#LoadModule proxy_http_module modules/mod_proxy_http.so@LoadModule proxy_http_module modules/mod_proxy_http.so@g' /usr/local/apache2/conf/httpd.conf && \
    sed -i 's@^#LoadModule proxy_fcgi_module modules/mod_proxy_fcgi.so@LoadModule proxy_fcgi_module modules/mod_proxy_fcgi.so@g' /usr/local/apache2/conf/httpd.conf && \
    sed -i 's@^#LoadModule socache_shmcb_module modules/mod_socache_shmcb.so@LoadModule socache_shmcb_module modules/mod_socache_shmcb.so@g' /usr/local/apache2/conf/httpd.conf

RUN sed -i 's@Listen 80@Listen 80\nListen 443@g' /usr/local/apache2/conf/httpd.conf

#Custom configuration.
RUN mkdir /usr/local/apache2/conf/conf.d && \
    mkdir /usr/local/apache2/conf/vhost.d && \
    mkdir /usr/local/apache2/conf/ssl && \
  echo 'IncludeOptional conf/conf.d/*.conf' >> /usr/local/apache2/conf/httpd.conf

COPY conf.d /usr/local/apache2/conf/conf.d

EXPOSE 80
EXPOSE 443
#CMD ["/bin/sh","-c","#(nop) ","USER www-data"]

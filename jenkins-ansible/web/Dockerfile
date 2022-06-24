FROM remote-host

COPY ./conf/nginx.repo /etc/yum.repos.d/nginx.repo

RUN                                                                          \
  yum -y install nginx-1.12.2 openssl --enablerepo=nginx                  && \
  yum install https://repo.ius.io/ius-release-el7.rpm https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm -y         

RUN yum search php7

RUN yum -y install                                                          \
    php74-fpm                                                               \
    php74-cli                                                               \
    php74-mysqlnd                                                           \
    php74-soap                                                              \
    php74-xml                                                               \
    php74-zip                                                               \
    php74-json                                                              \
    php74-mcrypt                                                            \
    php74-mbstring                                                          \
    php74-zip                                                               \
    php74-gd                                                                \
     --enablerepo=ius && yum clean all

EXPOSE 80 443

VOLUME /var/www/html /var/log/nginx /var/log/php-fpm /var/lib/php-fpm

COPY ./conf/nginx.conf /etc/nginx/conf.d/default.conf

COPY ./bin/start.sh /start.sh

RUN chmod +x /start.sh

CMD /start.sh


FROM centos:centos7

RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
    rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm && \
    rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

RUN yum -y update

RUN yum install -y libaio \
                   gcc \
                   openssl-devel \
                   git

ADD source/oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm /tmp
ADD source/oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm /tmp

RUN rpm -i /tmp/oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm && \
    rpm -i /tmp/oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm

RUN export LD_LIBRARY_PATH=/usr/lib/oracle/12.1/client64/lib/
RUN export ORACLE_HOME=/usr/lib/oracle/12.1/client64/lib/

ENV LD_LIBRARY_PATH /usr/lib/oracle/12.1/client64/lib/
ENV ORACLE_HOME /usr/lib/oracle/12.1/client64/lib/

RUN yum install -y php56-php-common \
                   php56-php-fpm \
                   php56-php-cli \
                   php56-php-mcrypt \
                   php56-php-mbstring \
                   php56-php-pecl-memcache \
                   php56-php-pecl-memcached \
                   php56-php-gd \
                   php56-php-pecl-zip \
                   php56-php-process \
                   php56-php-soap \
                   php56-php-pecl-stomp \
                   php56-php-pear \
                   php56-php-devel \
                   php56-php-xml \
                   php56-php-pdo \
                   php56-php-oci8 \
                   php56-php-bcmath \
                   php56-php-pecl-xdebug \
                   php56-xhprof

EXPOSE 9000

RUN echo '/opt/remi/php56/root/usr/sbin/php-fpm --nodaemonize' > /tmp/entrypoint.sh

ENTRYPOINT ["sh", "/tmp/entrypoint.sh"]
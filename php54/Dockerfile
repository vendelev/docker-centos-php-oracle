FROM centos:centos7

RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
    rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm && \
    rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

RUN yum -y update

RUN yum install -y libaio \
                   gcc \
                   openssl-devel

ADD source/oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm /tmp
ADD source/oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm /tmp

RUN rpm -i /tmp/oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm && \
    rpm -i /tmp/oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm

ENV LD_LIBRARY_PATH /usr/lib/oracle/12.1/client64/lib/
ENV ORACLE_HOME /usr/lib/oracle/12.1/client64/lib/

RUN yum install -y php54-php-common \
                   php54-php-fpm \
                   php54-php-cli \
                   php54-php-mcrypt \
                   php54-php-mbstring \
                   php54-php-pecl-memcache \
                   php54-php-pecl-memcached \
                   php54-php-gd \
                   php54-php-pecl-zip \
                   php54-php-process \
                   php54-php-soap \
                   php54-php-pecl-stomp \
                   php54-php-pear \
                   php54-php-devel \
                   php54-php-xml \
                   php54-php-pdo \
                   php54-php-oci8

EXPOSE 9000

ENTRYPOINT ["/opt/remi/php54/root/usr/sbin/php-fpm", "--nodaemonize"]
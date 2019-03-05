FROM centos:7

MAINTAINER Bikram (bikram2690@gmail.com)

# Install httpd
RUN yum update -y \
    yum install httpd -y

CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]

EXPOSE 80

# Install PHP 

RUN yum install php php-mysql -y

# Install wordpress
RUN yum install php-gd \
    mkdir /opt/wordpress \
    yum install wget -y
    
WORKDIR /opt/wordpress 

RUN wget http://wordpress.org/latest.tar.gz 
RUN tar -xzvf latest.tar.gz 
RUN mv wordpress/* /var/www/html 
RUN mkdir /var/www/html/wp-content/uploads 
RUN chown -R apache:apache /var/www/html/*


WORKDIR /var/www/html
RUN mv wp-config-sample.php wp-config.php
RUN sed -i "s/database_name_here/wordpress/g" wp-config.php 
RUN sed -i "s/username_here/root/g" wp-config.php 
RUN sed -i "s/password_here/WordPress/g" wp-config.php 
RUN sed -i "s/localhost/172.18.0.2/g" wp-config.php 

CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]


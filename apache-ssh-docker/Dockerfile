FROM ubuntu:16.04

EXPOSE 22 80

RUN apt-get update && apt install -y \
	apache2 \
	openssh-server \
	zip

# create ubuntu user with password
RUN useradd -ms /bin/bash ubuntu \
	&& echo 'ubuntu:ubuntu' | chpasswd

# apache customization
RUN chmod 777 -R /var/www/html \
	&& sed 's_DocumentRoot /var/www/html_DocumentRoot /var/www/html/result/analyzeData_' /etc/apache2/sites-available/000-default.conf >> /etc/apache2/sites-available/000-default.conf1 \
	&& cp /etc/apache2/sites-available/000-default.conf1 /etc/apache2/sites-available/000-default.conf \
	&& rm /etc/apache2/sites-available/000-default.conf1 \
	&& echo "Header set Access-Control-Allow-Headers \"Content-Type\" \nHeader set Access-Control-Allow-Origin \"*\" " >> /etc/apache2/sites-available/000-default.conf
RUN a2enmod headers

# start ssh and apache server
ENTRYPOINT service ssh start && service apache2 start && /bin/bash

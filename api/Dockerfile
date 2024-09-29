#using ubuntu as a base image
FROM ubuntu 	
			

#setting up the work dirictory
WORKDIR /app


#copying the application files into the container
COPY . .


#downloading dependencies
RUN apt-get update && apt-get install -y \
	curl\
	apache2\
	php\
	php-fpm \
    	php-mysql -y\
	php-cli\
	php libapache2-mod-php\
	php-xml\
	php-curl


#installing composer
RUN curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
RUN HASH=`curl -sS https://composer.github.io/installer.sig`
RUN php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN  php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer


#Running composer install to install the project packages
RUN composer install


#Merging the project with the database
#RUN php artisan migrate


#Exposing port 8000 from the container
EXPOSE 8000



#Starting the api
CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]

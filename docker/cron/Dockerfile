FROM php:7.2.23-fpm-stretch

# Install mysql and cron
RUN apt-get update && apt-get install -y \
    libpq-dev \
    cron \
    nano

RUN docker-php-ext-install mysqli pdo pdo_mysql

#RUN echo "2 * * * * /usr/bin/php /var/www/html/admin/cli/cron.php >/dev/null" > /etc/crontab

# ajout de crontab dans le repertoire cron 
ADD crontab /etc/cron.d/moodle-cron


# donner les droits d'execution au job cron
RUN chmod 0644 /etc/cron.d/moodle-cron

# creation du fichier log
RUN touch /var/log/cron.log

# command executer au demarrage du container
CMD cron && tail -f /var/log/cron.log
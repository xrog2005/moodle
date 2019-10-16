# Moodle
![Moodle](https://img.shields.io/badge/Moodle-%203.7.2-blue?colorB=f98012)
![Apache2](https://img.shields.io/badge/Apache2-2.4-blue.svg?colorB=557697)
![PHP](https://img.shields.io/badge/php-7.2.23--fpm--alpine3.9-blue.svg?colorB=8892BF)
![MariaDB](https://img.shields.io/badge/MariadDB-10.3-blue.svg?colorB=0085B0)
![Cron](https://img.shields.io/badge/Cron-php%3A7.2.23--fpm--stretch-yellow)

Crée rapidement un espace de travail local pour Moodle (Apache2, PHP-FPM et MariaDB). L'espace de travail local est créé et géré par Docker Compose

## Mise en place de l'environnement
1. Ce positionner dans le repertoire /opt
2. Cloner ce repository: ```git clone https://github.com/xrog2005/moodle.git```
3. Aller dans le répertoire moodle: ```cd moodle```
4. Cloner les sources moodle 3.7 stable: ```git clone -b MOODLE_37_STABLE https://github.com/moodle/moodle.git html```
5. copier  env-variable: ```cp env-variable .env```
6. Construire les containers: ```docker-compose build```
7. Démarrer l'environnement: ```docker-compose up -d```
8. Arrêt de l'environnement: ```docker-compose down```


## Variables d'environment 
Le tableau suivant décrit les variables d’environnement dans [**.env**](.env):

| Variable | Default value | Use |
| :--- |:--- |:--- |
| **REPO_FOLDER** | html | Default relative path for Moodle repo |
| **DOCUMENT_ROOT** | /var/www/html | Mount point inside containers for volume **REPO_FOLDER** |
| **MY_TZ** | America/Costa_Rica | Containers timezone |
| **PG_LOCALE** | es_CR | Containers locale |
| **PG_PORT** | 5432 | Postregres port to expose  |
| **POSTGRES_DB** | moodle | Postgres DB for Moodle |
| **POSTGRES_USER** | user | DB user for Moodle |
| **POSTGRES_PASSWORD** | password | DB password for Moodle |
| **PHP_SOCKET** | 9000 | PHP-FPM socket to connect apache2  and php-fpm services |
| **ALIAS_DOMAIN** | localhost | domain alias |
| **WWW_PORT** | 80 | Web port to be bound |
| **MOODLE_DATA** | /var/moodledata | Mount point inside containers for Moodle data folder  |
| **WWWROOT** | localhost | Host part to set in Moodle file 'config.php' for config option 'wwwroot' |







## Gestion des services
1. Arrêt d'un service
``` bash
docker-compose stop
# docker-compose stop <service>
```
2. Démarrage d'un service
``` bash
docker-compose start
# docker-compose start <service>
```

2. Démarrage de l'environnement
``` bash
docker-compose up -d
```
3. Arrêt du project
``` bash
docker-compose down
# Avec les volumes
# docker-compose --volumes down
```
4. Logs
``` bash
docker-compose logs
#docker-compose logs <service>
```

5. Plusieurs commandes Docker
``` bash
# Liste des containers
docker ps
# Liste des images
docker images
# Entrer dans un container
 docker exec -it <container_name> bash
# Verifier les log d'un container
docker logs <container_name> -f
Correspond a une commande tail -f
# Effacement des images dangling
docker rmi $(docker images -f "dangling=true" -q)

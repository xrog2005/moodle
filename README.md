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
5. Construire les containers: ```docker-compose build```
6. Démarrer l'environnement: ```docker-compose up -d```
7. Arrêt de l'environnement: ```docker-compose down```

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
3. Effacement du project
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

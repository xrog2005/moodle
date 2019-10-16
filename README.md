# Moodle
![Moodle](https://img.shields.io/badge/Moodle-%203.7.2-blue?colorB=f98012)
![Apache2](https://img.shields.io/badge/Apache2-2.4-blue.svg?colorB=557697)
![PHP](https://img.shields.io/badge/php-7.2.23--fpm--alpine3.9-blue.svg?colorB=8892BF)
![MariaDB](https://img.shields.io/badge/MariadDB-10.3-blue.svg?colorB=0085B0)
![Cron](https://img.shields.io/badge/Cron-php%3A7.2.23--fpm--stretch-yellow)





1. Arrêt environnement
``` bash
docker-compose stop
# docker-compose stop <service>
```
2. Démarrage environnement
``` bash
docker-compose start
# docker-compose start <service>
```

2. Démarrage project
``` bash
docker-compose up -d
# Different project name
# docker-compose -p my-proj up -d
```
3. Effacement du project
``` bash
docker-compose down
# Remove volumes too
# docker-compose --volumes
# With different project name:
# docker-compose -p my-proj down
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
# Effacement des images dangling
docker rmi $(docker images -f "dangling=true" -q)

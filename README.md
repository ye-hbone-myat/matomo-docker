# Matomo Installation on Docker

Clone file to your server
------------------------
```console
git clone https://github.com/ye-hbone-myat/matomo-docker.git
```
Go to the Matomo folder
----------------------
```console
cd matomo-docker/
```
Run docker compose file
-----------------------
```console
docker-compose up -d
```
Check docker containers
-----------------------
```console
docker ps 
```

Note: After docker containers are up and running, check your server ip address with port 8080 in browser. (For example: http://serverip:8080)

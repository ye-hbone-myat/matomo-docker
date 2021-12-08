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

Set up Database and Super User Account
-------------------------------------
1. Go to http://serverip:8080
2. Follow the steps according to Matomo UI
3. Create Super User Account

Note: Matomo configuration doesn't allow port 8080 for trusted device, so let's fix this.

Modify trusted host for port 8080
---------------------------------
**Step 1 : Check the current config**

```console
docker exec -it matomo-docker_app_1 cat config/config.ini.php | grep trusted_hosts
```
**Step 2 : Change as port 8080**

```console
docker exec -it matomo-docker_app_1 vi config/config.ini.php
```
It will open vi text editor. To edit the config,
1. Type i ( to modify file )
2. Change **trusted_hosts[] = "yourip"** to **trusted_hosts[] = "yourip:8080"**
3. Type esc and type wq! ( to save and quit vi )
4. Recheck the config with the follow command
```console
docker exec -it matomo-docker_app_1 cat config/config.ini.php | grep trusted_hosts
```
5. Go to the url http://serverip:8080 (Now it should be working)


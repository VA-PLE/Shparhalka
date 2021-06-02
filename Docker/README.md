# Shparhalka
## Docker
[Install Docker](https://docs.docker.com/engine/install/ubuntu/)
[Install Docker Compose](https://docs.docker.com/compose/install/)
[Manage Docker as a non-root user](https://docs.docker.com/engine/install/linux-postinstall/)

Display a live stream of container(s) resource usage statistics:
```sh
docker stats
```
Show docker disk usage:
```sh
docker system df
```
List unused volumes:
```sh
docker volume ls -f dangling=true
```
Stop all containers:
```sh
docker stop $(docker ps -aq)
```
Prune unused Docker objects:
```sh
docker system prune -af && docker volume rm $(docker volume ls -f dangling=true -q)
```


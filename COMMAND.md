```bash
# запуск контейнера:
$ docker run -it <IMAGE> sh

# процессы
$ docker ps -a

# удаление
$ docker rm <ID> <ID2> 
$ docker rm $(docker ps -a -q -f status=exited)
$ docker run -rm <other>

# сеть докера
$ docker network ls
$ docker network inspect bridge
$ docker network create <name>
$ docker run --net <network_name> --name <alias>

# docker-compose
$ docker-compose up
$ docker-compose up -d
$ docker-compose ps
$ docker-compose stop
```

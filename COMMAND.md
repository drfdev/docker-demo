```bash
# запуск контейнера:
$ docker run -it <IMAGE> sh

# процессы
$ docker ps -a

# удаление
$ docker rm <ID> <ID2> 
$ docker rm $(docker ps -a -q -f status=exited)
$ docker run -rm <other>

```

Проверить есть ли образы докера:

```bash
$ docker images -a

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              2ca708c1c9cc        7 months ago        64.2MB
hello-world         latest              fce289e99eb9        15 months ago       1.84kB
```

Запустить новый образ: alpine sh
```bash
$ docker run -it --name node-test2 alpine sh

Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
aad63a933944: Pull complete
Digest: sha256:b276d875eeed9c7d3f1cfa7edb06b22ed22b14219a7d67c52c56612330348239
Status: Downloaded newer image for alpine:latest
```

Добавить node.js

```bash
# apk add nodejs

fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/community/x86_64/APKINDEX.tar.gz
(1/7) Installing ca-certificates (20191127-r1)
(2/7) Installing c-ares (1.15.0-r0)
(3/7) Installing libgcc (9.2.0-r4)
(4/7) Installing nghttp2-libs (1.40.0-r0)
(5/7) Installing libstdc++ (9.2.0-r4)
(6/7) Installing libuv (1.34.0-r0)
(7/7) Installing nodejs (12.15.0-r1)
Executing busybox-1.31.1-r9.trigger
Executing ca-certificates-20191127-r1.trigger
OK: 36 MiB in 21 packages
```

Проверим что установилось:

```bash
# node --version

v12.15.0
```

Проверить контейнеры:

```bash
# exit
$ docker container ls -a

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
ef71ec31308f        alpine              "sh"                4 minutes ago       Exited (0) 3 seconds ago                       node-test2
```

Коммит докера: https://docs.docker.com/engine/reference/commandline/commit/
```bash
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
```

| Name, shorthand | Description |
|---|---|
| --author , -a | Author (e.g., “John Hannibal Smith hannibal@a-team.com”) |
| --change , -c | Apply Dockerfile instruction to the created image |
| --message , -m | Commit message |
| --pause , -p | Pause container during commit |

Делаем коммит:

```bash
$ docker commit node-test2 drfdev/node-test2:v1

sha256:4ea58a8f0a4edc7fed16cd0fc799278056380f61e6e87ebf2110c4e4419e0ef7
```

Проверим что образ создался:

```bash
$ docker images

REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
drfdev/node-test2   v1                  4ea58a8f0a4e        About a minute ago   39MB
alpine              latest              a187dde48cd2        3 weeks ago          5.6MB
ubuntu              latest              2ca708c1c9cc        7 months ago         64.2MB
hello-world         latest              fce289e99eb9        15 months ago        1.84kB
```

Авторизация:

```bash
$ docker login

Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: drfdev
Password:
WARNING! Your password will be stored unencrypted in /home/drafff/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```

Пушим образо:

```bash
$ docker push drfdev/node-test2

The push refers to repository [docker.io/drfdev/node-test2]
74db40db5881: Pushed
beee9f30bc1f: Mounted from library/alpine
v1: digest: sha256:436a4ed44e290ee79285b56ce3ad08efdebf7dd04b49d8fcd89822f5dcb100f2 size: 740
```

Удалим образ:
```bash
$ docker images -a

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
drfdev/node-test2   v1                  4ea58a8f0a4e        6 minutes ago       39MB
alpine              latest              a187dde48cd2        3 weeks ago         5.6MB
ubuntu              latest              2ca708c1c9cc        7 months ago        64.2MB
hello-world         latest              fce289e99eb9        15 months ago       1.84kB


$ docker rmi 4ea58a8f0a4e

Untagged: drfdev/node-test2:v1
Untagged: drfdev/node-test2@sha256:436a4ed44e290ee79285b56ce3ad08efdebf7dd04b49d8fcd89822f5dcb100f2
Deleted: sha256:4ea58a8f0a4edc7fed16cd0fc799278056380f61e6e87ebf2110c4e4419e0ef7
Deleted: sha256:083c554c1a3abe3b5be270a5fd0ba3c9dd294ba3d2094a8e9b4dabe1118d7ed2

```

Проверим что образ удалился:

```bash
$ docker images -a

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
alpine              latest              a187dde48cd2        3 weeks ago         5.6MB
ubuntu              latest              2ca708c1c9cc        7 months ago        64.2MB
hello-world         latest              fce289e99eb9        15 months ago       1.84kB

```

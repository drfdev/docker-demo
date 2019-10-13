Test 1:

```
$ sudo docker run -it ubuntu bash
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.40/containers/create: dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
drafff@drafff-pc:~$ sudo docker run -it ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
5667fdb72017: Pull complete
d83811f270d5: Pull complete
ee671aafb583: Pull complete
7fc152dfb3a6: Pull complete
Digest: sha256:b88f8848e9a1a4e4558ba7cfc4acc5879e1d0e7ac06401409062ad2627e6fb58
Status: Downloaded newer image for ubuntu:latest
#
```

```
# uname
Linux
# top
[...]
# apt update
Get:1 http://archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]          
Get:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                        
Get:4 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]    
Get:5 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [777 kB]                         
Get:6 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [13.5 kB]                                
Get:7 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1344 kB]                                                            
Get:8 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [680 kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [186 kB]                            
Get:10 http://security.ubuntu.com/ubuntu bionic-security/restricted amd64 Packages [11.3 kB]
Get:11 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [5665 B]                   
Get:12 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [11.3 MB]      
Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [21.9 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [8734 B]
Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [975 kB]
Get:16 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1295 kB]
Get:17 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [4227 B]
Get:18 http://archive.ubuntu.com/ubuntu bionic-backports/main amd64 Packages [2496 B]
Fetched 17.2 MB in 5s (3442 kB/s)                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
# apt install mc
[...]
# mc
# exit
```

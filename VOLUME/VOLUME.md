docker containers are ephemeral, when continer is removed by default all the data existing in the container will also remove

docker dont have any storage system it uses host filesystem.

using docker volume we can prevent the data getting deleted.

where docker store the data
/var/lib/docker
here overla2/
here it'll create the random value directory for the data

if you create a directory called volume it'll create the volume under

/var/lib/docker/volumes
docker volume create <name-of-volume>

[root@localhost overlay2]# docker volume inspect nginx
[
    {
        "CreatedAt": "2024-02-14T17:43:02Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/nginx/_data",
        "Name": "nginx",
        "Options": {},
        "Scope": "local"
    }
]

How to attach the volume to container
docker run -d -v nginx:/usr/shar/nginx/html -p 80:80 nginx
[root@localhost ~]# cd /var/lib/docker/volumes/nginx/_data/
[root@localhost _data]# ls -l
total 8
-rw-r--r-- 1 root root 497 Oct 24 13:46 50x.html
-rw-r--r-- 1 root root 615 Oct 24 13:46 index.html

above command shows the daa is mounted to created volume

we can also create a directory and mount it with container.
mkdir webdata
docker run -d -v /root/webdata/:/usr/share/nginx/html -p 2003:80 nginx
these volumes are anonymoud to data, these volumes cannot be managed by docker.

Inside host volume directory is created, and this directory can be mounted to any path of the container.

Data inside the volume can also be seen under the container path.

### Example
[root@localhost ~]# docker volume create mysql-data
[root@localhost ~]# docker run -d -v mysql-data:/var/lib/mysql mysql
[root@localhost ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                      PORTS     NAMES
de791458c718   mysql     "docker-entrypoint.s…"   14 seconds ago   Exited (1) 11 seconds ago 

[root@localhost ~]# docker logs de791458c718
2024-02-14 18:21:58+00:00 [ERROR] [Entrypoint]: Database is uninitialized and password option is not specified
    You need to specify one of the following as an environment variable:
    - MYSQL_ROOT_PASSWORD
    - MYSQL_ALLOW_EMPTY_PASSWORD
    - MYSQL_RANDOM_ROOT_PASSWORD

to vercome the above error we need to provide the password as below
[root@localhost ~]# docker run -d -v mysql-data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root123 mysql

[root@localhost ~]# docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                 NAMES
251d06ea445d   mysql     "docker-entrypoint.s…"   5 seconds ago   Up 4 seconds   3306/tcp

[root@localhost ~]# docker exec -it 251d06ea445d bash
bash-4.4# mysql -u root -proot123



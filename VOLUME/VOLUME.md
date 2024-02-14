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


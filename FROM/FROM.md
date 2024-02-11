FROM should be the first instruction in docker.
File Name should be docker file

How to build image form dockerfile

docker build -t (tagging) [docker-hub-url:username:imagename:version .]
ex:
docker build -t docker.io/ghouserizvi/from:v2 .

to push
docker push docker.io/ghouserizvi/from:v2
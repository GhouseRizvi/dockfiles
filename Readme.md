Docker file is a declerative way to create our own images.
By following the docker syntaxx we can create our own images.
go to the docker file reference

To delete all containers including its volumes use,

docker rm -vf $(docker ps -aq)
To delete all the images,

docker rmi -f $(docker images -aq)
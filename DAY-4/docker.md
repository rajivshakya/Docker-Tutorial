**DAY-4**
**Agenda:**


 
  Deploying a container with ubuntu image, hosting a application on container and access that from docker host.
   
  Deploying a container with nginx image, hosting a application on container and access that from docker host.

  Docker Inspect command
 	
  Docker search command

Deploying a container with ubuntu image, hosting a application on container and access that from docker host.

docker container run -itd --name my-server ubuntu

docker container ls

docker container exec -it ecd54c69e9af bash

apt update -y

apt install apache2 -y

service apache2 status

service apache2 start

curl http://<container ip>  # from docker host out side of container.

Deploying a container with nginx image, hosting a application on container and access that from docker host.	

docker container run -itd --name server2 nginx

docker container exec -it 845e35a3a7c9 bash

apt update -y

cd /usr/share/nginx/html/

exit

curl http://<container ip>  # from docker host out side of container.

**Container with centos7**

docker container run -itd --name <container-name> centos:7

docker container run -itd –name <container-name> jenkins



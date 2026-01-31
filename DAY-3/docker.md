
 

**DAY-3**
**Agenda:**

I.	Docker Install on a Linux Machine and creating containers.

Note: Docker can be install any of the Operating Systema, like windows, MacOS, Linux. But we will use the Linux machine to practice docker.

**Prerequisites: **

II.	Linux Machine

        For Linux machine we will create a instance on AWS with Amazon-AMI.
        
****Steps: ****

1.	Create a AWS instance on AWS with Linux operating system.
   
3.	Install Docker.
   
5.	Start Docker Engine.
   
7.	Container creation.
   
**Command:**

docker –help

docker ps

docker ps -a

docker container –help

docker container ls

docker container ls -a

docker container run ubuntu

docker container  run ubuntu sleep 30  # terminal will be busy

docker container run -d ubuntu sleep 30 # container will run in detach mode and terminal will not be engage.

docker container run -d -it ubuntu 

docker container stop <container-id or container name>

docker container start <container-id or container name>

docker container restart <container-id or container name>

docker container rm <container-id or container name>

Note : we cannot remove running container so first we have stop the container and then only we can remove it. If you want to remove running container then you have to remove forcefully.

docker container rm <container-id or container name> -f 

docker container run -itd  --name my-container1 ubuntu

docker container run -it – name my-container2 ubuntu /bin/bash

   apt get update -y
   
   apt get install apache2 -y
   
     cd /var/www/html/
     
      echo “Welcome to to my first application on Docker Container” > index.html
     
     service apache2 start
      
      free -h

docker container inspect <container-id or container name>
 
 take id address of container

curl http://container ip

docker container top <container id>

docker container stats <container id>









 





DAY-06
**Agenda: **
1.	docker attach 
2.	docker rename 
3.	docker export 
4.	docker import
5.	docker diff
6.	docker port  
7.	docker log

**1.	docker attach**

  docker container attach <container-id/name>
**Important behaviour**

•	Attaching connects to the main process, not a new shell

•	If you press Ctrl+C, it sends SIGINT to the container and may stop it

•	To detach without stopping the container, use: ctrl + pq

**Difference between docker attach and docker exec**

**docker attach**

Attaches your terminal to the container’s main running process.

**Key characteristics**

•	Connects to STDOUT / STDERR / STDIN of the container’s PID 1

•	Does not start a new process

•	Whatever you type goes to the existing process

•	Ctrl+C may stop the container

•	To safely detach: Ctrl + P, Ctrl + Q

**Example**

docker attach my_container
Use cases

•	Watching logs in real time

•	Interacting with a foreground app (Node, Python REPL, etc.)

•	Debugging startup behaviour

**Risks**

•	Killing the main process kills the container

•	Not suitable for ad-hoc debugging
________________________________________
**docker exec**

Runs a new command or shell inside an already running container.
Key characteristics

•	Starts a new process

•	Safe for production debugging

•	Does not affect the main process

•	Can open an interactive shell

**Example**

docker exec -it my_container bash

**Use cases**

•	Debugging issues

•	Running one-off commands

•	Inspecting files, env vars, processes

**2.	docker rename**
   
  -	for rename the container. 

**3.	docker export**
   	
-	docker export e4a1f23f88b1 >web.tar

-	docker export e4a1f23f88b1 >web.tar
**4.	docker import**
 	
-	docker import web.tar webimage

-	docker image import web.tar webimage

-	docker images

**5.	docker diff**
 	
-	To check the changes made after running container

-	To check changes in Container.

  docker diff <container-id/name?

**6.	docker port**
 	
-	shows the existing port mapping of container

 	docker container port <container-id/name>

**7.	docker log**

-	to check logs of the container and it’s application running inside it.








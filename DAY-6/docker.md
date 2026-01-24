**🚀 Docker Tutorial: Port Mapping & Deploying a Website in a Container**
📌 Video Agenda
1.	What is Docker & Containers (quick recap)
2.	What is Port Mapping in Docker
3.	Running a container with port mapping
4.	Installing Apache inside a container
5.	Deploying a sample website in a container
6.	Accessing the website from a web browser
7.	Using important Docker commands:
o	docker ps
o	docker exec
o	docker container cp
o	docker inspect
8.	Running multiple containers with different ports
9.	Key takeaways & best practices
________________________________________

**🐳** **What is Port Mapping in Docker?******

Port mapping allows us to access a service running inside a container from the host machine or browser.

**Syntax:**

-p <host_port>:<container_port>

**Example:**

-p 3000:80

•	3000 → Port on host machine

•	80 → Port inside container (Apache runs on port 80)

So when we open:

http://<host-ip>:3000

Docker forwards traffic to:

container:80
________________________________________
**🧪 Step 1: Run First Web Server Container**

docker container run -itd --name web-server1 -p 3000:80 ubuntu

Explanation:
•	-itd → interactive + detached mode
•	--name web-server1 → container name
•	-p 3000:80 → port mapping
•	ubuntu → base image
Check container:
docker ps
________________________________________
**🧪 Step 2: Access Container Shell**

docker exec -it web-server1 bash

Now you are inside the container.
________________________________________
**🧪 Step 3: Install & Start Apache**

Inside container:

# apt update -y

# apt install apache2 -y

Check Apache status:

# service apache2 status

Start Apache:

# service apache2 start
⚠️ Note:
service apache2 enable does not work in containers because containers don’t use systemd.
________________________________________
**🌐 Step 4: Access Default Apache Page**

Open browser:

http://<host-ip>:3000

You should see Apache default page.
________________________________________
**🧪 Step 5: Copy Sample Website into Container**

From host machine (outside container):

docker container cp template104/ web-server1:/var/www/html

Explanation:

•	template104/ → local website files

•	web-server1:/var/www/html → Apache web root inside container

Restart Apache:

docker exec -it web-server1 service apache2 restart

Now refresh browser → 🎉 Website deployed

________________________________________
**🧪 Step 6: Using docker inspect (Port Mapping Proof)**

docker inspect web-server1

Look for:

"HostPort": "3000"

"ContainerPort": "80"

This confirms port mapping.
________________________________________
**🧪 Step 7: Run Second Container (Port Conflict Explained)**

❌ This will FAIL:

docker container run -itd --name web-server2 -p 3000:80 ubuntu

Why?
•	Port 3000 already in use by web-server1
________________________________________
✅ Correct Way: Use a Different Port

docker container run -itd --name web-server3 -p 3001:80 ubuntu
Access:

http://<host-ip>:3001
________________________________________
**🧪 Step 8: Exec into Another Container**

docker exec -it web-server3 bash

Repeat Apache installation steps if needed.
________________________________________
**📌 Important Docker Commands Used**

Command	Purpose

docker ps	List running containers

docker exec	Access container shell

docker container cp	Copy files into container

docker inspect	View container details

docker run -p	Port mapping
________________________________________
**⚠️ Common Mistakes (Explain in Video)**

1.	Same host port cannot be used by multiple containers

2.	enable command doesn’t work inside containers

3.	Apache must run on container port (80)

4.	Website files must be in /var/www/html
________________________________________
**🎯 Key Takeaways**

•	Port mapping connects container services to the outside world

•	Each container must use a unique host port

•	Docker containers are lightweight and fast

•	Perfect for testing and learning web deployments
________________________________________





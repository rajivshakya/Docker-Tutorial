**🎥 Docker Volume – Complete Tutorial (Beginner to Advanced)**
________________________________________
**1️⃣ Problem Statement (How to Start the Video)**

Containers are stateless by default.

If a container is deleted, all data inside it is lost.

👉 So the big question is:

How do we persist data in Docker containers?

✅ The answer is Docker Volumes.
________________________________________
**2️⃣ What is a Docker Volume?**

Definition:

A Docker Volume is a persistent storage mechanism that exists outside the container filesystem but is mounted inside the container.

**Simple Line (Interview Friendly):**

Docker volumes allow data to survive container restarts and deletion.
________________________________________
**3️⃣ Purpose of Docker Volume (Why We Need It)**

Without Volume ❌

•	Data lost when container is removed

•	Not suitable for databases, logs, or configs

**With Volume ✅**

•	Data is persistent

•	Containers can be recreated safely

•	Easy data sharing between containers

**Real-World Use Cases:**
•	Database storage (MySQL, PostgreSQL)

•	Application logs

•	Configuration files

•	Shared data between multiple containers
________________________________________

**6️⃣ How Docker Volume Works (Conceptual View)**

**Host Machine**

┌──────────────────────────┐

│ /var/lib/docker/volumes

│

│   └── volume_data       │

└──────────▲──────────────┘

           │
           
      Mounted into
      
           │
           
Container Path (/data)

✔ Data stays even if container is deleted

✔ Volume lifecycle is independent
________________________________________
**7️⃣ Docker Volume Commands (Core Commands)**

List All Volumes

docker volume ls
________________________________________
Create a Volume

docker volume create myvolume
________________________________________
Inspect a Volume

docker volume inspect myvolume
Shows:
•	Driver
•	Mountpoint
•	Scope
________________________________________
Remove a Volume

docker volume rm myvolume

⚠ The volume must not be in use.
________________________________________
Remove All Unused Volumes

docker volume prune
________________________________________
**8️⃣ Practical Demo – Using Docker Volume**

Step 1: Create a Volume

docker volume create mydata
________________________________________
Step 2: Run a Container with Volume

docker run -it -v mydata:/app/data  ubuntu
________________________________________
Step 3: Write Data Inside Container

cd /app/data

echo "Hello Docker Volume" > file.txt

Exit the container.
________________________________________
Step 4: Remove the Container

docker rm <container_id>
________________________________________
Step 5: Reattach Volume to New Container

docker run -it  -v mydata:/app/data ubuntu

✔ Data still exists

✔ Volume is persistent
________________________________________
**9️⃣ Sharing a Volume Between Multiple Containers**

docker run -it -v sharedvol:/data ubuntu

docker run -it -v sharedvol:/data nginx

✔ Multiple containers

✔ Shared data access
________________________________________

**1️⃣3️⃣ Where Docker Stores Volumes**

Default location:

/var/lib/docker/volumes/

⚠ Do not manually modify volume data.
________________________________________

**1️⃣4️⃣ Backup and Restore Docker Volumes**

Backup:

docker run --rm  -v myvolume:/data \ -v $(pwd):/backup \ ubuntu tar cvf /backup/backup.tar /data
________________________________________
Restore:

docker run --rm \

  -v myvolume:/data \
  
  -v $(pwd):/backup \
  
  ubuntu tar xvf /backup/backup.tar -C /
________________________________________
**1️⃣5️⃣ Real-World Examples**

Application	Volume Path

MySQL	/var/lib/mysql

PostgreSQL	/var/lib/postgresql

Jenkins	/var/jenkins_home

Nginx	Logs

Prometheus	Data directory
________________________________________


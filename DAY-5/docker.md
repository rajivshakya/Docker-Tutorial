**🔹 What is Docker Hub? (Overview)**

Docker Hub is a cloud-based container image registry where developers and DevOps engineers can store, share, download, and manage Docker images.

https://hub.docker.com/

**🔹 Why Docker Hub is Important**
  1. Central place to find ready-made Docker images
  2. Helps in faster application deployment
  3. Used in CI/CD pipelines
  4. Reduces time for image creation from scratch

**🔹 Key Features of Docker Hub**
1️⃣ Public & Private Repositories
   1. Public repo: Anyone can pull images
   2. Private repo: Only authorized users can access.

**Commands:**

docker images pull <image-name>

docker image pull nginx

or

docker pull <image-name>

docker pull nginx

docker image ls

docker images

docker image tag <image> <image-tag>  # tag should be unique

docker push image <image-name>     ## befor push the image your termnal should be login with docker hub credentials.

docker image rm

docker image prune -a

docker image tag <image-name> <image-tag>
docker image nginx rajivshakya687/nginx
docker login
username rajivshakya687
passwrd  *************
docker image push rajivshakya687/nginx


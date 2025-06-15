##Docker
docker pull imagename:tag
#Pulls a specific image (with tag) from Docker Hub or a registry.

docker build -t imagename:tag .
#Builds an image from a Dockerfile and tags it.

docker run -d -p customport:appport imagename:tag
#Runs a container in detached mode, mapping host port to container port.

docker ps
#Lists **running** containers.

docker ps -a
#Lists **all** containers (running + stopped).

docker exec -it containername sh
#Opens an interactive shell (`sh`) inside the running container.

docker stop containerid
#Gracefully stops a running container.

docker rm containerid
#Removes a **stopped** container.

docker rmi imageid
#Removes a Docker image from the local system.

docker inspect containerid
#Displays detailed low-level info (JSON) about the container.

docker logs containerid
#Shows the logs (stdout/stderr) from a container.

docker volume create volumename
#Creates a named Docker volume for persistent storage.

docker volume ls
#Lists all Docker volumes on the system.

docker volume rm volumename
#Deletes a specific Docker volume (if unused).

docker tag image:tag newimagerepo:tag
#Tags an existing image with a new name and/or registry path.

docker login
#Logs in to Docker Hub or another Docker registry.

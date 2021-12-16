## Running NodeJS application on mongodb

```
docker pull mongo
docker pull mongo-express
```

* Check if the images are available locally
```
docker images 
```

## Docker Network  (Isolated network)

- it can be used to connect multiple containers together by using just the container name without the host port.
- Application(nodeJs) from outside can connect to the application from localhost/hostName and port number.

Example:
* Docker Network to connect to mongo and mongo-express
```
docker network ls # check if network exists
```

* Created mongo-network
```
docker network create <name of the network>
docker network create mongo-network
docker network ls
```
* Provide Docker Network to mongo and mongo-express
```
check to see how to use environment variables with mongo
    ```https://hub.docker.com/_/mongo```
```
* Run the mongo container
```
# docker run -d \
-p <hostPort:ContainerPort> \
--name <custom_name> \
-e MONGO_INITDB_ROOT_USERNAME=<addUserName> \
-e MONGO_INITDB_ROOT_PASSWORD=<addPassword> \
--network <useTheCreatedNetwork> \
<image_name>

docker run -d \
-p 27017:27017 \
--name mongodb \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=password \
--network mongo-network \
mongo
```
* Check if the mongo is running
```
- docker logs mongodb
- docker exec -it mongodb /bin/bash 
```
* Run the mongo-express container
```
https://hub.docker.com/_/mongo-express

docker run -d \
-p <hostPort:ContainerPort> \
--name <custom_name> \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=<addUserName> \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=<addPassword> \
--network mongo-network \
-e ME_CONFIG_MONGODB_SERVER=<AlreadySetup_containerName_ofMongo> \
<image_name>
```
```
docker run -d \
-p 8081:8081 \
--name mongo-express \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
--network mongo-network \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
mongo-express
```
* Check if the mongo-express is running
docker logs mongo-express  
http://localhost:8081/ 

#### user-account - Database is created on the mongo-express container

* Connect Node Server to MongoDB Container
#### user-account database will be used for the application(NodeJS)
```yaml
You can write code to update the website or create data in the database through the localhost URL.
> http://localhost:8081/ 
> click on the to created new database <user-account>
> create a new collection <users>
> insert a new document <user>
```
docker ps
docker logs <container_id>
# check the logs of the mongo-express container
docker logs mongo 
docker logs mongo | tail
# string the logs
docker logs mongo -f # follow the logs

# linux command to mv directory

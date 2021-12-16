# https://github.com/nodejs/docker-node/blob/6f740b0ca772e978b44c11d194f369e554c54a14/16/alpine3.14/Dockerfile
FROM node:13-alpine

# set the environment variables 
ENV MONGO_DB_USERNAME=admin \
    MONGO_DB_PWD=password

# Create the folder
RUN mkdir -p /home/app

# copy the files to the folder
COPY ./app /home/app

# set default dir so that next commands executes in /home/app dir
WORKDIR /home/app

# will execute npm install in /home/app because of WORKDIR
RUN npm install

# start the app
# no need for /home/app/server.js because of WORKDIR
CMD ["node", "server.js"]

# d - dettached
# p - port
# t - tag

# docker build -t my-app:1.0 .       # build the image
# docker run -d -p 3000:3000 my-app:1.0
# docker ps
# docker logs <container_id>
# docker exec -it <container_id> /bin/sh

# docker rm -f $(docker ps -a -q) # remove all containers
# docker rmi $(docker images -q) # remove all images
## demo app - developing with Docker

This demo app shows a simple user profile app set up using 
- index.html with pure js and css styles
- nodejs backend with express module
- mongodb for data storage

All components are docker-based

### With Docker

#### To start the application

Step 1: Create docker network

    docker network create mongo-network 

Step 2: start mongodb 

    docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

Step 3: start mongo-express
    
    docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

_NOTE: creating docker-network in optional. You can start both containers in a default network. In this case, just emit `--net` flag in `docker run` command_

Step 4: open mongo-express from browser

    http://localhost:8081

Step 5: create `user-account` _db_ and `users` _collection_ in mongo-express

Step 6: Start your nodejs application locally - go to `app` directory of project 

    npm install 
    node server.js
    
Step 7: Access you nodejs application UI from browser

    http://localhost:3000

### With Docker Compose

#### To start the application

Step 1: start mongodb and mongo-express

    docker-compose -f docker-compose.yaml up
    
_You can access the mongo-express under localhost:8080 from your browser_
    
Step 2: in mongo-express UI - create a new database "my-db"

Step 3: in mongo-express UI - create a new collection "users" in the database "my-db"       
    
Step 4: start node server 

    npm install
    node server.js
    
Step 5: access the nodejs application from browser 

    http://localhost:3000

#### To build a docker image from the application

    docker build -t my-app:1.0 .       
    
The dot "." at the end of the command denotes location of the Dockerfile.



mongo:

docker run -p 27017:27017 -d -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongo --net mongo-network mongo

docker run -d -p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
--net mongo-network \
--name mongo-express1 \
-e ME_CONFIG_MONGODB_SERVER=mongo \
mongo-express




Final Solution: First run this command: sudo chown $USER /var/run/docker.sock Then run this command: docker-compose up -d --build

sudo docker-compose -f docker-compose.yaml up

docker push sandeepprogrammer/dockerhub:myfirstimagepush



docker tag nodewithdb:latest sandeepprogrammer/dockerhub:myfirstimagepush
docker push sandeepprogrammer/dockerhub:myfirstimagepush
docker push simple_node_app:1.0

The push refers to repository [docker.io/sandeepprogrammer/dockerhub]
6c2e693f2a6f: Pushed 
5f70bf18a086: Pushed 
f7786d5915aa: Pushed 
f8fc2db163d5: Pushed 
629960860aca: Pushed 
f019278bad8b: Pushed 
8ca4f4055a70: Pushed 
3e207b409db3: Pushed 
myfirstimagepush: digest: sha256:50812c6bd92540a133e5b9f01394ccaca6429d467e0299124078513afa1a9a6d size: 1993


dckr_pat_TGHCt72HKSfcEBrkwPfJxO5L-eg



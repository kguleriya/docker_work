# commands

## create a docker network
docker network create mongo-network

## start mongodb
docker run -d \
 -p 27017:27017 \
 -e MONGO_INITDB_ROOT_USERNAME=admin \
 -e MONGO_INITDB_ROOT_PASSWORD=password \
 --name mongodb \
 --net mongo-network \
 mongo 

## start mongo-express
docker run -d \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_AUTH_USERNAME=admin \
-e ME_CONFIG_MONGODB_AUTH_PASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
-—net mongo-network \
--name mongo-express \
mongo-express

But the above is not working as it gives error for the authentication on database listing.

## working using yaml command 
docker-compose -f mongo.yaml up

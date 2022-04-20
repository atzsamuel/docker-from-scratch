# Aplicación web node-js + express
```sh
$ cd app;

# Installar dependencias
$ npm install;

# Ejecutar pruebas unitarias
$ npm test;

# Levantar la aplicación
$ node app;

La aplicación estará disponible en el puerto 8080.

#Docker multi-stage
# First install dependencies and execute tests
FROM node:14.5.0-alpine3.12 as build
RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app
WORKDIR /home/node/app
COPY app/ ./
USER node
RUN npm install
RUN npm test
# Second copy files application and expose port and running
FROM node:14.5.0-alpine3.12 as runtime
WORKDIR /home/node/app
COPY --from=build  /home/node/app ./
EXPOSE 8080
CMD ["node", "app"]
# For build docker multi-stage 
docker build -t node-app-multi .
# For view image build 
docker images
# For run docker image node-app-multi
docker run -d -p 8081:8080 node-app-multi
# You can view your docker file running in
http://localhost:8081

# DOCKER MULTI-STAGE
# This functionality is more for solutions compilated 
# For example first compilate image and later copy image compilated only with runtime 
# Other example, first we have .NET SDK and later  .NET RUNTIME
https://hub.docker.com/_/microsoft-dotnet-sdk
https://hub.docker.com/_/microsoft-dotnet-runtime

# Execute following command
docker pull mcr.microsoft.com/dotnet/sdk
# Later execute following command
docker pull mcr.microsoft.com/dotnet/runtime
# Diference between size is .net skd 705MG and size .net runtime 190MG
docker images

# PUBLISH DOCKER IMAGE
# For upload docker enter your username and password created in https://hub.docker.com 
docker login
# Firts name of image need name of your username then rename your image with following command
docker tag node-app-multi atzsamuel/node-app:v1
# View renamed repository with docker images
REPOSITORY                     TAG       IMAGE ID       CREATED          SIZE 
node-app-multi                 latest    fbca8a2c82aa   36 minutes ago   127MB
atzsamuel/node-app             v1        fbca8a2c82aa   36 minutes ago   127M
# For upload image execute
docker login
docker push atzsamuel/node-app:v1
# For donwload your public docker images use
docker run -d -p 8081:8080 atzsamuel/node-app:v1
```

```sh
#DOCKER-COOMPOSE
# 1 First create file docker-compose.yml and add your public docker and version 
version: "3"
services:
    node-app:
        image: atzsamuel/node-app:v1
        ports:
        - "8181:8080"
# 2 execute docker-compose up -d(for exit finaly) for view acces to url http://localhost:8080
```
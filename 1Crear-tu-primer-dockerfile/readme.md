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

# comands for install docker
#1. First install or enable Windows Subsystem for Linux WSL with comand
$ wsl --install;

#if your windows sistem is not version windows 10(Build 19041 and higher) or windows 11
#Execute following command
$ dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

#2. Donwloda docker
https://docs.docker.com/desktop/windows/install/

#3. Enable Hyper-V using Powershell
#Execute following command
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All

# ///////////////////////////////////////////////////////////////////////////////////////
## For completing automatically commnads install vscode extesion 
Docker ms-azuretools.vscode-docker

# For create image docker with respositry name(node-app) execute folliwng command
docker build -t node-app .
# For view name images execute following command
docker images

# For build new image execute following command, this command delete cache and create a new image
docker build -t node-app --no-cache .
# For always donwload node version and not use local node use command *--pull*, and for create with tag use *node-app:v1* after : is name of tag
docker build -t node-app:v1 --no-cache --pull .

# For execute image docker use following command -p for finally of the procces exite terminal, -p for set ports firts port of docker and port in you local machine, name of repository and tag
docker run -d -p 80:8080 node-app:v1

# For view conteiner is running execute following command or enter in you browser in this case http://localhost:80
docker ps
# For force remove conteiner 
docker rm 524dee025f21 -f

# For view all containers running and not run exectute 
docker ps -a
```
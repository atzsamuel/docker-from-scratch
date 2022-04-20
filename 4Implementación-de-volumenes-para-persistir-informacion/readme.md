# Docker compose
```sh
# Ejecutar los contenedores
$ docker-compose up -d
# for view docker execute, we have two docker containers first container  *adminer* and *mysql*
$ docker ps
#CONTAINER ID   IMAGE            COMMAND                  CREATED          STATUS          PORTS                    NAMES
#bdc62df8d392   adminer          "entrypoint.sh docke…"   52 seconds ago   Up 38 seconds   0.0.0.0:8080->8080/tcp #4implementacin-de-volumenes-para-persistir-informacin_adminer_1
#648cf2a52a41   mysql            "docker-entrypoint.s…"   52 seconds ago   Up 39 seconds   3306/tcp, 33060/tcp      #4implementacin-de-volumenes-para-persistir-informacin_db_1 

# For acces type http:localhost:8080 in your browser and default password is *MYSQL_ROOT_PASSWORD: example*(example) and user is *root*

# For remove dockers
$ docker-compose down

# FOR PERSIST INFORMATION 
# add in your yml file, first direcotry in you local computer and after directory in docker container
volumes:
        - /tmp/data:/var/lib/mysql

```
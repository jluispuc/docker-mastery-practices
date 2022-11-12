# Named volumes

### **1. Create a postgres container with name volume psql-data using version 9.6.1**

Para ello debemos conocer el path del VOLUME, entonces en [Dockerhub](https://hub.docker.com/) buscamos la image de **postgress** con el tag de la versión **9.6.1** para conocer el path.

~~~shell
user@machine:~$ docker container run -d --name vpostgres -v psql-data:/var/lib/postgresql/data postgres:15
~~~

>**Note:** Usa ``` docker container logs -f vpostgres ``` para ver el log de lo que ocurrió detrás de escenas al momento de correr el container.

Si inspeccionamos el container en ejecución, en la propiedad **Mounts** encontraremos la siguiente información:

~~~json
{
    "Mounts": [
        {
            "Type": "volume",
            "Name": "psql-data",
            "Source": "/var/lib/docker/volumes/psql-data/_data",
            "Destination": "/var/lib/postgresql/data",
            "Driver": "local",
            "Mode": "z",
            "RW": true,
            "Propagation": ""
        }
    ],
}
~~~
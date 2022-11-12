# 1.- Interactuando con un container por medio de CLI

### **Interacción con un container**


```shell 
user@machine:~$ docker container run -it --name p-centos centos:7 bash
```
Al ejecutar este comando podemos crear, iniciar un container y además interactuar con el por medio de la linea de comandos **bash**.

Una vez ingresado al bash del container podemos ejecutar una prueba actualizando el paquete **curl**:

```bash
[user@machine /]# yum update curl 
```

> **Note:** Puedes usar la opción **rm** para solo probar esta característica, por ejemplo: ``` docker container run --rm -it centos:7 bash ```

> **Note:** Para interactuar por CLI con un container en ejecución puedes ejecutar el siguiente comando: ``` docker exec -it centos bash ```


# 2.- Aplicando la técnica DNS Round Robin

La técnica de **DNS Round Robin** consiste en hacer que dos hosts con diferentes alias puedan responder al mismo nombre DNS, podemos aplicar esta técnica con **Docker Containers**.

### **Crear una red virtual**
```shell
user@machine:~$ docker network create dude
```
Lo primero que hacemos es crear la red virtual donde alojaremos a dos containers que responderán al mismo nombre DNS.

### **Crear dos containers de ***elasticsearch*** con las mismas características**
```shell
user@machine:~$ docker container run -d --net dude --net-alias search elasticsearch:2
```
> **Note:** Para crear los dos containers sólo ejecute el comando dos veces.

> **Note:** Notese que se agregarían a la red creada previamente con la opción **--net <network_name>** y asignándoles un alias con la opción **--net-alias**.

### **Probando búsqueda**
```shell
user@machine:~$ docker container run --rm --net dude centos curl -s search:9200
```
Para probar ejecutamos un container temporal agregándolo a la misma red y ejecutando una búsqueda al DNS **search:PORT**.

> **Note:** Puede ejecutar el comando N veces para asegurarse que los dos container previamente creados y asignados a la misma red estarían respondiendo correctamente.
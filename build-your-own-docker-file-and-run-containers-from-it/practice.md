# 1.- Crea tu propio Dockerfile y corre containers

### **1. Crea un imagen Docker a partir de un archivo Dockerfile**


```shell 
user@machine:~$ docker image build -t appnode .
```

Cuando se ejecuta el comando se va a crear una imagen de docker que podremos usar para correr containers, **appnode** se refiere al nombre que le daremos a la imagen y **.** indica que use el archivo Dockerfile que se debería encontrar desde el lugar donde ejecutemos el comando.

### **2. Correr un container con una imagen previamente creada**


```shell 
user@machine:~$ docker container run -p 80:3000 --rm appnode
```
Se ejecutará un container a partir de la imagen creada.

>**Nota:** Toma en cuenta que al usar la opción **--rm--** es para crear un container temporal.

### **3. Crea una imagen a tu repositorio con su respectivo tag**

```shell 
user@machine:~$ docker image tag appnode:latest <name_repository>/appnode:latest
```

Este comando creará una imagen binculado al repositorio que indiques con el tag **latest** (tag default).

### **4. Sube la imagen al repositorio indicado previamente**

```shell 
user@machine:~$ docker image push <name_repository>/appnode:latest
```

Si todo se ejecuta correctamente podrás ver la imagen en el dashboard de tu repositorio docker (por default es dockerhub [Dockerhub](https://hub.docker.com/).
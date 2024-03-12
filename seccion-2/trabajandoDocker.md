---
title: Sección 2: Herramientas de despliegue de aplicaciones web
layout: default
nav_order: 5
has_children: true
permalink: /seccion-2-herramientas
---
# Creación de contenedores
Para crear un contenedor docker existen dos opciones, la primera es crearlo desde cero y la segunda importando un contenedor desde [dockerhub](https://hub.docker.com/)
Ambas opciones tienen una parte en común que es la siguiente:
```bash
docker run -it --name nombre_contenedor -p puerto1_maquina:puerto1_contenedor -p puerto2_maquina:puerto2_contenedor
```

Ahora, si el contenedor se crea sin usar nada, el codigo completo es 
```bash
docker run -it --name nombre_contenedor -p puerto1_maquina:puerto1_contenedor -p puerto2_maquina:puerto2_contenedor sistemaOperativo:version /bin/bash
```

En caso que el contenedor se descargue desde dockerhub el codigo sería:
```bash
docker run -it --name nombre_contenedor -p puerto1_maquina:puerto1_contenedor -p puerto2_maquina:puerto2_contenedor usuario/contenedor:etiqueta /bin/bash
```

La opción -it indica que el contenedor va a tener interactividad con el usuario.
La opción /bin/bash sirve para entrar en el contenedor una vez creado.
# Eliminación de un contendor 
Para eliminar un contenedor docker lo primero que debemos hacer es detenerlo, para ello hay que usar el comando:
```bash
docker stop nombreContenedor
```
Una vez se haya detenido usamos:
```bash
docker rm nombreContenedor
```

# Puesta en marcha de un contenedor
Para trabajar con un contenedor que ya existe debemos:
    1. Inicializarlo

        ```bash
        docker start contenedor
        ```

    2. Arrancarlo

    ```bash
    docker exec -it contenedor /bin/bash
    ```
Con esos comando ya estaremos dentro del contenedor.
Ademas de las opciones anteriores, hay muchas otras para crear y arrancar los contenedores, todas ellas se pueden consultar en la [documentación oficial](https://docs.docker.com/reference/cli/docker/container/exec/)

# Exportar un contenedor
Para exportar un contenedor es necesario tener cuenta en dockerhub. Esta cuenta nos permitirá tener un repositorio propio en el que almacenar imágenes de nuestros contenedores ya configurados. El primer paso para subir un contenedor es autenticarnos en la terminal con las credenciales de dockerhub, para ello usaremos
 ```bash
 docker login
 ```
Tras esto nos pedirá introducir el usuario y contraseña. En caso de hacerlo bien, aparecerá un mensaje de confirmación.
Una vez autenticados, el siguiente paso es crear la imagen del contenedor que vamos a subir, para esto necesitaremos el id del contenedor que se puede obtener con el comando
```bash
docker ps -a
```
Posteriormente usamos el siguiente comando para crear la imagen a partir del contenedor
```bash
docker commit idContenedor usuarioDockerhub/nombreImagen:etiqueta
```
Finalmente para subir el contenedor a dockerhub usamos 
```bash 
docker push usuarioDockerhub/nombreImagen:etiqueta
```


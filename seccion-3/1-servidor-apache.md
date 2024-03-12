---
title: 3.1-Servidor Apache2
parent: 3-Administracion de servidores web
layout: default
nav_order: 1
---

# Servidor Apache
# Instalación de Apache 2 en Ubuntu

## Introducción

Apache HTTP Server, comúnmente conocido como Apache, es un servidor web de código abierto ampliamente utilizado en Internet. Este tutorial te guiará a través del proceso de instalación de Apache 2 en un sistema Ubuntu.

## Pasos para la instalación

1. **Abrir la terminal**: Abre una terminal en tu sistema Ubuntu. Puedes hacerlo buscando "Terminal" en el menú de aplicaciones o presionando `Ctrl + Alt + T`.

2. **Actualizar el índice de paquetes**: Actualiza el índice de paquetes de tu sistema para asegurarte de que tienes la información más reciente sobre los paquetes disponibles. Ejecuta el siguiente comando:

    ```
    sudo apt update
    ```

3. **Instalar Apache 2**: Una vez que se haya actualizado el índice de paquetes, puedes instalar Apache 2 ejecutando el siguiente comando:

    ```
    sudo apt install apache2
    ```

    Durante la instalación, se te pedirá confirmación para proceder. Presiona `Y` y luego `Enter` para continuar con la instalación.


    ```
    sudo apt install apache2
    ```

4. **Verificar la instalación**: Una vez completada la instalación, Apache 2 debería estar en funcionamiento. Puedes verificarlo ingresando la dirección IP de tu servidor en un navegador web. Si estás en el mismo equipo donde instalaste Apache, puedes usar `http://localhost` o `http://127.0.0.1`.

    Si Apache 2 se ha instalado correctamente, verás una página de bienvenida de Apache que indica que la instalación ha sido exitosa.

    Tambien puedes comprobar que tu servidor apache funciona correctamente con el comando
    ```
    sudo service apache2 status
    ```
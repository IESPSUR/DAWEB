---
title: Servidor Apache2
parent: 4-Administracion de servidores web
layout: default
nav_order: 5
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

## Configuración de Servidor HTTPS en Apache 2.2 sobre Linux

Configuración en el servidor Apache instalado en Ubuntu:

1. **Habilitar el servidor virtual por defecto**:
   - Utiliza el comando `sudo a2ensite default` para habilitar el servidor virtual por defecto de Apache.


2. **Habilitar el servidor virtual SSL por defecto**:
   - Habilita el módulo `mod_ssl` y el sitio `default-ssl` para configurar el servidor virtual SSL por defecto.

3. **Acceder a la URL segura para probar la configuración realizada**:
   - Accede a `https://10.33.X.3` en un navegador web y prueba la configuración realizada.

4. **Deshabilitar el servidor virtual SSL por defecto (default-ssl)**:
   - Utiliza el comando `sudo a2dissite default-ssl` para deshabilitar el servidor virtual SSL por defecto.

5. **Crear un certificado digital autofirmado con OpenSSL para el dominio claseDAW.net**:
   - Utiliza OpenSSL para generar un certificado autofirmado para el dominio `claseDAW.net`.

6. **Crear y habilitar un servidor virtual HTTPS para el dominio claseDAW.net**:
   - Crea un servidor virtual HTTPS con el directorio raíz en `/var/www/claseDAW/` y configura el log de errores en `/var/log/apache2/claseDAW.error.log` y el log de accesos en `/var/log/apache2/claseDAW.access.log` con formato `combined`.

Para realizar estos pasos, asegúrate de tener privilegios de administración en la sesión de Ubuntu XX.
Apache es un servidor modular, lo que significa que su funcionalidad puede extenderse mediante módulos adicionales. Cada módulo agrupa funcionalidades y directivas que permiten su configuración. Puedes consultar los módulos disponibles en [http://httpd.apache.org/docs/2.2/mod/](http://httpd.apache.org/docs/2.2/mod/) y [http://modules.apache.org/](http://modules.apache.org/).

Existen dos tipos de módulos en Apache:
- **Módulos estáticos:** Se incluyen durante la compilación de Apache.
- **Módulos dinámicos:** Se cargan al iniciar el servidor.

Durante la compilación, Apache incluye un conjunto básico de módulos en el servidor. Además, si se compila con la opción DSO (Dynamic Shared Object), se pueden cargar módulos dinámicos mediante la directiva `LoadModule`.

La directiva `<IfModule nombre_modulo>` `</IfModule>` permite especificar directivas que se aplicarán si el módulo indicado está cargado.

## Reinicio del Servidor

Es crucial reiniciar el servidor para aplicar los cambios realizados.

## Configuración SSL

Para habilitar SSL en Apache, es necesario modificar el archivo de configuración `/etc/apache2/ports.conf`. Además, se puede verificar si el servidor está escuchando en los puertos 80/TCP y 443/TCP utilizando el comando `netstat -ltn | grep apache`. Se debe habilitar el servidor virtual SSL por defecto (`default-ssl`) ejecutando `sudo a2ensite default-ssl`.

Después de habilitar SSL, es importante observar la configuración del archivo `/etc/apache2/sites-available/default-ssl`, donde se definen las directivas para SSL y la ruta del certificado digital utilizado por el servidor. Por lo general, se utiliza un certificado autofirmado por defecto, lo que significa que los navegadores mostrarán una advertencia de seguridad al acceder al servidor.

## Servidor Virtual para un Dominio Específico

Para configurar un servidor virtual para un dominio específico, como `claseDAW.net`, se deben seguir varios pasos:

1. Configurar un servidor DNS para que resuelva el nombre de dominio a la dirección IP del servidor.
2. Crear un directorio raíz para el sitio web (`/var/www/claseDAW`).
3. Crear un certificado digital autofirmado utilizando OpenSSL.
4. Configurar el archivo de sitio disponible para el servidor claseDAW.
5. Deshabilitar el servidor SSL por defecto.
6. Habilitar el servidor virtual claseDAW.
7. Reiniciar el servidor para aplicar los cambios.

Estos pasos permiten configurar y gestionar servidores web con Apache en Ubuntu de manera efectiva.
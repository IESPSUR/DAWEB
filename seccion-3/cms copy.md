---
title: SSL Certificate
parent: 4-Administracion de servidores web
layout: default
nav_order: 6
---
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
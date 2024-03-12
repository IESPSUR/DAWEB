---
title: 1.1 - Guía rápida SSH
layout: default
nav_order: 1
parent: 1 - Servicio-SSH

---
# Guia rápida de como usar ssh

## Abrir la terminal

En tu sistema operativo (Windows, macOS, Linux), abre la terminal o el símbolo del sistema. Esto te permitirá ingresar comandos de texto para comunicarte con tu computadora o con otros servidores.

## Escribir el comando SSH: 

El formato básico del comando SSH es:

```
ssh usuario@direccion_del_servidor
```

-usuario: El nombre de usuario en el servidor remoto al que deseas conectarte.
- direccion_del_servidor: La dirección IP o el nombre de dominio del servidor al que nos conectamos.

Por ejemplo, si tu nombre de usuario en el servidor remoto es "usuario" y la dirección IP del servidor es "192.168.1.100", el comando sería:

```
ssh usuario@192.168.1.100
```

## Introducir la contraseña: 

Después de ejecutar el comando, se te pedirá que ingreses la contraseña del usuario en el servidor remoto. Escribe la contraseña y presiona Enter. Ten en cuenta que cuando escribas la contraseña, no se mostrará en la pantalla por razones de seguridad, pero el sistema la está recibiendo.

## Autenticación de clave SSH (opcional):

En lugar de ingresar una contraseña cada vez que te conectas al servidor, también puedes configurar la autenticación mediante clave SSH. Esto implica generar un par de claves SSH (pública y privada), cargar la clave pública en el servidor remoto y guardar la clave privada en tu computadora. Este método es más seguro y conveniente que usar contraseñas.

Para generar un par de claves SSH, puedes usar el siguiente comando en tu terminal:

```
ssh-keygen -t rsa -b 4096
```

Sigue las instrucciones en pantalla para generar tus claves. Luego, carga la clave pública en el servidor remoto. La ubicación donde debes colocar la clave pública varía según la configuración del servidor, pero comúnmente se encuentra en el archivo ~/.ssh/authorized_keys en el directorio de inicio del usuario remoto.
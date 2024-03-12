---
layout: default
title: 1-Servicio SSH
nav_order: 2
has_children: true
---


# Sección 1: ¿Qué es SSH?
El servicio SSH (secure shell) permite establecer conexiones seguras entre máquinas remotas. 
Sus características principales son:
    - Usa el puerto 22 TCP y UDP
    - Permite la autenticación mediante contraseña o un sistema de claves
    - Se puede integrar con otros sistemas de autenticación (Kerberos, PGP o PAM)
    - Está soportado por la mayoría de sistemas operativos y plataformas

Las ventajas de utilizar este servicio son:
    - Después de que un usuario se conecta a una máquina a través de otra máquin,a la máquina cliente puede saber que en las conexiones futuras se harán al mismo servidor
    - La información de autenticación se envía de forma cifrada, así como los datos que se transmitan mientras esté funcionando la conexión, evitando así:
        1. Suplantación de host
        2. Interceptación de la comunicación
    - El cliente puede ejecutar aplicaciones gráficas desde el shell de forma segura

# Proceso de conexión
    1. El cliente abre una conexión con el puerto 22 del servidor
    2. El cliente y el servidor determinan la versión de SSH que usarán, además del algoritmo de cifrado
    3. El servidor envía la clave pública al cliente
    4. El cliente compara la clave recibida con la que almacena (salvo que sea la primera vez que se conectan)

![Esquema de la conexión entre cliente y servidor](/imagenes/parClaves.png)

    5. El cliente crea una clave de sesión y un mensaje con esta clave y el algoritmo usado para crearla y lo encripta usando la clave pública que recibe del servidor
    6. A partir de entonces y hasta que se rompa la conexión, se comunicarán con la clave privada
    7. Se autentica el usuario y se inicia la sesión
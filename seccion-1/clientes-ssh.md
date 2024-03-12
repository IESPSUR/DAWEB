---
title: Clientes SSH
layout: default
nav_order: 3
parent: 1-Servicio-SSH

---
# ¿Qué es el cliente SSH?
Es una herramienta que permite al usuario solicitar establecer una conexión entre su máquina y una máquina remota de forma segura. Se puede hacer de forma gráfica o por comandos.
El comando scp copia, de forma segura, un archivo local de la máquina local a una máquina remota

```bash
scp nombre_usuario@maquina_origen:archivo_origen nombre_usuario@maquina_destino:archivo_destino
```
Este comando copia el archivo local a la máquina remota

```bash
scp archivo_local nombre_usuario@maqquina_remota:archivo_copia
```
Este comando copia un archivo remoto a la máquina local

```bash
scp nombre_usuario@maquina_remota:archivo_remoto archivo_copia_local
```
Este comando copia un directorio local a la máquina remota

```bash
scp /directorio/* nombre_usuario@nombre_maquina:/directorio_destino/
```

El comando sftp abre una sesión segura e interactiva:

```bash
sftp nombre_usuario@nombre_maquina
```

## X11
Es una de las funciones de SSH. Establece un canal de órdenes seguras. Cuando dos máquinas están conectadas por SSH a través de un canal seguro, los datos que envíen el cliente y el servidor se harán a través de este canal.

## Reenvío por TCP/IP
Consiste en asignar a un puerto del servidor remoto, un puerto local del cliente. Así, la información que recibe el cliente, se puede enviar a otro puerto de la máquina servidor. 
Ésto se usa para protocolos que no tienen soporte nativo de comunicaciones cifradas y autenticadas como POP, IMAP o FTP. La forma de crear un túnel de reenvío local es:

```bash
    ssh -L puerto_local:maquina_local:puerto_remoto nombre_usuario@maquina_remota
    ssh -L 10143:localhost:143 alumno1@mail.servidor.aula
```

En este caso el usuario alumno1 envía desde el puerto 10143 de su máquina local a la 143 del servidor sus peticiones




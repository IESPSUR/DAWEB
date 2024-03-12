---
title: Introducción a Docker para desarrolladores
parent:  2-Herramientas de despliegue de aplicaciones web
layout: default
nav_order: 3

---

# Introducción a Docker para desarrolladores


## Docker
Docker es una tecnología de virtualización por medio de contenedores. Los contenedores contienen la arquitectura necesaria para que una aplicación pueda ejecutarse en él y su uso reduce los requerimientos de otros sistemas de despliegue. Entre sus ventajas están la facilidad de distribución, la velocidad de arranque, la portabilidad y la eficiencia.

Docker está soportado por los mayores sistemas operativos, aunque en esta guía hablaremos de su instalación y uso en Ubuntu.

### Instalación
Para instalar docker en ubuntu tenemos dos opciones, en primer lugar de forma gráfica accediendo a la web oficial de docker

[web de docker](https://docs.docker.com/desktop/install/linux-install/) y descargando la aplicación directamente. La segunda forma es a través de la terminal mediante comandos, los cuales se pueden consultar aquí [instalación de docker por comandos en ubuntu](https://docs.docker.com/engine/install/ubuntu/):

Este comando se encargará de desinstalar de la máquina cualquier paquete que pueda ser conflictivo con la instalación

```bash
    for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
Este bloque de comandos se encarga de descargar los certificados y claves necesarios

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
El último comando es el necesario para descargar e instalar docker

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```


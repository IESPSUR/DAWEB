---
nav_order: 5
title: Tomcat
layout: default
parent: 5-Administracion de servidores de aplicaciones web

---

# Tomcat

# Pasos para Instalar y Configurar Apache Tomcat

## Paso 1: Instalación de Tomcat

1. Descargar la última versión de Apache Tomcat, en este caso Tomcat 10, desde la página de descargas.
2. Crear un usuario separado y no privilegiado para ejecutar Tomcat utilizando el comando `sudo useradd -m -d /opt/tomcat -U -s /bin/false tomcat`.
3. Instalar el Java Development Kit (JDK) con `sudo apt install default-jdk`.
4. Verificar la instalación de Java con `java -version`.
5. Descargar y extraer el archivo comprimido de Tomcat en el directorio `/opt/tomcat`.
6. Asignar la propiedad y permisos adecuados al directorio de instalación con `sudo chown -R tomcat:tomcat /opt/tomcat/` y `sudo chmod -R u+x /opt/tomcat/bin`.

## Paso 2: Configuración de Usuarios Administradores

1. Editar el archivo de configuración de usuarios de Tomcat en `/opt/tomcat/conf/tomcat-users.xml`.
2. Definir usuarios y roles para acceder a las páginas de administración de Tomcat, como Manager y Host Manager.
3. Modificar los archivos de configuración para permitir el acceso desde cualquier dirección IP a las páginas de administración.

## Paso 3: Creación de un Servicio systemd

1. Identificar la ubicación del Java Runtime Environment (JRE) con `sudo update-java-alternatives -l`.
2. Crear un archivo de servicio systemd para Tomcat en `/etc/systemd/system/tomcat.service` y definir su configuración.
3. Recargar el demonio systemd con `sudo systemctl daemon-reload`.
4. Iniciar el servicio de Tomcat con `sudo systemctl start tomcat`.
5. Verificar el estado del servicio para asegurarse de que se inició correctamente con `sudo systemctl status tomcat`.
6. Habilitar el inicio automático de Tomcat al arrancar el sistema con `sudo systemctl enable tomcat`.

* [Guia para instalar Tomcat en ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-10-on-ubuntu-20-04)


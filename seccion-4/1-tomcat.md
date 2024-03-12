---
nav_order: 1
title: Instalacion Tomcat
layout: default
parent: 5-Administracion de servidores de aplicaciones web

---

# Tomcat

## Pasos para Instalar y Configurar Apache Tomcat

* [Guia para instalar Tomcat en ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-10-on-ubuntu-20-04)

## Paso 1 — Instalación de Tomcat

En esta sección, configurarás Tomcat 10 en tu servidor. Para comenzar, descargarás su última versión y configurarás un usuario separado con los permisos apropiados. También instalarás el Kit de Desarrollo de Java (JDK).

Por motivos de seguridad, Tomcat debe ejecutarse bajo un usuario separado y no privilegiado. Ejecuta el siguiente comando para crear un usuario llamado tomcat:

```
sudo useradd -m -d /opt/tomcat -U -s /bin/false tomcat
```

Al proporcionar `/bin/false` como la shell predeterminada del usuario, te aseguras de que no sea posible iniciar sesión como tomcat.

Ahora instalarás el JDK. Primero, actualiza la caché del gestor de paquetes ejecutando:

```
sudo apt update
```

Luego, instala el JDK ejecutando el siguiente comando:

```
sudo apt install default-jdk
```

Responde 'y' cuando se te solicite continuar con la instalación. Cuando la instalación finalice, verifica la versión de la instalación de Java disponible:

```
java -version
```

La salida debería ser similar a esta:

```
openjdk version "11.0.14" 2022-01-18
OpenJDK Runtime Environment (build 11.0.14+9-Ubuntu-0ubuntu2.20.04)
OpenJDK 64-Bit Server VM (build 11.0.14+9-Ubuntu-0ubuntu2.20.04, mixed mode, sharing)
```

Para instalar Tomcat, necesitarás la última versión básica de Linux para Tomcat 10, que puedes obtener desde la página de descargas. Selecciona la última versión básica de Linux, que termina en .tar.gz. En el momento de escribir esto, la última versión era 10.0.20.

Primero, navega al directorio `/tmp`:

```
cd /tmp
```

Descarga el archivo usando wget ejecutando el siguiente comando:

```
wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.0.20/bin/apache-tomcat-10.0.20.tar.gz
```

El comando wget descarga recursos de Internet.

Luego, extrae el archivo descargado ejecutando:

```
sudo tar xzvf apache-tomcat-10*tar.gz -C /opt/tomcat --strip-components=1
```

Dado que ya has creado un usuario, ahora puedes otorgarle a tomcat la propiedad sobre la instalación extraída ejecutando:

```
sudo chown -R tomcat:tomcat /opt/tomcat/
sudo chmod -R u+x /opt/tomcat/bin
```

Ambos comandos actualizan la configuración de tu instalación de tomcat. Para obtener más información sobre estos comandos y qué hacen, visita Conceptos básicos de permisos en Linux y Cómo usar Umask en un VPS.

En este paso, instalaste el JDK y Tomcat. También creaste un usuario separado para él y configuraste permisos sobre los binarios de Tomcat. Ahora configurarás credenciales para acceder a tu instancia de Tomcat.
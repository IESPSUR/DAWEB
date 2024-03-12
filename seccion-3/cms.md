---
title: Sistema de gestión de contenidos
parent: 4-Administracion de servidores web
layout: default
nav_order: 4
---
# ¿Qué es un CMS como Magento?

Un CMS, o Sistema de Gestión de Contenidos, es una aplicación que permite crear, administrar y publicar contenido en línea de manera fácil y eficiente. Magento es un CMS especialmente diseñado para la creación y gestión de tiendas en línea, también conocidas como comercio electrónico.

En resumen, Magento es un CMS especializado en comercio electrónico que ofrece una amplia gama de funciones y herramientas para ayudar a las empresas a crear y gestionar tiendas en línea de manera efectiva y exitosa.

Vamos a proceder a explicar como instalar magento en un contenedor docjker.

# Pasos para configurar una plataforma LAMP con Docker

Paso 1: Construir la plataforma LAMP

```
docker run -it --name lamp -p 80:80 -p 443:443 ubuntu:22.04 /bin/bash
```

Instalación de Apache2 y MariaDB en el contenedor:

```
apt update && apt upgrade
apt install apache2
apt install mariadb-server mariadb-client -y

```

Instalación de PHP 7 para Magento:
```
apt-get install software-properties-common
add-apt-repository ppa:ondrej/php
apt update
apt-get install php7.1 php7.1-common php7.1-mbstring php7.1-xmlrpc php7.1-soap php7.1-gd php7.1-xml php7.1-intl php7.1-mysql php7.1-cli php7.1-mcrypt php7.1-ldap php7.1-zip php7.1-curl

```

Creación de la base de datos para Magento:

```
mariadb -u root -p

CREATE DATABASE `magento`;
CREATE USER 'miusuario'@localhost IDENTIFIED BY 'mipassword';
GRANT USAGE ON *.* TO 'miusuario'@localhost IDENTIFIED BY 'mipassword';
GRANT USAGE ON *.* TO 'miusuario'@'%' IDENTIFIED BY 'mipassword';
GRANT ALL privileges ON `magento`.* TO 'miusuario'@localhost IDENTIFIED BY 'mipassword';
FLUSH PRIVILEGES;
exit;

```

Subida del contenedor a Docker Hub para tener la imagen LAMP7:

```
docker commit -m "plataforma LAMP con MariaDB, Apache2 y PHP7" lamp nombreusuariodocker/lamp7:1.0
docker push nombreusuariodocker/lamp7:1.0

```

Instalación de Magento:

```
mkdir /var/www/html/magento/
cd /var/www/html/magento/
wget https://github.com/OpenMage/magento-mirror/archive/refs/tags/1.9.4.5.tar.gz
tar -zxvf 1.9.4.5.tar.gz
chown -R www-data:www-data /var/www/html/magento
chmod -R 755 /var/www/html/magento

```

Dentro del archivo, agrega el siguiente contenido:

```
<VirtualHost *:80>
    ServerAdmin admin@example.com
    DocumentRoot /var/www/html/magento/
    ServerName example.com
    ServerAlias www.example.com

    <Directory /var/www/html/magento/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

Luego, habilita el sitio Magento y el módulo rewrite:

```
a2ensite magento.conf
a2enmod rewrite
service apache2 restart
```
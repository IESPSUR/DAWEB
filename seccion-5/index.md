---
nav_order: 6
title: 5-Servicios de nombres de dominio
layout: default
has_children: true
---

# 6-Servicios de nombres de dominio (DNS)

El Sistema de Nombres de Dominio (DNS) es un servicio fundamental en Internet que traduce los nombres de dominio legibles por humanos en direcciones IP numéricas utilizadas por los equipos para comunicarse entre sí. Aquí hay una descripción de los servicios que ofrece DNS:

## Resolución de Nombres

DNS proporciona el servicio de resolución de nombres, que implica la traducción de nombres de dominio en direcciones IP y viceversa. Esto permite a los usuarios acceder a sitios web, enviar correos electrónicos y realizar otras actividades en Internet utilizando nombres de dominio amigables en lugar de direcciones IP numéricas difíciles de recordar.

## Registro de Dominios

Los servicios de DNS también incluyen el registro de nombres de dominio, donde los usuarios pueden registrar y administrar nombres de dominio únicos para sus sitios web. Esto implica la reserva de un nombre de dominio específico y la asociación de ese nombre con una dirección IP en los servidores DNS.

## Distribución de Carga

DNS puede ser utilizado para distribuir la carga de tráfico entre varios servidores. Al configurar múltiples registros de recursos (RR) con el mismo nombre de dominio pero diferentes direcciones IP, el DNS puede redirigir las solicitudes entrantes a servidores específicos en función de factores como la disponibilidad o la carga actual del servidor.

## Seguridad y Control de Acceso

Además de la traducción de nombres de dominio, DNS también puede desempeñar un papel en la seguridad y el control de acceso. Los registros de recursos como SPF (Sender Policy Framework) y DKIM (DomainKeys Identified Mail) se utilizan para autenticar el correo electrónico saliente y evitar el correo no deseado o el phishing.

## Caché

DNS utiliza la caché para mejorar el rendimiento y la eficiencia. Cuando se realiza una consulta DNS, los servidores DNS pueden almacenar temporalmente los resultados en caché. Esto significa que si se realiza la misma consulta nuevamente en el futuro, el servidor DNS puede responder directamente desde su caché en lugar de realizar una nueva consulta a otros servidores DNS.

En resumen, el Sistema de Nombres de Dominio (DNS) ofrece una variedad de servicios esenciales que son fundamentales para el funcionamiento de Internet. Desde la resolución de nombres hasta el registro de dominios y la distribución de carga, el DNS juega un papel crucial en la accesibilidad, la seguridad y la eficiencia de la red global.

![Esquema de la conexión entre cliente y servidor](imagenes/DNS.png)



Aquí podras encontrar documentación sobre DNS
* [Instalacion de Bind9](pdf/Instalaci%C3%B3n%20del%20servidor%20DNS%20con%20Bind9.pdf)
* [Servicio DNS](pdf/Servicio%20DNS.pdf)
* [Servidor DNS](pdf/Servidor%20DNS.pdf)

* [Sistema de nombres de dominio](https://www.evernote.com/shard/s201/client/snv?noteGuid=7c1b2ce5-2c65-4475-adeb-aee3c806618d&noteKey=443ae331de64f2d9d3ce30d132a9755f&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs201%2Fsh%2F7c1b2ce5-2c65-4475-adeb-aee3c806618d%2F443ae331de64f2d9d3ce30d132a9755f&title=Sistema%2Bde%2Bnombres%2Bde%2Bdominio%2B-%2BWikipedia%252C%2Bla%2Benciclopedia%2Blibre&authuser=0)
* 
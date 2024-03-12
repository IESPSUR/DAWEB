---
layout: home
title: Introducción a Despliegue De Aplicaciones Web
nav_order: 1
---


# Bienvenidos a Despliegue de Aplicaciones Web
## Aquí encontrarás la documentación necesaria para el curso de Despliegue de Aplicaciones Web.

El contenido de esta sección es el que se proporciona durante el curso de 2º año de DAW, en el que se tratan temas como SSH, servidores web y DNS

## Aspectos generales en la arquitectura web

- **Escalabilidad**: 
  - Vertical (hw: ampliando capacidades, sw: instalando nuevos servidores en la propia máquina).
  - Horizontal (hw: instalando nuevas máquinas, sw: instalando el servidor en formato clúster para la alta disponibilidad).
- **Separación de responsabilidades**
- **Portabilidad**
- **Utilización de componentes en los servicios de infraestructura**
- **Gestión de las sesiones del usuario**
- **Aplicación de patrones de diseño**

De forma genérica podríamos decir que la arquitectura web es un modelo compuesto de tres capas:

1. **Capa de Base de Datos**: Aquí se encuentra toda la documentación de la información que se pretende administrar mediante el servicio web y emplearía una plataforma del tipo MySQL, PostgreSQL, etc.

2. **Capa de Servidores de Aplicaciones Web**: En esta capa se encuentran los servidores de aplicaciones web, ejecutando aplicaciones de tipo Apache, nginx, Microsoft IIS, Tomcat, Resin, etc.

3. **Capa de Clientes**: Aquí se encuentran los clientes del servicio web, que accederán mediante un navegador web como Firefox, Internet Explorer, Opera, etc.


## Aplicaciones web segun el uso

### Propósito General
- Permiten crear portales de múltiples temas.

### Blogs
- Permiten gestionar los contenidos de forma cronológica, por temas, por editores, etc.

### Contabilidad
- Permiten gestionar en equipo la contabilidad de una entidad.

### ERP (Sistemas de Planificación de Recursos Empresariales)
- Sistemas de gestión integral de recursos empresariales.

### Gestión de Proyectos
- Permiten realizar la gestión de proyectos, temporizando, asignando recursos, rediseñando el plan inicial, diagrama de Gantt, etc.

### Wikis
- Permiten la colaboración en la edición y publicación de contenidos online.

### E-commerce (Comercio Electrónico)
- Permiten crear un portal de comercio electrónico, una tienda online, gestionando todos sus detalles.

## Tegnologias mas usadas en desarrollo web

### Servidor Web
- Apache
- Nginx
- Apache Tomcat

### Servidor de Bases de Datos
- MySQL
- Oracle
- PostgreSQL
- SQL Server

### Lenguaje de Desarrollo
- PHP (la gran mayoría)
- Java
- Perl
- Ruby on Rails
- Python (gran crecimiento en los últimos años, asociado al big data e inteligencia artificial)


## Cloud Computing

“Cloud computing” es un modelo de prestación de servicios de negocio y tecnología en la red. 

### Tipos de cloud según modelo de despliegue

- Nube pública: Los servicios que ofrecen se encuentran en servidores externos al usuario.  Es administrado por terceras partes. Las aplicaciones e información almacenada de diferentes clientes pueden coexistir en los servidores. 
Ejemplo: Hosting compartido, AWS.

- Nube privada: Las plataformas internas, como los Centros de Procesamiento de Datos (CPD) privados y el housing, se encuentran dentro de la compañía que demanda el servicio y no suelen ofrecer servicios a terceros. Por lo general, son administradas por un único cliente, quien controla qué aplicaciones deben ejecutarse y dónde. Son propietarios del servidor, almacenamiento y red, y tienen el poder de decidir qué usuarios están autorizados a utilizar la infraestructura. Este enfoque es una excelente opción para las compañías que requieren una alta protección de datos.
  
- Nube híbrida: El modelo de despliegue de Cloud Híbrido combina los dos tipos de cloud anteriores: el Cloud Privado, que se usa para los datos y aplicaciones de misión crítica para garantizar un alto rendimiento, disponibilidad, seguridad y control, y el Cloud Público, para asumir picos de demanda puntuales que en las instalaciones privadas no es posible satisfacer.

## OpenStack

OpenStack es una solución de cloud computing del tipo IaaS de código abierto.

Su misión es “crear una plataforma en software libre para cloud computing que cumpla con las necesidades de los proveedores de nubes públicas y privadas, independientemente de su tamaño, que sea fácil de implementar y masivamente escalable."


## [Amazon Web Services](https://aws.amazon.com/es/)

Amazon Web Services ofrece un amplio conjunto de servicios globales de informática, almacenamiento, bases de datos, análisis, aplicaciones e implementaciones que ayudan a las organizaciones a avanzar con más rapidez, reducir costes de TI y escalar aplicaciones.

## [Microsoft Azure](https://azure.microsoft.com/es-es)

Microsoft Azure es un servicio de computación en la nube creado por Microsoft para construir, probar, desplegar y administrar aplicaciones y servicios mediante el uso de sus centros de datos.

## [Contenedores Docker](https://www.docker.com/)

Docker es un proyecto de código abierto que automatiza el despliegue de aplicaciones dentro de contenedores de software, proporcionando una capa adicional de abstracción y automatización de virtualización de aplicaciones en múltiples sistemas operativos.​ 

## [Virtualización con Virtualbox](https://www.virtualbox.org/)

Oracle VM VirtualBox es un software de virtualización para arquitecturas x86/amd64. Actualmente es desarrollado por Oracle Corporation como parte de su familia de productos de virtualización.

## [Virtualización con Qemu](https://www.qemu.org/)

QEMU es un emulador de procesadores basado en la traducción dinámica de binarios. QEMU también tiene capacidades de virtualización dentro de un sistema operativo, ya sea GNU/Linux, Windows, o cualquiera de los sistemas operativos admitidos; de hecho es la forma más común de uso.






* [Sesión 1: SSH](seccion-1)
* [Sesión 2: Herramientas de despliegue de aplicaciones web](seccion-2)
* [Sesión 3: Sección 3: Servidor Apache](seccion-3)
* [Sesión 4: Redes en docker](seccion-4)
* [Sesión 5: Subsección 4: Apache Tomcat](seccion-5)

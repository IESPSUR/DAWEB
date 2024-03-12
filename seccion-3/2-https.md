---
title: 3.2 - Configuración de Servidor HTTPS en Apache
parent: 3-Administracion de servidores web
layout: default
nav_order: 2
---

# Configuración de Servidor HTTPS en Apache 2.2 sobre Linux

Configuración en el servidor Apache instalado en Ubuntu:

1. **Habilitar el servidor virtual por defecto**:
   - Utiliza el comando `sudo a2ensite default` para habilitar el servidor virtual por defecto de Apache.


2. **Habilitar el servidor virtual SSL por defecto**:
   - Habilita el módulo `mod_ssl` y el sitio `default-ssl` para configurar el servidor virtual SSL por defecto.

3. **Acceder a la URL segura para probar la configuración realizada**:
   - Accede a `https://10.33.X.3` en un navegador web y prueba la configuración realizada.

4. **Deshabilitar el servidor virtual SSL por defecto (default-ssl)**:
   - Utiliza el comando `sudo a2dissite default-ssl` para deshabilitar el servidor virtual SSL por defecto.

5. **Crear un certificado digital autofirmado con OpenSSL para el dominio claseDAW.net**:
   - Utiliza OpenSSL para generar un certificado autofirmado para el dominio `claseDAW.net`.

6. **Crear y habilitar un servidor virtual HTTPS para el dominio claseDAW.net**:
   - Crea un servidor virtual HTTPS con el directorio raíz en `/var/www/claseDAW/` y configura el log de errores en `/var/log/apache2/claseDAW.error.log` y el log de accesos en `/var/log/apache2/claseDAW.access.log` con formato `combined`.

Para realizar estos pasos, asegúrate de tener privilegios de administración en la sesión de Ubuntu XX.
Apache es un servidor modular, lo que significa que su funcionalidad puede extenderse mediante módulos adicionales. Cada módulo agrupa funcionalidades y directivas que permiten su configuración. Puedes consultar los módulos disponibles en [http://httpd.apache.org/docs/2.2/mod/](http://httpd.apache.org/docs/2.2/mod/) y [http://modules.apache.org/](http://modules.apache.org/).

Existen dos tipos de módulos en Apache:
- **Módulos estáticos:** Se incluyen durante la compilación de Apache.
- **Módulos dinámicos:** Se cargan al iniciar el servidor.

Durante la compilación, Apache incluye un conjunto básico de módulos en el servidor. Además, si se compila con la opción DSO (Dynamic Shared Object), se pueden cargar módulos dinámicos mediante la directiva `LoadModule`.

La directiva `<IfModule nombre_modulo>` `</IfModule>` permite especificar directivas que se aplicarán si el módulo indicado está cargado.

## Reinicio del Servidor

Es crucial reiniciar el servidor para aplicar los cambios realizados.

```
sudo service apache2 reload
```

O parar y arrancar el servidor de nuevo

```
sudo service apache2 restart
```
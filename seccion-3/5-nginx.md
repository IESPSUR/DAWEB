---
title: 3.5 - Servidor Nginx
parent: 3 - Administracion de servidores web
layout: default
nav_order: 5
---
# ¿Cómo configurar Nginx para securizar un sitio web?

Configurar un certificado SSL en Nginx es un proceso esencial para asegurar la comunicación entre tu servidor y los usuarios. A continuación, se detallan los pasos para realizar esta configuración:

### Paso 1: Obtener un certificado SSL

Puedes obtener un certificado SSL de una autoridad certificadora (CA) como Let's Encrypt, Comodo, DigiCert, etc. Aquí usaremos Let's Encrypt con Certbot, una herramienta que facilita la obtención y renovación de certificados SSL.

### Paso 2: Instalar Certbot

Para instalar Certbot y el complemento Nginx en una distribución basada en Debian/Ubuntu, utiliza los siguientes comandos:

```sh
sudo apt update
sudo apt install certbot python3-certbot-nginx
```

### Paso 3: Obtener el certificado SSL

Ejecuta el siguiente comando para obtener el certificado SSL y configurar Nginx automáticamente:

```sh
sudo certbot --nginx
```

Este comando te guiará a través del proceso de configuración y pedirá la información necesaria para generar y configurar el certificado SSL.

### Paso 4: Verificar la configuración de Nginx

Certbot debería configurar Nginx automáticamente. Para verificar que la configuración es correcta, abre el archivo de configuración de tu sitio en Nginx. Por ejemplo:

```sh
sudo nano /etc/nginx/sites-available/default
```

Deberías ver algo similar a esto en el bloque del servidor:

```nginx
server {
    listen 80 default_server;
    listen [::]:80 default_server;
    server_name your_domain;

    # Redirigir HTTP a HTTPS
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl default_server;
    listen [::]:443 ssl default_server;
    server_name your_domain;

    ssl_certificate /etc/letsencrypt/live/your_domain/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/your_domain/privkey.pem;
    include /etc/letsencrypt/options-ssl-nginx.conf;
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;

    root /var/www/html;
    index index.html index.htm index.nginx-debian.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Asegúrate de reemplazar `your_domain` con tu dominio real.

### Paso 5: Probar la configuración

Después de realizar cambios en la configuración de Nginx, siempre es una buena idea probar la configuración para asegurarse de que no hay errores de sintaxis:

```sh
sudo nginx -t
```

### Paso 6: Recargar Nginx

Si la prueba de configuración es exitosa, recarga Nginx para aplicar los cambios:

```sh
sudo systemctl reload nginx
```

### Paso 7: Configuración de renovación automática

Certbot configura automáticamente una tarea cron para renovar los certificados antes de que expiren. Puedes verificar si la renovación automática está configurada correctamente:

```sh
sudo systemctl status certbot.timer
```

### Solución de problemas

1. **Puertos 80 y 443 bloqueados**: Asegúrate de que los puertos 80 y 443 estén abiertos en tu firewall.
2. **Configuración incorrecta**: Verifica la configuración de Nginx y asegúrate de que los archivos de certificado y clave estén en las rutas correctas.
3. **Permisos de archivos**: Asegúrate de que los archivos de certificado y clave tengan los permisos adecuados para ser leídos por Nginx.

Siguiendo estos pasos, deberías poder configurar un certificado SSL en Nginx correctamente.

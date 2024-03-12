---
nav_order: 4
title: 4.4-Acceso a la Interfaz Web de Tomcat
layout: default
parent: 4-Administracion de servidores de aplicaciones web
---

# Paso 4 — Acceso a la Interfaz Web

Ahora que el servicio Tomcat está en ejecución, puedes configurar el firewall para permitir conexiones a Tomcat. Luego, podrás acceder a su interfaz web.

Tomcat utiliza el puerto 8080 para aceptar solicitudes HTTP. Ejecuta el siguiente comando para permitir el tráfico en ese puerto:

```
sudo ufw allow 8080
```

En tu navegador, ahora puedes acceder a Tomcat navegando a la dirección IP de tu servidor:

```
http://tu_direccion_ip_del_servidor:8080
```

Verás la página de bienvenida predeterminada de Tomcat:

![Pagina Inicial de Tomcat](imagenes/tomcat-2.png)



Ahora has verificado que el servicio de Tomcat está funcionando.
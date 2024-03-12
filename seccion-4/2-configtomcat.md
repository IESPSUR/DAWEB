---
nav_order: 2
title: Configuración de Credenciales de Tomcat
layout: default
parent: 5-Administracion de servidores de aplicaciones web
---

# Paso 2 — Configuración de Usuarios Administradores

Para obtener acceso a las páginas Manager y Host Manager, definirás usuarios privilegiados en la configuración de Tomcat. Necesitarás eliminar las restricciones de dirección IP, que impiden que todas las direcciones IP externas accedan a esas páginas.

Los usuarios de Tomcat se definen en /opt/tomcat/conf/tomcat-users.xml. Abre el archivo para editarlo con el siguiente comando:

```
sudo nano /opt/tomcat/conf/tomcat-users.xml
```

Agrega las siguientes líneas antes de la etiqueta de cierre:

```
<role rolename="manager-gui" />
<user username="manager" password="contraseña_del_manager" roles="manager-gui" />

<role rolename="admin-gui" />
<user username="admin" password="contraseña_del_admin" roles="manager-gui,admin-gui" />
```

Reemplaza las contraseñas resaltadas con las tuyas propias. Cuando hayas terminado, guarda y cierra el archivo.

Aquí defines dos roles de usuario, manager-gui y admin-gui, que permiten el acceso a las páginas Manager y Host Manager, respectivamente. También defines dos usuarios, manager y admin, con roles relevantes.

Por defecto, Tomcat está configurado para restringir el acceso a las páginas de administración, a menos que la conexión provenga del propio servidor. Para acceder a esas páginas con los usuarios que acabas de definir, necesitarás editar archivos de configuración para esas páginas.

Para eliminar la restricción de la página Manager, abre su archivo de configuración para editarlo:

```
sudo nano /opt/tomcat/webapps/manager/META-INF/context.xml
```

Comenta la definición de Valve, como se muestra:

```
<Context antiResourceLocking="false" privileged="true" >
  <CookieProcessor className="org.apache.tomcat.util.http.Rfc6265CookieProcessor"
                   sameSiteCookies="strict" />
<!--  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
  <Manager sessionAttributeValueClassNameFilter="java\.lang\.(?:Boolean|Integer|Long|Number|String)|org\.apache\.catalina\.filters\.Csrf>
</Context>
```

Guarda y cierra el archivo, luego repite para Host Manager

```
sudo nano /opt/tomcat/webapps/host-manager/META-INF/context.xml
```

Ahora has definido dos usuarios, manager y admin, que luego utilizarás para acceder a partes restringidas de la interfaz de administración. Ahora crearás un servicio systemd para Tomcat.
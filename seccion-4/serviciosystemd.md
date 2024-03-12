---
nav_order: 3
title: Creación de un servicio systemd Tomcat
layout: default
parent: 5-Administracion de servidores de aplicaciones web
---

# Paso 3 — Creación de un servicio systemd

El servicio systemd que crearás ahora mantendrá Tomcat en funcionamiento silenciosamente en segundo plano. El servicio systemd también reiniciará automáticamente Tomcat en caso de un error o fallo.

Tomcat, siendo una aplicación Java en sí misma, requiere que el tiempo de ejecución de Java esté presente, lo cual instalaste con el JDK en el paso 1. Antes de crear el servicio, necesitas saber dónde se encuentra Java. Puedes buscarlo ejecutando el siguiente comando:

```
sudo update-java-alternatives -l
```

La salida será similar a esta:

```
java-1.11.0-openjdk-amd64      1111       /usr/lib/jvm/java-1.11.0-openjdk-amd64
```

Toma nota de la ruta donde reside Java, listada en la última columna. Necesitarás la ruta en breve para definir el servicio.

Guardarás el servicio tomcat en un archivo llamado tomcat.service, en /etc/systemd/system. Crea el archivo para editarlo ejecutando:

```
sudo nano /etc/systemd/system/tomcat.service
```

Agrega las siguientes líneas:

```
[Unit]
Description=Tomcat
After=network.target

[Service]
Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64"
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"
Environment="CATALINA_BASE=/opt/tomcat"
Environment="CATALINA_HOME=/opt/tomcat"
Environment="CATALINA_PID=/opt/tomcat/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target
```

Modifica el valor resaltado de JAVA_HOME si difiere del que anotaste anteriormente.

Aquí, defines un servicio que ejecutará Tomcat mediante los scripts de inicio y apagado que proporciona. También estableces algunas variables de entorno para definir su directorio base (que es /opt/tomcat como antes) y limitar la cantidad de memoria que el JVM de Java puede asignar (en CATALINA_OPTS). En caso de falla, el servicio de Tomcat se reiniciará automáticamente.

Cuando hayas terminado, guarda y cierra el archivo.

Recarga el daemon de systemd para que sea consciente del nuevo servicio:

```
sudo systemctl daemon-reload
```

Luego, puedes iniciar el servicio de Tomcat escribiendo:

```
sudo systemctl start tomcat
```

Después, mira su estado para confirmar que se inició correctamente:

```
sudo systemctl status tomcat
```

La salida se verá así:
```
● tomcat.service - Tomcat
     Loaded: loaded (/etc/systemd/system/tomcat.service; disabled; vendor preset: enabled)
     Active: active (running) since Fri 2022-03-11 14:37:10 UTC; 2s ago
    Process: 4845 ExecStart=/opt/tomcat/bin/startup.sh (code=exited, status=0/SUCCESS)
   Main PID: 4860 (java)
      Tasks: 15 (limit: 1132)
     Memory: 90.1M
     CGroup: /system.slice/tomcat.service
             └─4860 /usr/lib/jvm/java-1.11.0-openjdk-amd64/bin/java -Djava.util.logging.config.file=/opt/tomcat/conf/logging.properties ...
```

Presiona 'q' para salir del comando.

Para habilitar que Tomcat se inicie con el sistema, ejecuta el siguiente comando:

```
sudo systemctl enable tomcat
```

En este paso, identificaste dónde reside Java y habilitaste systemd para ejecutar Tomcat en segundo plano. Ahora accederás a Tomcat a través de tu navegador web.
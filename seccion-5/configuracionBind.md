---
nav_order: 2
title: Bind9 servidor caché DNS
layout: default
parent: 6-Servicios de nombres de dominio

---

# Configuración de BIND9 como Servidor DNS y Configuración del Cliente

En esta guía, aprenderás cómo configurar BIND9 como servidor DNS en un sistema Linux y cómo configurar un cliente para utilizar este servidor DNS.

## 1. Instalación de BIND9

BIND9 es un software de servidor DNS de código abierto y ampliamente utilizado en sistemas Linux. Para instalarlo, ejecuta el siguiente comando en la terminal de tu servidor:

```
sudo apt update
sudo apt install bind9
```

## 2. Modificación del Archivo `named.conf.options`

Después de la instalación, necesitamos configurar BIND9 para utilizar servidores DNS externos como forwarders. Esto se realiza modificando el archivo de configuración `named.conf.options`, típicamente ubicado en `/etc/bind/named.conf.options`. Agrega los siguientes forwarders:

```
forwarders {
    2.2.2.2;
    8.8.4.4;
};
```

## 3. Configuración del Cliente

En el equipo cliente, necesitamos configurar la conexión de red para que utilice nuestro servidor DNS. Esto se hace generalmente a través de la configuración de red del sistema operativo, donde debes especificar la dirección IP del servidor BIND9 como el servidor DNS predeterminado.

## 4. Verificación de la Conexión

Para asegurarnos de que la configuración funcione correctamente, podemos realizar una consulta DNS desde el cliente utilizando el comando `dig`. Por ejemplo, para consultar el registro A del sitio web "www.marca.com", ejecuta el siguiente comando en la terminal del cliente:

```
dig www.marca.com
```

Este comando debería devolver la dirección IP asociada con `www.marca.com`, confirmando que la conexión a Internet y la resolución DNS a través de nuestro servidor BIND9 están funcionando correctamente.

Con estos pasos, has configurado BIND9 como servidor DNS y configurado correctamente tu cliente para utilizarlo como servidor DNS predeterminado. Esto proporciona una forma eficaz y fiable de resolver nombres de dominio en direcciones IP en tu red.


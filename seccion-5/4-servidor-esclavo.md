---
nav_order: 4
title: 5.4 - Bind9 servidor esclavo DNS
layout: default
parent: 5 - Servicios de nombres de dominio

---
# Servidor DNS esclavo 

Un servidor DNS esclavo es aquel que para resolver las consultas de direcciones debe hacer las peticiones a un servidor maestro ya que por sí mismo no contiene ningún registro. Su función principal es reducir la carga del servidor maestro, de forma que el esclavo es el que resuelve las consultas de los usuarios, evitando que el maestro haga esta tarea.

## 1. Configuración de un DNS esclavo
Para configurar un DNS esclavo lo único que debemos hacer es indicar quién es el servidor maestro de su zona y en el archivo de configuración del maestro añadir al esclavo.

En resumen, debemos tocar tres archivos diferentes, dos en el maestro y una en el esclavo.

## En el maestro modificaremos los archivos

`/etc/bind/db.aula129.org`
Añadiendo el nuevo servidor esclavo
```bash
// Añadir línea en /etc/bind/db.aula129.org del maestro
....
IN NS dns.aula129.org.
IN NS dns2.aula129.org. // Nueva línea
.... 
```

`/etc/bind/192.rev`
```bash
....
IN NS dns.aula129.org.
IN NS dns2.aula129.org. // Nueva línea
....
```
## En el esclavo modificaremos el archivo
`/etc/bind/named.conf.local`
Aquí en `type` indicamos que es esclavo y además añadimos a qué maestro debe hacer las peticiones
```bash
// Añadir en /etc/bind/named.conf.local del esclavo
zone "aula129.org" {
type slave;
file "/etc/bind/db.aula129.org";
masters { 192.168.1.200; };
};

zone "1.168.192.in-addr.arpa" {
type slave;
file "/etc/bind/192.rev";
masters { 192.168.1.200; };
}; 
```

De forma optativa, en el servidor maestro podemos añadir la línea `also-notify` para que se mantenga sincronizado de forma que cuando haya un cambio de zona, pase del maestro al esclavo
```bash
// Archivo /etc/bind/named.conf.local del maestro
zone "aula129.org" {
type master;
file "/etc/bind/db.aula129.org";
also-notify {ip_del_esclavo;}
};

zone "1.168.192.in-addr.arpa" {
type master;
file "/etc/bind/192.rev";
also-notify {ip_del_esclavo;}
};
```


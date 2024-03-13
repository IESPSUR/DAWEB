---
nav_order: 3
title: 5.3 - Bind9 servidor maestro DNS
layout: default
parent: 5 - Servicios de nombres de dominio

---
# Servidor DNS maestro 

El servidor maestro DNS hace las funciones de resolución de direcciones, de forma que cuando un servidor caché le lanza una consulta, este la resuelve y le devuelve el nombre de dominio correspondiente a la dirección IP que recibió. Este servidor es el que almacena los registros de zona DNS para un dominio específico, además tiene la capacidad de modificar los registros de zona.

## 1. Configuración de un DNS maestro
Para configurar un servidor DNS maestro debemos indicarlo en el archivo `/etc/bind/named.conf.local` añadiendo el tipo `master` como se indica en el código siguiente.
```bash
// Añadir en /etc/bind/named.conf.local
// Archivo para búsquedas directas
zone "zona4.org" {
type master;
file "/etc/bind/db.zona4.org";
};

// Archivo para búsquedas inversas
zone "129.168.192.in-addr.arpa" {
type master;
file "/etc/bind/192.rev";
}; 
```

A continuación, es necesario crear los archivos `db.zona4.org` y `192.rev` e indicar en ellos los equipos y direcciones de la red local. En el bloque de código siguiente se muestra un ejemplo de cómo se desarrolla el archivo db.zona4.org. Se puede dividir en tres bloques, el primero son los parámetros relacionados con el funcionamiento de DNS en cuanto actualización, periodos de reintento y versión, en el segundo bloque se declara el servidor maestro, que sería `equipo00` y en el último bloque se declaran el resto de equipos de la red local.

```bash
;
; BIND data file for zona4.org
;
$TTL    1D
@ IN SOA zona4.org. root.zona4.org. (
        1 ; Serial
        604800 ; Refresh
        86400 ; Retry
        2419200 ; Expire
        604800 ) ; Default TTL

; Servidores DNS del dominio
        IN      NS      equipo00.zona4.org.

; Hosts
equipo00 IN A 192.168.129.200
equipo01 IN A 192.168.129.201
equipo02 IN A 192.168.129.202
equipo03 IN A 192.168.129.203
equipo04 IN A 192.168.1.204
equipo05 IN A 192.168.1.205
equipo06 IN A 192.168.1.206
equipo07 IN A 192.168.1.207
equipo08 IN A 192.168.1.208
equipo09 IN A 192.168.1.209
equipo10 IN A 192.168.1.210

; Alias
www IN A 192.168.1.200
```

El último paso es crear el archivo de búsqueda inversa, el cual se encargará de hacer consultas de IP a nombre, para esto creamos el archivo `192.rev` como mencionamos anteriormente.

El archivo de búsqueda inversas tiene los mismos blosques que el archivo de búsqueda directa, cambiando sólo la forma en la que se declara la zona en el primer bloque y los equipos en el tercero. En este caso el último triplete de la dirección IP de cada equipo es el que los identifica dentro de la red.

```bash
;
; BIND reverse data file for 192.168.1.0
;
$TTL    1D
@ IN SOA 1.168.192.in-addr.arpa. root.aula129.org. (
        1 ; Serial
        604800 ; Refresh
        86400 ; Retry
        2419200 ; Expire
        604800 ) ; Default TTL

        IN      NS      equipo00.aula129.org.

200 IN PTR equipo00.aula129.org.
201 IN PTR equipo01.aula129.org.
202 IN PTR equipo02.aula129.org.
203 IN PTR equipo03.aula129.org.
204 IN PTR equipo04.aula129.org.
205 IN PTR equipo05.aula129.org.
206 IN PTR equipo06.aula129.org.
207 IN PTR equipo07.aula129.org.
208 IN PTR equipo08.aula129.org.
209 IN PTR equipo09.aula129.org.
210 IN PTR equipo10.aula129.org.
211 IN PTR equipo11.aula129.org.
200 IN PTR www.aula129.org.
```
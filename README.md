# Detección de equipos, puertos, servicios y vulnerabilidades

## Indice

> * [WHOIS, DomainTools y DNSrecon](#whois-domaintools-y-dnsrecon)
> * [Nmap con scripts y Nikto](#nmap-con-scripts-y-nikto)
> * [Wfuzz y Dirb](#wfuzz-y-dirb)
> * [Searchsploit](#searchsploit)

En esta práctica vamos a obtener información  sobre las máquinas del laboratorio de vulnerabilidades (***DVWA, bWAPP, Multillidae II***).

## WHOIS, DomainTools y DNSrecon

**WHOIS** es una herramienta que no ofrece información sobre una ip o dominio, como dominio registrado, fecha de creación y de actualización del dominio, información sobre servidores, etc:

![WHOIS](Imagenes/1.png)

Se puede utilizar mediante comandos o mediante web:

![WHOIS](Imagenes/2.png)

![WHOIS](Imagenes/3.png)

![WHOIS](Imagenes/4.png)

**DomainTools** es otra herramienta que ofrece información sobre ips o dominios como sus servidores localizacion de estos, ips asociadas, etc:

![DomainTools](Imagenes/5.png)

**DNSrecon** permite obtener información sobre los registros DNS, también permite hacer ***reverse lookup*** (Obtener dominio mediente una ip):

![DNSrecon](Imagenes/6.png)

![DNSrecon](Imagenes/7.png)

## Nmap con scripts y Nikto

Antes de hacer escaneo de puertos con **Nmap** y **Nikto** podemos comprobar los propios puertos que se encuentra abiertos en mi equipo, si revisamos el **docker-compose.yml** que utilizamos para levantar máquinas vulnerables:

El 8000, 8001, 81, 82 y 389:

![DNSrecon](Imagenes/8.png)

![DNSrecon](Imagenes/9.png)

![DNSrecon](Imagenes/10.png)

![DNSrecon](Imagenes/11.png)

Ahora vamos a realizar un escaneo con nmap, ademas de los puertos abiertos, también nos aparecen los servicios asociados y sus versiones, algunos de los puertos que aparecen son de otros servicios diferentes a los de las máquinas vulnerables:

![DNSrecon](Imagenes/12.png)

Vamos a realizar una escaneo con la herramienta **Nikto** 

![DNSrecon](Imagenes/16.png)

Obtenemos mucha información, como directorios que deberian estar ocultos pero están públicos:

![DNSrecon](Imagenes/17.png)

Secciones de las páginas que son vulnerables a **Inclusión remota de fichero**:

![DNSrecon](Imagenes/18.png)

O ***Backdoors***:

![DNSrecon](Imagenes/19.png)

Con *nmap* también podemos hacer una búsqueda de las vulnerabilidades que puedan tener las máquinas:

![DNSrecon](Imagenes/13.png)

Nos aparecen posibles vulnerabilidades en *Multillidae II*, como posibles archivos con información sensible o de administrador:

![DNSrecon](Imagenes/14.png)

Y en *DVWA*, como posibles directorios de administrador públicos o el archivo *robots.txt*:

![DNSrecon](Imagenes/15.png)

## Wfuzz y Dirb

Vamos a utilizar **wfuzz* para encontrar directorios en los diferentes servicios:

![DNSrecon](Imagenes/20.png)

Encontamos varios como '*data*', '*images*' o '*passwords*' entre otros.

La información que obtenemos con la herramienta **dirb** es parecida a la extraida con **Wfuzz**:

![DNSrecon](Imagenes/21.png)

## Searchsploit

Con **Searchsploit** podemos realizar búsquedas de exploits, para realizar la explotación de vlnerabilidades:

Podemos buscar por código **CVE** en concreto:

![DNSrecon](Imagenes/22.png)

O también podemos buscar exploits por la versión del kernel o de sudo entre otros:

![DNSrecon](Imagenes/23.png)

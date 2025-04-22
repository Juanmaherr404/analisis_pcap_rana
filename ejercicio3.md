# EJERCICIO 3

## APT4711 envió un correo de spear phishing a Krusty (192.168.0.54) el 18 de marzo

## Nota: Krusty usa IMAP cifrado con SSL (TCP 993) hacia imap.google.com, por lo que no podemos inspeccionar el contenido del correo. Sin embargo, sabemos que Krusty abrió el archivo adjunto a las 10:35:36 UTC, lo que provocó la descarga de un software de Comando y Control (C2).

## ¿Desde qué IP y puerto TCP se descargó el software C2?

1. Filtramos por tiempo con el filtro **ip.dst== 192.168.0.54 && frame.time >= "2015-03-18 11:35:00" && frame.time <= "2015-03-18 11:36:00"**

2. Vemos que hay mucho trafico con la **ip 103.10.197.187 y el puerto TCP 2703**

<img src="./r3_1.png>

## ¿Qué tipo de canal de Comando y Control (C2) se estableció desde la computadora de Krusty a un servidor en Hong Kong después de que el software C2 fue descargado y ejecutado



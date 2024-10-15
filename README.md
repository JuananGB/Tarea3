# Tarea 3.

## Paso 1. Descargar la imagen 'httpd' y comprobar que está en el equipo

```bash
docker pull httpd:2.4
```
+ Se descarga la imagen de Apache con la etiqueta 2.4

-Comprobar si la imagen está en el equipo y listamos:

```bash
docker images | grep httpd
```

## Paso 2. Crear un contenedor con el nombre 'dam_web1'

```bash
docker run --name dam_web1 -d -p 8000:80 httpd:2.4
```
* Se crea un contenedor **dam_web1** basado en la imagen de Apache **httpd:2.4**
* Se asigna el puerto **8000** del host al puerto **80** del contenedor para poder acceder al servidor desde el navegador

-Comprobar que funcione: 

```bash
docker ps | grep dam_web1
```

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

## Paso 3. Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?

### Utiliza bind mount para que el directorio del apache2 'htdocs' esté montado un directorio que tu elijas.

* Abrir el navegador y escribir en el navegador **http://localhost:8000** ,si todo va bien deberías ver un texto con las palabras **It works¡** en tu navegador

```bash
docker run --name dam_web1 -d -p 8000:80 -v $(pwd)/html:/usr/local/apache2/htdocs/ httpd:2.4
```
- Guardamos en la carpeta que creamos con nombre **html** lo que esta almacenado en la carpeta **/htdocs** .Podremos manipurarla desde el host.

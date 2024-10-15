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
* Guardamos en la carpeta que creamos con nombre **html** lo que esta almacenado en la carpeta **/htdocs** .Podremos manipurarla desde el host.

-Borré con anterioridad el contenedor dam_web1 usando:

```bash
docker rm dam_web1
```

## Paso 4.Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador

```bash
echo "<h1>Hola Mundo</h1>" > html/index.html
```

* Dentro del directorio **/html** creamos un archivo **index.html** con un mensahe "Hola Mundo". Si todo va bien lo podremos visualizar en el navegador .

**Tuve que acceder en modo superusuario porque no tenía permisos**

## Paso 5.Crea otro contenedor 'dam_web2' con el mismo bind mount y a otro puerto, por ejemplo 9080.

```bash
docker run --name dam_web2 -d -p 9080:80 -v $(pwd)/html:/usr/local/apache2/htdocs/ httpd:2.4
```
* Hacemos lo mismo pero con un nombre de contenedor y puerto del host diferentes.

## Paso 6.Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador:

   **http://localhost:9080**

   **http://localhost:8000**

## Paso 7. Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página

```bash
echo "<h1>SXE</h1>" > html/index.html # Crea el archivo con el contenido inicial
echo "<h2>Tarea3</h2>" >> html/index.html # Agrega la segunda línea al archivo
```




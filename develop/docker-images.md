# docker-images

Cual es la diferencia con las imágenes de Docker.

## Imagenes

Las imágenes de docker por lo regular están basadas en el mas reciente y estable sistema operativo con Debian. Es una imagen completa de ese sistema operativo.

En DockerHub las imágenes son etiquetadas como stretch, buster o jessie para las diferentes versiones de Debian. 

Para las versiones de Debian 10.4 se usa el nombre “Buster”, para todas la versiones 9 se llama “Stretch” y para las variaciones de la version 8 el nombre clave es “Jessie”.

Para las futuras versiones de Debian serán “Bullseye” y “Brookworm”

### slim 
En esta imagen generalmente solo se instalan los paquetes mínimos necesarios para ejecutar su herramienta en particular. Al dejar de lado las herramientas menos utilizadas, la imagen es más pequeña. Se usa está imagen si tiene limitaciones de espacio y no necesita la versión completa.

### alpine 
Las imágenes de Alpine se basan en el proyecto Alpine Linux, que es un sistema operativo creado específicamente para su uso dentro de contenedores. Durante mucho tiempo, estas fueron las variaciones de imagen más populares debido a su pequeño tamaño. 

Sin embargo, algunos equipos se están alejando de alpine porque estas imágenes pueden causar problemas de compatibilidad que son difíciles de depurar. La razón principal para usar una imagen Alpine es hacer que la imagen resultante sea lo más pequeña posible. 

> La imagen base tendrá un tamaño inferior a 5 MB. 

Esta imagen es la más recomendada si el espacio es una preocupación. La desventaja es que no contiene algunos paquetes que podrías necesitar. Principalmente, utiliza una lib `musl` más delgada en lugar de `glibc`. Puede tener problemas si su aplicación tiene requisitos libc específicos.

### window server core 

Se usa si la aplicación se ejecuta solo en Windows o Windows Server.

### Tamaño de imagen

Comparando el tamaño de las imágenes de Docker.

```php
docker pull --quiet python:3.8
docker pull --quiet python:3.8.3
docker pull --quiet python:3.8.3-slim
docker pull --quiet python:3.8.3-alpine
docker images 
```

Peso de las imagenes:

```php
python				3.8.3-slim				165MB
python				3.8						934MB
python				3.8.3					934MB
python				3.8.3-alpine			78.9MB
```

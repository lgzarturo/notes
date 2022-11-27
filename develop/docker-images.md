# docker-images

Cual es la diferencia con las imágenes de Docker.

## Imagenes

Las imágenes de docker por lo regular están basadas en el mas reciente y estable sistema operativo con Debian. Es una imagen completa de ese sistema operativo.

En DockerHub las imágenes son etiquetadas como stretch, buster o jessie para las diferentes versiones de Debian. 

Para las versiones de Debian 10.4 se usa el nombre “Buster”, para todas la versiones 9 se llama “Stretch” y para las variaciones de la version 8 el nombre clave es “Jessie”.

Para las futuras versiones de Debian serán “Bullseye” y “Brookworm”

- slim
- alpine
- window servercore

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

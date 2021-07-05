---
author: "Arturo López"
title: "Buenas prácticas con Wordpress"
date: 2020-12-15
description: "Este es un listado de ideas y sugerencias para mejorar el rendimiento de un sitio web con Wordpress"
tags: ["tips", "rendimiento", "seguridad"]
categories: ["programación"]
series: ["Wordpress"]
favorite: true
type: "post"
---

![Wordpress plugins](https://i.imgur.com/WK3wdDD.png "Lista de recomendaciones para sitios con Wordpress")

Listado de actividades y plugins recomendados para tener un sitio web en WordPress funcionando de manera optima.

## Recomendaciones de Wordpress

- [ ] Crear una cuenta de administrador y el usuario admin ponerlo como editor.
- [ ] Crear una cuenta de [CloudFlare](https://wordpress.org/plugins/cloudflare/) para mejorar el rendimiento de la respuesta del sitio (DNS) y tener un Servicio de Caché automático.
  - [Autoptimize](https://wordpress.org/plugins/autoptimize/)
  - [SG Optimizer](https://wordpress.org/plugins/sg-cachepress/)
  - [WP Cloudflare Super Page Cache](https://wordpress.org/plugins/wp-cloudflare-page-cache/)
- [ ] Instalar el plugin [W3 Total Cache](https://wordpress.org/plugins/w3-total-cache/).
- [ ] Instalar el plugin [EWWW Image Optimizer](https://wordpress.org/plugins/ewww-image-optimizer/) para optimizar y comprimir las imágenes del sitio.
- [ ] Instalar el plugin [GTMetrix](https://wordpress.org/plugins/gtmetrix-for-wordpress/) para revisar los resultados de la optimización.
- [ ] Borrar todos los plugins y temas innecesarios.
- [ ] Reducir el sistema de versiones de los artículos.
- [ ] Reducir el tiempo de la papelera de reciclaje.
- [ ] Activar la compresión Gzip para todo el sitio.
- [ ] Minimizar y combinar los estilos CSS y las librerías Javascript.
- [ ] Activar la caché del navegador.
- [ ] Optimizar y reparar la base de datos.
- [ ] Crear respaldos de la base de datos y del sitio cada día.
- [ ] Actualiza los plugins de Wordpress al menos 1 vez cada 3 meses, recuerda realizar un respaldo antes de realizar la actualización de los plugins.

## Plugins de Wordpress en los Sitios Web

### [Captcha](https://wordpress.org/plugins/advanced-nocaptcha-recaptcha/)

Pone un método de seguridad en los formularios para determinar que quien envió el formulario es un usuario y no un robot.

### [Contact Form Manager](https://wordpress.org/plugins/contact-form-manager/)

Este plugin sirve para la creación de formularios dentro de contacto.

### [Limitador de intentos de login](https://wordpress.org/plugins/limit-login-attempts-reloaded/)

Sirve para mejorar la seguridad mediante un contador de intentos fallidos de acceso al panel de administración.

### [Pods – Custom Content Types and Fields](https://wordpress.org/plugins/pods/)

Este plugin sirve para insertar elementos embebidos dentro del contenido de las páginas. Hace uso del elemento iFrame para cargar elementos externos dentro de la página.

### [Wordfence Security](https://wordpress.org/plugins/wordfence/)

Plugin que sirve para revisar el sitio web y prevenir ataques comunes, incluye un antivirus, firewall y una base de datos que permite detectar amenazas comunes.

### [Polylang](https://wordpress.org/plugins/polylang/)

Estos dos plugins sirven para crear el contenido en otro idioma. En el caso de los sitios de grupo argos se usan para crear versiones de las páginas en ingles.

### [WP Mail SMTP by WPForms](https://wordpress.org/plugins/wp-mail-smtp/)

Este plugin sirve para hacer el envío de los formularios de contacto por medio del servicio de correo electrónico.

### [XCloner](https://wordpress.org/plugins/xcloner-backup-and-restore/)

Sirve para realizar copias de seguridad de los archivos del sitio web.

### [Google Analytics](https://wordpress.org/plugins/google-analytics-for-wordpress/)

Activar un dashboard para obtener datos sobre el tráfico en el sitio web:

- Medición demográfica y de interés.
- Medir por las URL de las campañas lanzadas.
- Crear un panel básico con las estadísticas más importantes.
- Crear reportes personalizados por trimestre.
- Filtrar nuestra dirección IP de las Estadísticas.
- Definir objetivos y alertas específicas por sitio web.

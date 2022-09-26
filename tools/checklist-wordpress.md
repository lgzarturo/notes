---
title: "Buenas prácticas con WordPress"
description: "Este es un listado de ideas y sugerencias para mejorar el rendimiento de un sitio web con WordPress"
tags: web-develop
---

![WordPress plugins][image-1]

Listado de actividades y plugins recomendados para tener un sitio web en WordPress funcionando de manera optima.

## Recomendaciones de WordPress

- [ ] Crear una cuenta de administrador y el usuario admin ponerlo como editor.
- [ ] Crear una cuenta de [CloudFlare][1] para mejorar el rendimiento de la respuesta del sitio (DNS) y tener un Servicio de Caché automático.
  - [Autoptimize][2]
  - [SG Optimizer][3]
  - [WP Cloudflare Super Page Cache][4]
- [ ] Instalar el plugin [W3 Total Cache][5].
- [ ] Instalar el plugin [EWWW Image Optimizer][6] para optimizar y comprimir las imágenes del sitio.
- [ ] Instalar el plugin [GTMetrix][7] para evaluar el rendimiento del sitio web.
- [ ] Borrar todos los plugins y temas innecesarios.
- [ ] Reducir el sistema de versiones de los artículos.
- [ ] Reducir el tiempo de la papelera de reciclaje.
- [ ] Activar la compresión Gzip para todo el sitio.
- [ ] Minimizar y combinar los estilos CSS y las librerías Javascript.
- [ ] Activar la caché del navegador.
- [ ] Optimizar y reparar la base de datos.
- [ ] Crear respaldos de la base de datos y del sitio cada día.
- [ ] Actualiza los plugins de WordPress al menos 1 vez cada 3 meses, recuerda realizar un respaldo antes de realizar la actualización de los plugins.

## Plugins de WordPress en los Sitios Web

### [Captcha][8]

Pone un método de seguridad en los formularios para determinar qué quien envió el formulario es un usuario y no un robot.

### [Contact Form Manager][9]

Este plugin sirve para la creación de formularios dentro de contacto.

### [Limitar los intentos de login][10]

Sirve para mejorar la seguridad mediante un contador de intentos fallidos de acceso al panel de administración.

### [Pods – Custom Content Types and Fields][11]

Este plugin sirve para insertar elementos embebidos dentro del contenido de las páginas. Hace uso del elemento iFrame para cargar elementos externos dentro de la página.

### [Wordfence Security][12]

Plugin que sirve para revisar el sitio web y prevenir ataques comunes, incluye un antivirus, firewall y una base de datos que permite detectar amenazas comunes.

### [Polylang][13]

Estos dos plugins sirven para crear el contenido en otro idioma. En el caso de los sitios de grupo argos se usan para crear versiones de las páginas en ingles.

### [WP Mail SMTP by WPForms][14]

Este plugin sirve para hacer el envío de los formularios de contacto por medio del servicio de correo electrónico.

### [XCloner][15]

Sirve para realizar copias de seguridad de los archivos del sitio web.

### [Google Analytics][16]

Activar un dashboard para obtener datos sobre el tráfico en el sitio web:

- Medición demográfica y de interés.
- Medir por las URL de las campañas lanzadas.
- Crear un panel básico con las estadísticas más importantes.
- Crear reportes personalizados por trimestre.
- Filtrar nuestra dirección IP de las Estadísticas.
- Definir objetivos y alertas específicas por sitio web.

[1]:	https://wordpress.org/plugins/cloudflare/
[2]:	https://wordpress.org/plugins/autoptimize/
[3]:	https://wordpress.org/plugins/sg-cachepress/
[4]:	https://wordpress.org/plugins/wp-cloudflare-page-cache/
[5]:	https://wordpress.org/plugins/w3-total-cache/
[6]:	https://wordpress.org/plugins/ewww-image-optimizer/
[7]:	https://wordpress.org/plugins/gtmetrix-for-wordpress/
[8]:	https://wordpress.org/plugins/advanced-nocaptcha-recaptcha/
[9]:	https://wordpress.org/plugins/contact-form-manager/
[10]:	https://wordpress.org/plugins/limit-login-attempts-reloaded/
[11]:	https://wordpress.org/plugins/pods/
[12]:	https://wordpress.org/plugins/wordfence/
[13]:	https://wordpress.org/plugins/polylang/
[14]:	https://wordpress.org/plugins/wp-mail-smtp/
[15]:	https://wordpress.org/plugins/xcloner-backup-and-restore/
[16]:	https://wordpress.org/plugins/google-analytics-for-wordpress/

[image-1]:	https://i.imgur.com/WK3wdDD.png "Lista de recomendaciones para sitios con WordPress"
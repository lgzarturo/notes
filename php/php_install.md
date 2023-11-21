# Configuración de PHP

Para ejecutar PHP en la maquina local uso una versión en Windows y otra en Mac.

- Windows: [Laragon](https://laragon.org/)
- Mac: [Herd](https://herd.laravel.com/)

## Configurar xDebug

> Esta configuración de xDebug solo aplica para Laragon

### Paso 1. Extensión xDebug

[Bajar la extensión de xDebug](https://xdebug.org/download) para instalarla en el servidor local de PHP.

Se requiere verificar la versión de PHP para escoger la versión de la extensión, por ejemplo: Selecciona la extensión que tiene "TS" si tu version de PHP es "PHP 5.6 VC11 TS (64 bit)"

### Paso 2. Instala la Extensión

Se necesita descomprimir la extensión y copiarla en la carpeta de extensiones de PHP.

C:\laragon\bin\php\php-8.1.10-Win32-vs16-x64\ext\php_xdebug-3.3.0alpha3-8.1-vs16-x86_64.dll

### Paso 3. Editar php.ini

Se requiere activar la extensión y agregar la configuración de xDebug en el archivo de configuración de PHP.

```ini
;extension=tidy
extension=xsl
; xDebug
zend_extension=xdebug-3.3.0alpha3-8.1-vs16-x86_64

zend_extension=opcache
opcache.enable=1
opcache.jit_buffer_size=100M
opcache.jit=tracing

; xDebug
[XDebug]
xdebug.mode = debug
xdebug.client_host = localhost
xdebug.output_dir = "C:\laragon\www\xdebug"
```

### Paso 4. Reiniciar el servidor

Ahora solo es necesario reiniciar Laragon para que los cambios efectuados se apliquen al entorno.

### Paso 5. Extensión del navegador

[xDebug helper - Edge browser](https://microsoftedge.microsoft.com/addons/detail/xdebug-helper/ggnngifabofaddiejjeagbaebkejomen)

## Referencias

- [Para un realizar un monitoreo más completo se puede usar un profiler](https://xdebug.org/docs/profiler)
- [Configurar xDebug en PhpStorm](https://www.jetbrains.com/help/phpstorm/2023.2/configuring-xdebug.html#integrationWithProduct)
- [Descargar extensión xDebug](https://xdebug.org/download)

---
title: "Como instalar MySQL en MacOS"
description: "Paso a paso de como instalar MySQL en MacOS com Homebrew"
category: database
---

Para realizar la instalación de la última versión de MySQL usa el siguiente comando:

```bash
brew install mysql
```

Si necesitas instalar una versión en particular simplemente agrega una arroba y el número de la version, por ejemplo necesito instalar la versión 5.7, entonces el comando queda de la siguiente manera:

```bash
brew install mysql@5.7
```

> Si instalas una versión especifica te recomiendo realizar la vinculación con el servicio en homebrew. Es necesario ejecutar el siguiente comando `brew link --force mysql@5.7`

Una vez que termine el proceso de instalación, podemos iniciar el proceso de la siguiente forma:

```bash
brew services start mysql
```

Ahora es necesario configurar el servidor, por default el servicio viene si una contraseña para el usuario `root`, aún en entornos de desarrollo es una mala práctica dejarlo asi, por lo tanto necesitamos protegerlo:

Ejecuta:

```bash
mysql_secure_installation
```

Simplemente es necesario responder las preguntas que solicita, para el entorno de desarrollo es recomendable poner una política de contraseñas baja.

Para detener el servicio de MySQL ejecutaremos el siguiente comando:

```bash
brew services stop mysql
```

También puedes hacer uso del modo `daemon mode`, que funciona para que el servicio de mysql se ejecute al iniciar la computadora. Si requiere iniciar o detener el servidor usa los siguientes comandos:

```bash
# para iniciar
mysql.server start

# para detener
mysql.server stop
```

Una vez que se esta ejecutando el servidor, nos podemos conectar con el siguiente comando:

```bash
mysql -u root -p
```

> Ahora solo es necesario poner la contraseña del usuario `root`.

## Eliminar el servicio de MySQL

Si requieres remover el servidor de la base de datos te recomiendo ejecutar los siguientes comandos en la terminal.

```bash
brew uninstall mysql
rm -rf /usr/local/var/mysql
rm /usr/local/etc/my.cf
```

## GUI

Si necesitas usar un administrador visual para manejar los datos de MySQL, en MacOS te recomiendo usar el programa [Sequel Pro](http://www.sequelpro.com/).

- [Sequel-Ace](https://sequel-ace.com/): Fork de Sequel Pro, funciona para nuevas versiones de MySQL

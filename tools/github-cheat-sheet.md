---
title: "Github Search Cheat Sheet"
description: "Realiza búsquedas de código más eficientes con GitHub"
---

La funcionalidad búsqueda en GitHub soporta diferentes operaciones. A continuación expongo las opciones comunes de búsqueda.

## Keyboard Shortcuts

Cuando estas en la página principal de un repositorio, puedes navegar de forma mas sencilla en el código con los siguientes accesos directos.

- Presiona `t` para abrir el exportador de archivos.
- Presiona `w` para mostrar el selector de ramas.
- Presiona `s` para poner el foco el campo de búsqueda.
- Presiona `l` para editar las etiquetas en los issues.
- Presiona `y` para cambiar la url relativa por una version permanente del archivo en el que te encuentras.

## Búsqueda de código

La búsqueda de código aplica para los archivos almacenados en las ramas de los repositorios:

- `{word} repo:charles/privaterepo` Busca solo en un determinado repositorio.
- `{word} user:heroku` Busca en los repositorios públicos de un usuario.
- `{word} extension:coffee` Busca el código filtrando por tipo de extensión.
- `{word} size:>1000` Busca en los archivos que el tamaño de archivo sea mayor a 1000kb.
- `{word} path:/docs/` Busca en el path especificado.
- `{word} fork:true` Busca en el código fuente de los repositorios fork.
- `hello NOT world` Busca la palabra `hello` pero sin la palabra `world`

## Búsqueda de usuarios

- `fullname:"Linus Torvalds"` Busca a todos los usuario con por nombre.
- `lgzarturo location:"San Francisco, CA` Busca a los usuarios por medio de su ubicación.
- `lgzarturo followers:100..200` Busca a todos los usuarios `lgzarturo` que tengan entre 100 y 200 seguidores.
- `lgzarturo repos:>10` Busca a todos los usuarios `lgzarturo` con mas de 10 repositorios.

Otras opciones de búsqueda que ofrece GitHub son las siguientes:

- Buscador de archivos en GitHub
- Búsqueda en los repositorios
- Búsqueda en los tópicos
- Búsqueda de Código
- Búsqueda en los commits
- Búsqueda en issues y pull requests
- Buscar usuarios
- Búsqueda en discusiones y el marketplace
- Búsqueda en paquetes
- Búsqueda en wikis
- Búsqueda en forks

> Para más información te recomiendo visitar la [documentación oficial de GitHub](https://docs.github.com/en/github/searching-for-information-on-github/searching-on-github) ya que puede cambiar en el futuro.

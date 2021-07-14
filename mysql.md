---
title: "Datos interesante sobre MySQL"
description: "Tipos de datos, consultas y más información sobre MySQL"
tags: databases
---

## Tipos de campo para texto

Los tipos de campo que maneja MySQL son los siguientes: TINYTEXT, TEXT, MEDIUMTEXT y LONGTEXT

Estimación del tamaño de cada tipo de campo

![Tamaño en disco](images/fields-disk-size.png)

Estimaciones máxima y mínima sobre el número de palabras

![Palabras estimadas en ingles](images/fields-estimated-words.png)

Medida en base a palabras en inglés.

![Máximo y mínimo de palabras](images/fields-worst-and-best-scenario.png)

> Notas
>
> - El número de caracteres depende del tipo de codificación.
> - Las estimaciones de multi-byte se refieren a idiomas como Geek, Arabic, Hebrew, Hindi, Thai, etc

**Referencias:**

- [Pregunta en StackOverflow](https://stackoverflow.com/questions/13932750/tinytext-text-mediumtext-and-longtext-maximum-storage-sizes/35785869#35785869)
- [Instala MySQL en MacOS X](devops/instala-mysql-para-macos.md)

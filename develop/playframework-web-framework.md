---
title: "Play Framework - Build Modern & Scalable Web Apps"
description: "Un framework que facilita la creación de aplicaciones con Java y Scala"
---

> Play Framework es un marco de aplicación web de código abierto que sigue el patrón arquitectónico modelo-vista-controlador. Está escrito en Scala y se puede usar desde otros lenguajes de programación que se compilan en JVM Bytecode, p. Java - [Wikipedia](https://en.wikipedia.org/wiki/Play_Framework)

El creador de este genial framework ([Guillaume Bort](http://guillaume.bort.fr)) lo define como: Un framework que facilita la creación de aplicaciones con Java y Scala.

Actualmente este proyecto está en la [versión 2](https://blog.playframework.com/) con soporte nativo de Scala y Java, es una distribución que aún es muy prematura, tiene muchas nuevas características, pero el enfoque de la versión 1.x de play cambia radicalmente.

Posiblemente es debido a la evolución sobre el nuevo lenguaje de moda "[SCALA](https://scala-lang.org)".

SCALA promete ser el reemplazo de Java, sin embargo, este post no profundiza en ese tema; Actualmente trabajo con varias versiones de Play (1.1, 1.1.1 y 1.2.4), estas distribuciones las encuentro muy bien definidas y con un rendimiento bastante óptimo.

La principal característica que me gusta de Play es la compilación en tiempo de ejecución, esto funciona de maravilla y es que el hecho de programar y probar los cambios se vuelve tan crucial cuando los cambios son constantes y necesitamos revisar de inmediato sin esperar la tediosa compilación y el posterior despliegue de la aplicación. Esto yo lo llamo "programación al puro estilo de php".

Play aún se encuentra muy lejos de ser popular. ¿Por qué? Mmmm... sencillo, según mi punto de vista, Play actualmente compite con grandes proyectos que están muy bien mercadeados como es el caso de Ruby and Rails, Grails o el mismo Spring, sin embargo, durante el desarrollo de la versión 1.x la popularidad viral de Play fue muy bien aceptada. Al desarrollar la versión 2 de Play el cambio fue muy agresivo, ya que parece que en realidad es otro framework más que aprender a dominar.

Una alianza con Typesafe y Scala: Durante el desarrollo de play 1.x ya se mostraban claras las tendencias de desarrollar un módulo muy completo para el soporte de Scala, al parecer Guillame Bort estaba encantado por las bondades de Scala y fue tanto el entusiasmo que lo llevó al soporte nativo en la versión 2 de Play. Particularmente yo creo que fue una buena elección, sin embargo, muchos equipos de desarrollo no se pueden dar el lujo de cambiar una infraestructura ya definida para empezar a experimentar con algo desconocido; en mi caso fue esa la problemática al querer migrar mis aplicaciones de Play a la versión 2.

Ya he comenzado a trabajar en pequeños proyectos con Play 2, sin embargo, aún me bloqueo ante lo desconocido y hay momentos que pienso que a lo mejor es tiempo de resignarse con la versión 1.2.4 o migrar con otro framework amigable como Grails. Aún estoy muy lejos de tomar alguna decisión, por lo pronto seguiremos explotando las bondades de las versiones estables.

Yo recomiendo que conozcan [Play framework](https://www.playframework.com/getting-started) y que intenten desarrollar alguna aplicación simple que les demuestre que pueden aprovechar muchas de las características que han sido muy bien pensadas y que nos ayudan a generar aplicaciones en tiempos muy cortos.

5 características que me gustan de play:

- Compilación en tiempo de ejecución.
- Soporte nativo para servicios web REST.
- La definición de rutas amigables.
- El soporte con los entornos de desarrollo (IDE) es muy bueno.
- La configuración es muy simple y solo se basa en un solo archivo "application.conf".

5 cosas que no me gustan de play:

- La documentación es buena pero muy escasa.
- Solo hay dos libros y son muy básicos.
- El rendimiento de la aplicación se ve afectado cuando se despliega en Tomcat.
- El código se queda en la carpeta del despliegue.
- El manejo de archivos blob pierde relación sobre el nombre del archivo.

## Libros

- [Practical Play Framework: Focus on what is really important (English Edition)](https://amzn.to/3gqvrjI)
- [Play for Scala: Covers Play 2](https://amzn.to/33WU9Dr)
- [Developing on Play Framework 2](https://amzn.to/3mSVqCW)

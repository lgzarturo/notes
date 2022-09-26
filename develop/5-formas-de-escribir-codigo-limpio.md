---
title: "5 Formas de escribir código limpio"
description: "Técnicas para crear código libre de errores para mejorar él mantenimiento"
tags: programming
---

## Principios básicos para crear código libre de errores

Técnicas para crear código libre de errores para mejorar él mantenimiento y asegurar una evolución sana en el desarrollo de aplicaciones.

### Buenas prácticas de programación

**¿Por qué es necesario aplicar buenas prácticas de programación?** Todo programador debería estar obligado a crear software basado en buenas prácticas de desarrollo, patrones de diseño, documentación y capacitación continua. En mi caso procuro seguir estándares establecidos, invertir tiempo en lectura sobre desarrollo de nuevas técnicas o metodologías de programación.

Siempre intento pensar como usuario y criticar todo el software que vea, para buscar la manera de cómo hacerlo mejor y formular una crítica constructiva que me deje algo en que pensar.

Es esencial adoptar buenos principios de programación y adaptarlos a la manera de crear código. En este caso puedo decir que principalmente me siento influenciado por la filosofía de Python donde sus dos principios básicos son la legibilidad y la transparencia, denominando al código que cumple estas características como "**código pythonico**".

De igual manera uno de los desarrolladores de Python Tim Peters escribió el Zen de Python, como una serie de principios que definen cómo deberían pensar los programadores:

- Bello es mejor que feo.
- Explícito es mejor que implícito.
- Simple es mejor que complejo.
- Complejo es mejor que complicado.
- Plano es mejor que anidado.
- Disperso es mejor que denso.
- La legibilidad cuenta y mucho.
- Los casos especiales nunca son tan especiales, como para quebrantar los principios.
- Lo práctico gana a la pureza.
- Los errores nunca deberían dejarse pasar silenciosamente.
- A menos que hayan sido silenciados explícitamente.
- Frente a la ambigüedad, rechaza la tentación de adivinar.
- Debería haber una -y preferiblemente solo una- manera obvia de hacerlo.
- Aunque esa manera puede no ser obvia al principio a menos que usted sea holandés.
- Ahora es mejor que nunca.
- Aunque nunca es a menudo mejor que ya mismo.
- Si la implementación es difícil de explicar, es una mala idea.
- Si la implementación es fácil de explicar, puede que sea una buena idea.
- Los espacios de nombres (**namespaces**) son una gran idea ¡Hagamos más de esas cosas!

Aplicar estos principios es más complicado de lo que parece, ya que siempre hay que tenerlos presentes al momento de estar escribiendo el código y tomar decisiones en tiempo real (por así decirlo) sobre la manera en cómo sería más conveniente aplicar. Lo ideal es crear código simple, mantenerlo simple, buscar la solución más lógica y refactorizar.

Recuerda que la práctica hace al maestro y en el caso de los programadores, mientras más código escribas más practica tendrás para refactorizar, sin embargo mientras más repites el mismo código entonces algo está haciendo mal. Para este párrafo lo mejor es aplicar los principios KISS & DRY.

### KISS (Keep It Simply Stupid)

En español "**Mantenle Sencillo, ¡Estúpido!**", es un principio que recomienda que el programador debe planear el desarrollo de código de la manera mas simple, codificando instrucciones simples, comprensibles, dividiendo el código en pequeños módulos para minimizar el código de cada módulo.

> Todo debe ser lo más simple posible, no solo simple - **Albert Einstein**.

6 pasos para aplicar el principio KISS:

- Aplica la primera solución que se te ocurra.
- Si todo funciona bien, elimina lo superfluo.
- Simplifica el resto del código.
- Documenta solo lo que no es evidente.
- Si algo no es evidente, simplificarlo debes!.
- Revisa, evalúa y vuelve a simplificar.

> La simplicidad es la sofisticación extrema - **Leonardo Da Vinci**.

### DRY (Don’t Repeat Yourself)

En español “**No te repitas**”, este principio nos hace mención a que el código escrito debe ser único y promueve la refactorización para la reducción de código duplicado. La idea de aplicar el principio es dividir los proyectos en pequeños módulos y que cada pedazo de código se pueda reutilizar de modo que no debería ser duplicada la funcionalidad.

Factores que se intentan minimizar con este principio:

- Duplicidad de código
- Disminución en la dificultad de los cambios.
- Mayor eficiencia para la evolución posterior.
- Mejorar la claridad del software.
- Evitar inconsistencias.

Sin importar los principios que el programador aplique, lo que queda claro es que son para evitar que el código se vuelva complicado y costoso de mantener o actualizar, he aquí algunos de los errores más comunes:

- Código duplicado, existe código idéntico o muy similar en más de una ubicación.
- Clases, Métodos, funciones, módulos o procedimientos demasiado grandes.
- Una lista muy grande de parámetros en un procedimiento o función empeora la legibilidad y la calidad del código.
- Una clase que usa excesivamente métodos de otra clase.
- Dependencias en detalles de implementación de otra clase.
- Una clase que sobrescribe un método de una clase base de tal manera que el contrato de la clase base no es honrado por la clase derivada.
- Clases que hacen muy poco, son consideradas como clases perezosas.
- El uso forzado de patrones de diseño demasiado complicados, donde uno más simple sería suficiente.
- Identificadores excesivamente cortos o largos. El nombre de una variable deberá reflejar su función, a menos que sea obvio.
- Excesivo uso de literales, estos deben codificarse como constantes con nombre, para mejorar la legibilidad y para evitar errores de programación.
- Código espagueti, denominado así a cualquier código con un control de flujo complejo e incomprensible. Es decir, código muy complicado de mantener y documentar que se vuelve una pesadilla hasta para su creador.

> La perfección se logra cuando no queda nada por quitar, todo lo demás viene sobrando.

### Limpieza de código

Una vez que adoptamos los principios en el desarrollo de software, solo sería necesario acostumbrarnos a la técnica de Refactorización como un método para simplificar el código.

La refactorización se aplica como una técnica para reestructurar la estructura interna del código fuente, sin cambiar su comportamiento o el resultado. Esta técnica también es usada en parte del mantenimiento de código donde no se arreglan errores, ni se añade funcionalidad y en el cual es objetivo es mejorar la comprensión del código, eliminar código muerto, para así facilitar el mantenimiento en el futuro.

Al aplicar la refactorización como un proceso separado, nos aseguramos de no introducir errores al sistema y nos ayuda a identificar posibles bugs debido a que el código estaba mal planeado, a esto se le conoce como limpieza de código.

Para más información revisa el documento en línea "[The Zen of Python][1]"

[1]:	http://www.python.org/dev/peps/pep-0020/
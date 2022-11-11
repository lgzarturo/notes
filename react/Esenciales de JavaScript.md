# Esenciales de JavaScript

La programación declarativa se describe cómo el flujo de la aplicación basado en declaraciones en vez de el flujo secuencial y lógico de la programación imperativa.

> **Imperativo** se define como una secuencia de operaciones a realizar, mientras que **Declarativo** especifica el resultado deseado y no el cómo lograrlo, la solución se obtiene mediante mecanismos internos.

Programación imperativa es:
- Estructurada
- Procedimental
- Modular

Programación declarativa es:
- Lógica
- Funcional

> “Mientras más explícito sea el código, más seguro se puede volver”

*“use script”* - El modo estricto ha sido planteado para evitar los efectos raros y de hoisting de javascript. 

Hoisting: Es el efecto que hace javascript al declarar las variables, estas son llevadas al inicio en la ejecución del script. Esto hace que se puedan referir a las variables sin importar dónde estén declaradas.

> Las variables que no hayan sido iniciadas devolverán un valor undefined, y también serán elevadas a la parte superior de la función donde se han declarado.

Contexto: hace referencia al objeto que está invocando la función, también tiene que ver con el alcance de las variables. “¿Quién es this?”

## Funciones

En javascript hay dos maneras de crear funciones, por medio de declarar la palabra clave “function” y la segunda manera es a través de expresiones, asignando la creación de una función a una variable.

Con la definición de las funciones por expresión podemos crear variables anónimas. De esta forma la función podría o no llevar un nombre, aunque es muy común que se hagan anónimas y se accedan a ellas por medio de la variable declarada.

Diferencias:
- Con la función declarativa javascript aplica hoisting y eleva a un ámbito global las funciones. Podemos invocar la función antes de ser declarada.
- Con las expresiones no aplica el efecto hoisting. No podemos invocar la función antes de ser declarada. 
- El nombre de la expresión tiene un scope local en el bloque donde fue creada la expresión.

Las arrow functions no hacen el bound del contexto, obtienen el contexto del padre donde están definidas la función flecha. 

Para todos métodos que reciben un callback o que iteran otros objetos, se debe usar una función flecha y no se deben usar como métodos, debido a que se pierde el contexto.

Para usar métodos de objetos se debe de usar la notación regular con la palabra reservada function.

3 Tipos de runtime
- Window
- Global
- Worker global scope

## Alcance

- “Let” y “Const” solo podrán ser “vistas” dentro del bloque donde son declarados. Tiene un scope de bloque.
- “Var” tiene un alcance de función, puede ser vista por todo el bloque. Tiene un scope local.

Cuando declaras una función fuera de una función se denomina como “Variable Global”, esto se debe a que dicha función queda disponible para cualquier función dentro del script actual.

Mientras, que si declaras una variable dentro de una función su alcance se denomina como “Variable Local”, ya que solo está disponible dentro de la función donde fue creada.

Un efecto no deseado puede ser modificar el valor de las variables globales, lo que puede provocar perder el estado inicial de dicha variable.

## Inmutabilidad

No hay formas de hacer inmutables los objetos, se pueden congelar propiedades, pero la inmutabilidad es algo que no está soportado en JavaScript.

> Para proteger el cambio de referencia de los objetos se puede usar la “Desestructuración”, esta técnica nos permite generar variables a partir de un objeto. 

En React se usan los props para pasar nuevas variables a los componentes.

## Asyc

JavaScript es un lenguaje single thread, tiene un modelo de sincronía basado en el ciclo de eventos, el término en inglés es “eventLoop”.

Al introducir llamadas asíncronas a la aplicación, hay que controlar los posibles errores como falla en la conexión, recursos no disponibles, latencia en las respuestas, entre otros, sin embargo con las llamadas asíncronas se pueden manejar los callbacks con then, catch y finally.

Con promises se puede hacer programación “rail road”, que es un estilo de programación donde se encadenan las promesas para generar procesos complejos.

**Async y Await** siempre van juntos, “async” nos ayudan en la definición de las funciones y “await” en la invocación, nos permite ejecutar las peticiones asíncronas como si fuera programación imperativa.

## Módulos

Los módulos nos ayudan a dividir código en piezas reusables, nos ayudan a crear encapsulación con el alcance de funciones y variables dentro del script y el export nos ayuda a compartir código fuera del módulo. 

El script solo puede tener un “export default”, sin embargo, puede tener varios “named export”.

Los named export exportan el nombre de la función o de la variable donde son definidos. 

- Se pueden exportar variables, funciones y objetos.
- Export expone las funciones, objetos y variables.
- Es una forma de abstraer el código.

## Template string

Nos ayuda a interpolar variables, ayuda a la legibilidad del código. Es una manera de componer cadenas de texto inyectando variables en las cadenas.

## Paso por referencia

- Los tipos de datos primitivos pasan el valor “por valor”.
- Las variables son referencias en memoria y los primitivos son valores.
- Las propiedades de los objetos son mutables aun usando la desestructuración, a menos que solo se obtengan los valores de sus propiedades.

## Rail road

Procesos complejos a partir de la composición de funciones con encadenamiento de las promesas, produce código declarativo, elegante y legible.

## Spread operator (…)

Nos ayuda a recorrer objetos iterables, para repartir las propiedades en un nuevo objeto sin modificar el original.

## Optional channing operator (?.)

Este operador nos ayuda a acceder a propiedades no definidas.

## Nullish coalescing operator (??)

Nos ayuda a obtener un valor por default cuando la propiedad o el objeto es indefinido o nulo.

## Libros recomendados
- Eloquent javascript.
- You don’t know JS yet series.
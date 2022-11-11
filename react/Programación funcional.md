# Programación funcional

Es un paradigma de programación, esta enfocado en crear declaración y a partir de funciones se procesan las solicitudes.

JavaScript es un lenguaje multi paradigma, ya que puedes implementar clases, estilos y técnicas para lograr los objetivos deseados.

> Los métodos map, filter, reduce en Javascript cumplen con el patron funcional.

- Map convierte valores de un origen a un destino. Produce un nuevo valor a partir de uno inicial, sin modificar el original.
- En programación funcional es necesario crear declaraciones y se basa en la composición de funciones, diciendo la lógica en acciones pequeñas que ejecuten acciones concretas para obtener el resultado esperado.
- forEach tiene como objetivo recorrer objetos iterables.
- Las Promises están basadas en un concepto de programación funcional.

## Funciones puras
Son aquellas que no pueden genera un efecto secundario, como imprimir en la consola, actualizar una variable global, hacer una llamada asincrona.

Son funciones que son consistentes y dependiendo la entrada de parámetros siempre retornan el mismo resultado.

Beneficios:
- Remover efectos secundarios.
- Composición en base a funciones.
- Desacoplamiento.
- Mayor seguridad.
- Abstraer dependencias externas.

> React es una librería declarativa que tiene sus bases en la programación funcional. Sus componentes van a comportarse como funciones puras.

## Funciones impuras
Nos permiten aplicar un patrón de division de responsabilidades para aplicar un mejor diseño de la aplicación.

“Glue Code”: Con las funciones impuras podemos hacer la programación imperativa para crear el algoritmo que genere efectos secundarios para procesar las reglas del negocio.

## Higher Order Functions
Las sentencias “return” y los “argumentos” son el mecanismos que sirven de puente para conectar las funciones puras con las impuras.

> En React todo es un flujo de información que va pasando por los componentes

En javascript las funciones son first class citizen, debido a que se pueden retornar o pasar como objetos y esto recibe el nombre de “Funciones de Alto Orden”

- Los callbacks son funciones de alto orden ya se se pueden pasar como argumentos.
- El spread operator solo realiza la copia en un solo nivel.
- En React se conocen como “Higher Order Components”.








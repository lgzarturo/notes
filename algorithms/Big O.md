# Big O

Las operaciones de ordenamiento son una operación muy constante en los proyectos, de hecho una gran parte de las aplicaciones incluyen métodos para ordenar los datos, de esta forma se podría decir que representa una gran porción de las operaciones que se ejecutan en internet.

Y es que ordenar y clasificar datos representa una parte importante de los estudios en la ciencias computacionales. 

La notación Big O, comúnmente es llamada “análisis asintótica” o “complejidad algorítmica”, esto debido a que se enfoca en medir el numero de operaciones que tarda en completar el procesamiento de una colección de datos muy grande.

Básicamente es medir la eficiencia de un algoritmo y buscar la manera de que la solución se ejecute en menos tiempo, logrando que sea eficiente y eficaz.

O - se refiere al orden de la función, para determinar su tasa de crecimiento.
n - es el numero de operaciones por ejecutar en secuencia.

> La notación Big-O es la forma de saber qué tan bueno es un algoritmo dado para resolver problemas muy grandes.

En algoritmos de ordenamiento que son usados de forma común, la mejor notación se representa como O(n log n) esto aplica para: Quick Sort, Heap Sort, and Merge Sort.

Es importante notar que no hay un solo algoritmo que sea el mas rápido o eficiente para todos los casos. Depende de los datos de entrada y de cómo se manejen los estados en el procesamiento de la información. 

On(n^2) significa que dependiendo el numero de operaciones el tiempo de procesamiento sera mas largo.

El estudio de la notación Big O, nos puede ayudar a tener en cuenta el concepto de la eficiencia en el código, medir nuestros tiempos de ejecución cuando trabajamos con una gran cantidad de datos, con el objetivo de evitar cuellos de botella, poner atención a cuando es necesario optimizar. A este proceso se le llama análisis de sensibilidad, y es parte importante para solucionar problemas y escribir mejor software.

O(1) - Tiempo constante: es el mejor resultado, y quiere decir que el tiempo de ejecución no varía conforme aumenta el tamaño de los datos de entrada, y la respuesta siempre tarda lo mismo sin importar la magnitud de entrada.

> No importa lo que proporcione como entrada al algoritmo, aún se ejecutará en la misma cantidad de tiempo.

Ejemplo:
- 1 artículo, 1 segundo
- 10 artículos, 1 segundo
- 100 artículos, 1 segundo
- Determinar si un número binario es par o impar.

O(n) - Tiempo lineal: el crecimiento es lineal en tanto el tiempo de ejecución es cada vez mayor de modo proporcional a cómo se incrementa el tamaño de la entrada. Por lo que si tenemos el doble de elementos de entrada, tardará el doble, aunque despreciamos realmente la pendiente de la misma y sólo nos quedamos con que aumenta de forma lineal.

> El tiempo de cálculo aumenta al mismo ritmo que la entrada.

Ejemplo:
- 1 artículo, 1 segundo
- 10 artículos, 10 segundos
- 100 artículos, 100 segundos
- búsqueda de lista sin ordenar.

O(log n) - tiempo logarítmico: una forma de crecimiento que crece al inicio pero tiende a estabilizarse conforme aumentan el tamaño de entrada, por lo que es una buena nota para un algoritmo ya que no tiende a resentirse.

> El tiempo de cálculo apenas aumenta a medida que aumenta exponencialmente los números de entrada.

Ejemplo: 
- 1 artículo, 1 segundo
- 10 artículos, 2 segundos
- 100 artículos, 3 segundos
- Búsqueda binaria.

O(n2) - tiempo cuadrático: el crecimiento es de forma exponencial por lo que será un algoritmo a evitar ya que para valores pequeños de entrada el tiempo será asumible, pero conforme aumente el tamaño de los datos de entrada el tiempo tenderá a ser muy elevado y es probable que el procesador se quede inoperativo.

> El tiempo de cálculo aumenta al ritmo de n^2.

Ejemplo:
- 1 artículo, 1 segundo
- 10 elementos, 100 segundos
- 100 artículos, 10.000 segundos
- Ordenamiento de burbuja.

O(n!) - tiempo factorial: el crecimiento es factorial, por lo que rápidamente tiende a valores imposibles de tratar, en lo que sería una recta vertical.

> El tiempo de cálculo aumenta al ritmo de n!, lo que significa que sí n es 5, es 5x4x3x2x1, o 120. Esto no es tan malo con valores bajos de n, pero rápidamente se vuelve imposible.

Ejemplo:
- N=1, 1 opción
- N=10, 3.628.800 opciones
- N=100, 9.332621544×10157 opciones
- Travelling salesman problem

> TSP - dada una lista de ciudades y las distancias entre cada par de ellas, ¿cuál es la ruta más corta posible que visita cada ciudad exactamente una vez y al finalizar regresa a la ciudad origen?
> En la práctica, para un problema del viajante con 5 ciudades hay (5-1)!/2=12 rutas diferentes y no necesitamos un ordenador para encontrar la mejor ruta, pero apenas aumentamos el número de ciudades las posibilidades crece factorialmente:
> Para 10 ciudades hay (10-1)!/2=181.440 rutas diferentes
> Para 30 ciudades hay más de 4·10^30 rutas posibles. Un ordenador que calcule un millón de rutas por segundo necesitaría 10^17 años para resolverlo. Dicho de otra forma, si se hubiera comenzado a calcular al comienzo de la creación del universo (hace unos 13.400 millones de años) todavía no se habría terminado.
> Puede comprobarse que por cada ciudad nueva que incorporemos, el número de rutas se multiplica por el factor N y crece factorialmente. Por ello el problema pertenece a la clase de problemas NP-completos.



# Java 11: Que debes saber:

## Tipos de Datos:

- byte:1 byte - Stores whole numbers from -128 to 127
- short:2 bytes - Stores whole numbers from -32,768 to 32,767
- int:4 bytes	Stores whole numbers from -2,147,483,648 to 2,147,483,647
- long:8 bytes - Stores whole numbers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
- float:4 bytes - Stores fractional numbers. Sufficient for storing 6 to 7 decimal digits
- double:8 bytes - Stores fractional numbers. Sufficient for storing 15 decimal digits
- boolean:1 bit - Stores true or false values
- char:2 bytes - Stores a single character/letter or ASCII values

## Casteo (Convertir tipos de datos)
- Hay 2 formas de casteo, ascendente y descendente.
	- En el ascendente es automático y va de la siguiente forma:
		byte -\> short -\> char -\> int -\> long -\> float -\> double
	- En el descendente es manual y va de la siguiente forma: 
		double -\> float -\> long -\> int -\> char -\> short -\> byte

## Operadores
### Aritméticos
```
Oper	Nombre			Descripción								Ejemplo
+ 		Addition		Adds together two values				x + y	
- 		Subtraction		Subtracts one value from another		x - y	
* 		Multiplication	Multiplies two values					x * y	
/		Division		Divides one value by another			x / y	
%		Modulus			Returns the division remainder			x % y	
++		Increment		Increases the value of a variable by 1	++x	
--		Decrement		Decreases the value of a variable by 1	--x
```

### Asignación
```
Operador		Ejemplo				Similar a:
=				x = 5				x = 5	
+=				x += 3				x = x + 3	
-=				x -= 3				x = x - 3	
*=				x *= 3				x = x \* 3	
/=				x /= 3				x = x / 3	
%=				x %= 3				x = x % 3	
&=				x &= 3				x = x & 3	
|=				x |= 3				x = x | 3	
^=				x ^= 3				x = x ^ 3	
> > =			x \>\>= 3			x = x \>\> 3	
\<\<=			x \<\<= 3			x = x \<\< 3
```

## Clase String
- String es una clase inmutable la cual consiste en una colección de caracteres.
- Las cadenas son constantes, los valores no pueden ser cambiados una vez creados.

### Metodos:

- charAt() - Retorna el carácter en el índice especificado.
- codePointAt() - Retorna el valor Unicode del carácter especificado.
- codePointBefore() - Retorna el valor Unicode del carácter anterior al especificado.
- codePointCount() - Retorna la cantidad de caracteres Unicode encontrados en la cadena.
- compareTo() - Compara 2 cadenas de forma lexicográfica.
- compareToIgnoreCase()	Compara 2 cadenas de forma lexicográfica, ignorando mayúsculas e minúsculas.
- concat() - Adjunta una cadena al final de otra cadena.
- contains() - Comprueba si una cadena contiene una secuencia de caracteres.
- contentEquals() - Comprueba si una cadena contiene exactamente la misma secuencia de caracteres del CharSequence o StringBuffer.
- copyValueOf() - Returns a String that represents the characters of the character array.
- endsWith() - Checks whether a string ends with the specified character(s).
- equals() - Compare two strings. Returns true if the strings are equal, and false if not.
- equalsIgnoreCase() - Compares two strings, ignoring case considerations.
- format() - Returns a formatted string using the specified locale, format string, and arguments.
- getBytes() - Encodes this String into a sequence of bytes using the named charset, storing the result into a new byte array.
- getChars() - Copies characters from a string to an array of chars.
- hashCode() - Returns the hash code of a string.
- indexOf() - Returns the position of the first found occurrence of specified characters in a string.
- intern() - Returns the canonical representation for the string object.
- isEmpty() - Checks whether a string is empty or not.
- lastIndexOf() - Returns the position of the last found occurrence of specified characters in a string.
- length() - Returns the length of a specified string.
- matches() - Searches a string for a match against a regular expression, and returns the matches.
- offsetByCodePoints() - Returns the index within this String that is offset from the given index by codePointOffset code points.
- regionMatches() - Tests if two string regions are equal.
- replace() - Searches a string for a specified value, and returns a new string where the specified values are replaced.
- replaceFirst() - Replaces the first occurrence of a substring that matches the given regular expression with the given replacement.
- replaceAll() - Replaces each substring of this string that matches the given regular expression with the given replacement.
- split() - Splits a string into an array of substrings.
- startsWith() - Checks whether a string starts with specified characters.
- subSequence() - Returns a new character sequence that is a subsequence of this sequence.
- substring() - Returns a new string which is the substring of a specified string.
- toCharArray() - Converts this string to a new character array.
- toLowerCase() - Converts a string to lowercase letters.
- toString() - Returns the value of a String object.
- toUpperCase() - Converts a string to upper case letters.
- trim() - Removes whitespace from both ends of a string.
- valueOf() - Returns the string representation of the specified value.

Caracteres especiales:
```
Escape character	Result	Description
\'		'			Single quote
\"		"			Double quote
\\		\			Backslash
```


## Clase Math.
> Clase de Java la cual contiene métodos para realizar operaciones matemáticas básicas, exponenciales, logarítmicas, cuadráticas y trigonométricas.

- abs(x) - Returns the absolute value of x (double|float|int|long)
- acos(x) - Returns the arccosine of x, in radians.
- asin(x) - Returns the arcsine of x, in radians.
- atan(x) - Returns the arctangent of x as a numeric value between -PI/2 and PI/2 radians.
- atan2(y,x) - Returns the angle theta from the conversion of rectangular coordinates (x, y) to polar coordinates (r, theta).
- cbrt(x) - Returns the cube root of x.
- ceil(x) - Returns the value of x rounded up to its nearest integer.
- copySign(x, y) - Returns the first floating point x with the sign of the second floating point y.
- cos(x) - Returns the cosine of x (x is in radians).
- cosh(x) - Returns the hyperbolic cosine of a double value.
- exp(x) - Returns the value of Ex.
- expm1(x) - Returns ex -1.
- floor(x) - Returns the value of x rounded down to its nearest integer.
- getExponent(x) - Returns the unbiased exponent used in x.
- hypot(x, y) - Returns sqrt(x2 +y2) without intermediate overflow or underflow.
- IEEEremainder(x, y) - Computes the remainder operation on x and y as prescribed by the IEEE 754 standard.
- log(x) - Returns the natural logarithm (base E) of x.
- log10(x) - Returns the base 10 logarithm of x.
- log1p(x) - Returns the natural logarithm (base E) of the sum of x and 1.
- max(x, y) - Returns the number with the highest value.
- min(x, y) - Returns the number with the lowest value.
- nextAfter(x, y) - Returns the floating point number adjacent to x in the direction of y.
- nextUp(x) - Returns the floating point value adjacent to x in the direction of positive infinity.
- pow(x, y) - Returns the value of x to the power of y.
- random() - Returns a random number between 0 and 1.
- round(x) - Returns the value of x rounded to its nearest integer.
- rint(x) - Returns the double value that is closest to x and equal to a mathematical integer.
- signum(x) - Returns the sign of x.
- sin(x) - Returns the sine of x (x is in radians).
- sinh(x) - Returns the hyperbolic sine of a double value.
- sqrt(x) - Returns the square root of x.
- tan(x) - Returns the tangent of an angle.
- tanh(x) - Returns the hyperbolic tangent of a double value.
- toDegrees(x) - Converts an angle measured in radians to an approx. equivalent angle measured in degrees.
- toRadians(x) - Converts an angle measured in degrees to an approx. angle measured in radians.
- ulp(x) - Returns the size of the unit of least precision (ulp) of x.

## Modificadores
Modificadores de acceso:
- public: The code is accessible for all classes	
- private: The code is only accessible within the declared class	
- default: The code is only accessible in the same package. This is used when you don't specify a modifier.
- protected: The code is accessible in the same package and subclasses. You will learn more about subclasses and superclasses in the Inheritance chapter

Modificadores no de acceso:
- final: Attributes and methods cannot be overridden/modified
- static: Attributes and methods belongs to the class, rather than an object
- abstract: Can only be used in an abstract class, and can only be used on methods. 

The method does not have a body, for example abstract void run();. 
The body is provided by the subclass (inherited from). 

- transient: Attributes and methods are skipped when serializing the object containing them
- synchronized: Methods can only be accessed by one thread at a time
- volatile: The value of an attribute is not cached thread-locally, and is always read from the "main memory"

## Encapsulacion
- El concepto de encapsulación hace que la data sensible se oculta del usuario, para esto se debe considerar lo siguiente:
	- Las variables o atributos declarados deben ser de acceso privado.
	- Se debe brindar métodos get() y set() para acceder y modificar los valores de una variable privada.

## Herencia
- Es posible heredar atributos y métodos de una clase hacia otra, se agrupa en 2 categorías:
	- Hijo:	Es una clase que hereda de otra.
	- Padre: La clase la cual heredará.
	- Para indicar herencia, se utiliza la palabra reservada extends.

## Polimorfismo
- Polimorfismo significa muchas formas y ocurre cuando tenemos muchas clases que se relacionan entre sí por herencia.
	- La herencia nos permite heredar métodos y atributos, en el polimorfismo se usan métodos para realizar diferentes tareas. Permite realizar una sola acción de diferentes formas.

## Abstraccion
- La abstracción es el proceso por el cual se esconden ciertos detalles y se muestra solo la información esencial al usuario.
	- La abstracción se puede dar entre clases abstractas o interfaces abstractas
	- Recordar que la palabra reservada abstract es un no-modificador de acceso.
	- Una clase abstracta es una clase restringida que no puede ser usada para crear objetos. (Para acceder a ellos, se debe heredar desde otra clase.)
	- Una clase abstracta puede tener ambos tipos de método, abstracto y regulares.
	- Un método abstracto sólo puede ser usado en una clase abstracta y no tiene cuerpo. El cuerpo se desarrolla por una subclase (herencia).

## Interfaces
- Una forma de lograr la abstracción es con interfaces.
	- Una interfaz es una completa clase abstracta que se usa para definir métodos sin cuerpo.
	- Para acceder a los métodos de una interfaz estaba debe tener una implementación (Como herencia) por otra clase, usando la palabra reservada implements (en vez de extends). El cuerpo del método lo provee la clase que implementa la interfaz.
	- Se pueden implementar muchas interfaces en una clase separándolos con ",".

## Enum
- Los Enum son una clase especial que representan un grupo de constantes (variables que no pueden ser cambiadas, como variables finales).
	- Para crear un Enum se usa la palabra reservada Enum(sin class ni interface) y separan las constantes con una coma. Deben estar en mayúsculas.

## Array
- Los arreglos se usan para guardar múltiples valores en una sola variable, para declarar un array se utilizan los corchetes `[]`.
	- Para acceder al valor de un arreglo se hace mediante el índice, el cual inicia en 0.
## Set
- Es una lista de elementos los cuales son únicos entre sí.

## ArrayList
- Es un arreglo pero redimensionable.
	- La diferencia entre un Array y un ArrayList es que el tamaño del Array una vez definido no puede ser cambiado.

## LinkedList
- Es una colección que puede contener múltiples objetos del mismo tipo, como los ArrayList.
	- La clase LinkedList tiene los mismos métodos que ArrayList porque ambos implementan la interfaz List.
	- Sin embargo si bien pueden usarse de la misma forma, tienen ciertas diferencias:
		- Cómo funciona un ArrayList:
			- Un ArrayList tiene por dentro un Array, cuando un elemento se añade, se agrega al Array. Si el Array no es muy grande, un nuevo Array es creado reemplazando al anterior el cual es removido.
		- Cómo funciona un LinkedList:
			- LinkedList almacena los items en contenedores, la lista tiene un enlace al primer contenedor y cada contenedor tiene un enlace hacia el contenedor previo, para agregar un elemento a la lista, el elemento es depositado en un contenedor el cual es enlazado a otro contenedor en la lista.
	- La recomendación es usar ArrayList para almacenar y acceder a la información y usar LinkedList para manipular la información.

## HashMap
- En un HashMap, los valores se almacenan en pares de Key/Value y puedes acceder a ellos en base al índice de otro tipo, ejemplo String.
	- Puedes almacenar claves y valores diferentes, por ejemplo llaves de String con valores de Integer, o llaves String y valores String, etc.
	- Metodos:
		.put() : añade un nuevo item a la lista.
		.get(key) : busca un elemento en base a su llave:
		.remove(key): elimina un elemento en base a su llave:
		.clear() : limpia todos los items de la lista.
		.size() : tamaño de la lista.
		.keySet() : obtiene solo la lista de llaves.

## HashSet
- Es una colección de objetos donde cada item es único
	- Se usa el método .contains(Value) para verificar si un item existe.

## Iterator
- Es un objeto que se usa para recorrer colecciones.
	- Para recorrer un Iterator se usa el método .hasNext() y next()

## Java I/O
- Es un concepto usado para procesar inputs y output se encuentra en el paquete java.io
	- Se puede administrar archivos con el API I/O de java.
	- Se tienen 3 streams básicos creados por java para el manejo:
		- System.out: estándar para streams de salida.
		- System.in: estándar para streams de entrada.
		- System.err: estándar para streams de error.
	- InputStream:
		- Las aplicaciones usan el InputStream para leer datos de una fuente, puede ser un archivo, un arreglo, dispositivos periféricos o sockets.
	- OutputStream:
		- Las aplicaciones usan el OutputStream para escribir datos a un destino, puede ser un archivo, un arreglo, dispositivos periféricos o sockets.

---- 

Clases Wrapper:
- Son clases que proveen métodos para trabajar con tipos de datos primitivos.

	```
	Primitive Data Type		Wrapper Class
		byte						Byte
		short						Short
		int							Integer
		long						Long
		float						Float
		double						Double
		boolean						Boolean
		char						Character
	```

---- 

Clase Throwable:
- Es la clase padre de todas las excepciones en Java. Solo los objetos que son instanciados por esta clase o sus hijos, son lanzadas por la JVM o pueden ser lanzadas  por la declaración throw.
	- De forma similar, solo esta clase o sus hijas pueden ser argumentos en la cláusula catch()
	- Throwable o cualquiera de sus hijos que no sea una subclase de RunTimeException o Error se consideran excepciones comprobadas.
	- La instancia de 2 subclases que son Error y Exception son las que se usan de forma convencional cuando una situación de excepción ocurre. Típicamente estas instancias se crean en el contexto de una excepción y contiene información de la misma.
	- Una de las razones por las cuales la clase Throwable tiene una causa es que se construye a bajo nivel de abstracción con lo que la operación a alto nivel falla durante la ejecución.
	- Métodos mas usados:
		.getCause(): retorna la causa del error o nulo en caso de desconocer el motivo.
		.getMessage(): retorna el mensaje detallado del error.
		.getLocalizedMessage(): Crea una descripción focalizada del error.

Clase Exception:
- Es un hijo de Throwable.
	- Se refiere a un evento ocurrido durante la ejecución del programa que interrumpe el flujo normal de las instrucciones.
	- Existen excepciones en tiempo de ejecución y en tiempo de compilación.
	- Hay 2 tipos de excepciones, verificadas y no verificadas.
	- Una excepción se puede recuperar en un bloque try / catch.
	- Excepciones más conocidas:
		- RunTimeException: Son para errores en tiempo de ejecución de la JVM, son excepciones no verificadas.
			- Excepciones conocidas:
				- BufferOverflowException: La capacidad del buffer se ha sobrecargado.
				- ClassCastException: Se está intentando castear a una clase de la cual no es una instancia.
				- DateTime Exception: Problemas en la creación, cálculo y manipulación de fechas y horas.
				- IllegalArgumentException: Se indica que a un método le ha llegado un argumento que no está permitido.
				- IndexOutOfBoundsException: El índice al arreglo que se refiere esta fuera del rango.
				- NoSuchElementException: Indica que el elemento al cual quiere acceder no existe.
				- NullPointerException: Cuando la aplicación intenta usar un objeto nulo cuando se requiere, que incluye:
					- Llamar el método de una instancia de un objeto nulo.
					- Acceder o modificar un campo de un objeto nulo.
					- Calcular el tamaño de un nulo como si fuera un arreglo.
					- Acceder a los campos de un arreglo que estén nulos.
				- UnsupportedOperationException: Indica que la operación requerida no se encuentra soportada.
				- ArrayIndexOutOfBoundsException: Indica que un arreglo ha sido accedido con un índice incorrecto, puede ser negativo o mayor al tamaño del arreglo.
		- IOException: Son para errores ocurridos en la lectura o escritura de datos.


Clase Error:
- Es un hijo de Throwable.
	- Los errores por lo general están relacionados a los recursos del sistema.
	- No puede ser atrapado o manejado.
	- Indica problemas serios.
	- Ocurren en tiempo de ejecución.
	- Son errores no verificados.

---- 

HashCode: Es el valor de 32 bits que identifica la instancia de una clase.
final: Permite que la clase no pueda ser heredada de ninguna otra.

Collectors:
- Es una clase de utilidad y final que provee métodos y algoritmos para reducción, acumulación y añadir elementos a una colección.
	- Se tienen diferentes Collector's que hacen más sencilla la recopilación de datos.
	- Collector es una interfaz que su implementación es retornar los métodos implementados en la clase Collectors.

Lambdas:
- Las funciones lambdas fueron agregadas en JAVA 8.
	- Antes de las lambdas es hacia por hilos, implementando la Interfaz Runnable o extendiendo de la clase Thread
	- Una función tiene 4 propiedades:
		- Nombre de la función.
		- Lista de parametros.
		- Cuerpo de la función.
		- Tipo de retorno.
	- Si la función lambda solo tiene 1 línea de código, no necesita los corchetes.
	- Solo se pueden convertir a lambda las funciones que tengan solo 1 método abstracto
	- Por debajo, por cada implementación se está creando un archivo .class pero con lambda esto no ocurre, se invoca de forma Dinámica es decir en tiempo de ejecución y no compilación.
	- De igual forma inferencia de tipos, es decir el compilador detecta el tipo estático sin especificarlo de forma explícita, así como también el tipo de retorno y el tipo de los métodos.

	Interfaz Funcional:
	- Una interfaz funcional solo tiene 1 método abstracto.
		- La interfaz funcional se declara con la anotación @FuncionalInterfaz
		- Se puede utilizar para brindar implementaciones en el camino.		

	Programación Funcional:
	- La programación funcional está dentro de la programación declarativa.
		- Existen otras interfaces funcionales que se encuentran dentro del paquete java.util, las más usadas son: Predicate, Consumer, Function, Supplier
			- Predicate: Ingresa un tipo T y retorna un boolean.
			- Consumer: Ingresa un tipo T y no retorna nada.
			- Function: Ingresa un tipo T y sale un tipo R.
			- Supplier: No ingresa nada y retorna un tipo T.
			- UnaryOperator: Ingresa un tipo T y retorna un tipo T. (Extensión de Function).
			- BinaryOperator: Ingresan 2 tipos iguales T y retorna un tipo T.
			- BiPredicate: Ingresan 2 tipos L y R y retorna un booleano.
			- BiConsumer: Ingresan 2 tipos T y U y no retorna nada.
			- BiFunction: Ingresan 2 tipos T y U y retorna un tipo R.

	Referencia de Métodos:
	- Existen 4 tipos de referencias de métodos:
		- object::instanceMethod	: instancia un método de un objeto. System.out::println
			- Class::staticMethod
			- Class::instanceMethod		: instancia un método de una clase. Math::random
			- Class::new

Optional: java.util.Optional\<T\>
- Soluciona los problemas de nullPointerException.
	- Cuando un valor es nulo genera una excepción si se intenta operar con él y detiene el programa.
	- La clase Optional tiene métodos para poder trabajar con el valor de “null”.
	- Los objetos creados de Optional son inmutables una vez creados.
	- Métodos para obtener el valor de un Optional:
		- Optional.get() -\> Si no estás seguro de que si o si el valor estará presente, no uses este método. -\> NoSuchElementException.
		- Optional.isPresent() -\> Sí el valor está presente entonces retorna un valor, sino hace otra cosa.
		- Optional.orElse() -\> Da un valor por defecto en caso el valor no esté presente.
		- Optional.orElseThrow() -\> Si no encuentra el error retorna una excepción controlada.
	- Operaciones con Optional:
		- Optional.map() -\> Cambia el valor que viene del optional por otro, retorna el tipo de dato.
		- Optional.filter() -\> Sí el valor está presente y coincide con el predicado (condición) retorna un Optional con el valor, sino retorna un Optional empty.
		- Optional.flatMap() -\> Cambia el valor que viene del optional por otro, retorna el tipo de dato contenido en el Optional, retorna Optional.
		- Optional.ifPresent() -\> Ejecuta un Consumer si el valor está presente, en caso contrario no ocurre nada.
		- Optional.ifPresentOrElse() -\> Ejecuta un consumer si el valor está presente, caso contrario ejecuta una segunda acción.
		- Optional.stream() -\> retorna el valor del Optional como un stream para ser trabajado como tal.
		- Optional.or() -\> Retorna el valor del opcional de existir, sino retorna un nuevo valor.
		- Optional.equals() -\> Compara el contenido de 2 optional, si ambos son empty o si ambos comparten el mismo valor por el método equals.
		- Optional.hashCode() -\> Devuelve el hashcode del valor del optional, si no existe devuelve 0.

Programación funcional a profundidad:
- La programación funcional es otro paradigma de programación donde todo se hace en forma de funciones matemáticas puras.
	- Se realizan los cálculos en base a proveer algoritmos y datos.
	- Usa los datos proveídos y realiza los cálculos, no tiene nada que ver con los datos de los objetos.
	- Qué resolver en vez de como resolverlo.
	- El paradigma se basa en cálculos de expresiones lambda.
	- Conceptos bases.
		- Las funciones como ciudadanos de primera clase.
			- En java tradicional, se tratan a los objetos como primera clase.
			- POO: int result = myFunction(int a);
			- Functional: Function aFun = myFunction(Function b);
		- Funciones puras.
			- La salida de una función pura depende solo de:
				a) Sus parámetros de entrada.
				b) Su algoritmo interno.
			- y = f(x)
			- No tiene efectos secundarios: No hace nada más que su propio algoritmo.
			- Las funciones puras nunca cambian el estado de las variables
		- Funciones de alto orden.
			- Son funciones que pueden tener más de una función como parámetro y retorna otra función, o retornar funciones nada más.
		- Referencia transparente:
			- Transparencia referente es una propiedad de una función, variable o expresión donde la expresión puede ser reemplazada por su valor evaluado sin afectar el comportamiento de un programa.
			- La transparencia se refiere a que los cambios no deben afectar el efecto.
	- Técnicas: 
		- Encadenamiento funcional: Es una técnica que permite llamar a una función detrás de otra.
			- Ejemplo: obj.function1().function2().function3()
		- Composición funcional: Es la inversa del encadenamiento, se ejecuta primero la última hacia la primera.
			- Ejemplo: a.compose(b), primero se ejecuta b y luego a.
		- Cierres:
		- Currificacion: Transformar una función que utiliza múltiples argumentos en una secuencia de funciones que usan un único argumento.
		- Evaluación perezosa: 
		- Optimización de llamadas de cola

Patrones de Diseño:
- Los patrones de diseño son guías para el comportamiento de objetos.
	Iterator: java.util.Iterator java.util.Enumeration
	- Trata sobre el acceso a los elementos de un contenedor sin exponerlos.
		- Permite tener un camino de acceso a los elementos de una colección de objetos en forma secuencial sin necesidad de saber su representación interna.
	Strategy: 
	- Se usa cuando se tiene múltiples soluciones o algoritmos para resolver una tarea específica y el cliente decide cuál será la implementación específica que va a ser utilizada en tiempo de ejecución.
	Decorator:
	- Se usa para modificar la funcionalidad de un objeto en tiempo de ejecución sin afectar otras instancias de la misma clase.
	Factory:
	- Se enfoca en cómo se crea un objeto sin exponer la lógica de creación.
	Builder:
	- Provee flexibilidad en la creación de objetos.

Streams:
- Se introdujo en JAVA 8
	- Se puede manejar los datos de forma declarativa y funcional.
	- Stream no es una colección ni contenedor.
	- Los streams obtienen datos de una fuente, hace el proceso y luego retorna los datos a un contenedor que quiera el usuario o solo consume los datos.
	- El código es más limpio y legible.
	- También se pueden procesar en paralelo.
	- Un Stream pipeline se refiere a todos los métodos ejecutados uno tras otro en un Stream.
		- Tiene una fuente de datos.
		- Tiene cero o más métodos intermedios.
		- Tiene una operación final.
		- Un stream tiene apertura y cierre, con lo cual es inmutable, una vez cerrado ya no se puede utilizar.
	- Funciones más utilizadas:
		- Filter: Toma un predicado(obtiene algo y devuelve un boolean) para realizar un filtro.
		- Map: Toma una Función (A,B) obtiene algo y retorna otra cosa.	
		- Reduce: Reduce los elementos de un stream.
		- PeeK: permite actuar con los datos pero devuelve el mismo stream.
	- Las operaciones intermedias son perezosas, es decir solo se activan cuando se ejecutan.
	- NumericStreams: Permiten tener métodos matemáticos para el manejo de datos.
		- Map: retorna objects
		- MapToDouble: retorna double primitivos, ahorra la consulta.
		- MapToInteger: retorna integer primitivos, ahorra la consulta.
		- MapToLong: retorna long primitivos, ahorra la consulta.
		- Hay que tener en cuenta la diferencia entre el objeto Double, Integer y Long con los tipos de datos primitivos.
		- Métodos importantes:
			- sum() : suma todos los números en el stream.
			- max() : retorna el número máximo en el stream como un OptionalInt primitivo.
			- min() : retorna el número mínimo en el stream como un OptionalInt primitivo.
			- average() : retorna el promedio de los números en el stream como un OptionalInt primitivo.
			- summaryStatics() : Devuelve 5 datos: El conteo de valores, el mínimo, el máximo, el promedio y la suma.
	- Las colecciones de datos lineales se pueden transformar en streams, pero los map no porque son pares de valores.
	- Para hacer la conversión de un Map a stream se realiza de las siguientes formas:
		- Método .entrySet().stream() para obtener ambos datos de entrada.
		- Método .values().stream() para obtener los valores.
		- Método .keySet().stream() para obtener los valores de las llaves.
	- Stream infinitos:
		- Stream.iterate(a, a -\> a - b).limit(15) : de esta forma se crean streams con ciertas condiciones.
		- Stream.generate(() -\> "Hello") : Requiere un supplier y va a ejecutar ese supplier dentro del stream.
	- FLATMAP:
		- Consume una función y un mapper y retorna un stream. Se usa para combinar streams y obtener los datos del mismo.
	- Parallel Stream.
		- Es lo mismo que los Streams solo que se ejecutan en hilos paralelos y esto depende de la cantidad de núcleos del procesador y el procedimiento que queremos realizar.
		- Se puede configurar la cantidad de núcleos que queremos utilizar para el paralelismo.
		- ForkJoinPool se usa para configurar la cantidad de hilos que queremos utilizar.
		- Se recomienda que para cálculos intensivos el números de hilos sea menor que la cantidad de núcleos.
		- Se recomienda para Input y Outpot operations el número de hilos sea mayor que el número de núcleos, ya que la aplicación está inactiva la mayor parte del tiempo.
		- Por defecto, el JVM toma 1 núcleo del procesador para la clase Main.
	- Interfaz Spliterator:
		- Es un objeto especial en el que se construye para conectar a una fuente de datos personalizada, que no sean colecciones.
		- Podemos conectar un stream a una fuente de datos.
		- Tiene 4 métodos abstractos y varios por defecto.
			- boolean tryAdvance(Consumer\<? super T\> action);
			- Spliterator\<T\> trySplit();
			- long estimateSize();
			- int characteristics();
				- ORDERED: Significa que está ordenado.
				- DISTINCT: No hay valores duplicados.
				- SORTED: Indica sí está creado a partir de un filtro.
				- SIZED: El tamaño del stream.
				- NONNULL: No hay valores nules.
				- INMUTABLE: Que no se puede modificar.
				- CONCURRENT: Significa que el string tiene datos concurrentes.

POO:
Paradigma de programación, es decir guías de cómo programar.
Antes era procedural: Se forma secuencial.

Un objeto es un conjunto de métodos y atributos que definen su comportamiento.
La clase es la definición del objeto, como una plantilla de la cual a partir de ella se puede crear instancias de objetos de esa clase.

API (Application Programming Interface): 
- Es una pieza de software la cual permite intercambiar información entre 2 aplicaciones, simplifica la arquitectura, hace más rápido compartir y procesar  de flujos de datos.
	- Estilos de APIs más comunes:
		- REST (Representation State Transfer):
			- Es un estilo de arquitectura, la cual combina la arquitectura cliente servidor con restricciones adicionales las cuales definen una interfaz uniforme. Los desarrolladores pueden implementarlas de muchas formas.
			- Cuándo un cliente hace una petición mediante una API RESTful, ésta transfiere una representación del estado del recurso a un endpoint. Esta información se entrega en muchos formatos HTTP, por ejemplo JSON, PHP, XLT como otros.
			- REST es un conjunto de reglas versátiles que se pueden implementar en base a su necesidad, haciendo de las APIs REST rápidas y adaptables mas que otro tipo de APIs. 
			- Debido a sus bajos requerimientos de seguridad, compatibilidad con navegadores, acceso a data correcta y más, este estilo es de los más comunes en internet, incluso considerado más directo que SOAP
		- SOAP (Simple Object Access Protocol)
			- Es un protocolo de comunicación de sistemas que se conectan usando HTTP con XML, por lo general se usan para almacenar usuarios y contraseñas.
			- La ventaja de SOAP es que el manejo de errores es más detallado y manejable.

## HTTP
Principales códigos de respuesta:
- Respuestas informativas (100–199).
- Respuestas satisfactorias (200–299).
- Redirecciones (300–399).
- Errores de los clientes (400–499).
- Errores de los servidores (500–599).

Métodos:
- GET: El recurso se ha obtenido y se transmite en el cuerpo del mensaje.
- HEAD: Los encabezados de entidad están en el cuerpo del mensaje.
- PUT o POST: El recurso que describe el resultado de la acción se transmite en el cuerpo del mensaje.
- TRACE: El cuerpo del mensaje contiene el mensaje de solicitud recibido por el servidor.


## PRINCIPIOS DE LA PROGRAMACIÓN:

### SOLID
#### Single Responsability:
- Cada clase tiene una sola responsabilidad, es decir de una sola parte del sistema, una sola cosa, por ejemplo si tenemos una clase que crea usuarios pero dentro de la creación estamos incluyendo el código para encriptar su clave, estaríamos rompiendo el principio, la idea es que cada clase sea independiente.

#### Open Close:
- Una entidad de software debe estar abierta para creación pero cerrada para modificación, si deseas añadir una funcionalidad no debes modificar el código, debes hacerlo aparte, aquí se practica herencia y polimorfismo.

#### Liskov Substitution:
- Toda clase que es hija de una clase debe poder utilizarse como si fuera el padre.

#### Interface Segretation:
- Es mejor tener clases pequeñas y especializadas que una sola complicada, usar interfaces especializadas.

#### Dependency Inversion
- Los módulos de alto nivel no pueden depender de bajo nivel y viceversa, usar capas abstractas como DAO, Service, por ejemplo podríamos cambiar la base de datos usando CRUDRepository desde mysql a mongodb sin afectar el código.

#### Resumen:
- Código mantenible, legible y fácil de entender y cambiar.

#### KISS | KEEP IT SIMPLE, STUPID:
- Mantener la cosas simples
- La implementación debe ser sencilla
- Evitar soluciones muy complejas.

#### DRY | DON'T REPEAT YOURSELF:
- No repetir código, es similar al principio de responsabilidad única
- Código legible, reusable, testable, mantenible, desarrollo más rápido.

#### YAGNI | YOU AREN'T GONNA NEED IT :
- Evitar tener código que no sea necesario.
- Si no lo necesitas simplemente no lo implementes.
- Evitar código inflado.

## PATRONES DE DISEÑO:
- Un patrón de diseño es una receta, un plan de acción, una descripción de un problema y cómo solucionarlo, define una solución a un problema recurrente.

### Patrones creacionales:
- Solucionar problemas para creación de objetos.
	1.- FACTORY:
	- El método responsable de la creación de objetos de forma polimórfica, se utilizan las interfaces por lo cual no se genera dependencia entre las mismas.
	2.- ABSTRACT FACTORY:
	- Es la reducción de muchas factorías individuales, se tendría una factoría abstracta que implementa las demás factorías.
	3.- SINGLETON:
	- Asegurar de que existe solo una instancia de una clase concreta y solo una, como base el constructor es privado y se declara  una función estática privada para poder validar si esta instancia ya existe, en caso de existir devuelve la misma instancia en caso de no la crea. Parece una variable GLOBAL, se complica el test unitario.
### Patrones estructurales:
- Ayuda a configurar relaciones entre objetos.
	1.- DECORATOR:
	- Permite extender funcionalidades de una clase sin necesidad de recurrir de herencia. Composición VS Herencia.
		- Se crea una clase general y luego decoradores para que puedan servir a otras clases.
		- Los decoradores son componentes y también tiene un componente dentro.
		- Se debe tener bien mapeado el orden de los decoradores.
### Patrones de comportamiento:
- Ayuda con la interacción entre clases u objetos
	1.- STRATEGY:
	- Permite ejecutar diferentes lógicas de forma indiferente, depende de las abstracciones. Por ejemplo, crear métodos generales en interfaces para poder usar un mismo de forma independiente.
	2.- OBSERVER:
	- Se necesita notificar cambios de estado a un objeto, es decir hay un objeto observable y un observador.

## PATRONES DE ARQUITECTURA:

### MONOLITOS:
- Complejos de escalar y modificar.
- Escalamiento Horizontal

### SOA:
- Orientada a servicios.
- Como monolitos independientes.
- Todo debe coordinarse perfectamente y no hay mucha libertad para el desarrollo.
- Cómo integra todo en uno solo, existe aún el problema de la escalabilidad.
- Escalamiento vertical

### MICROSERVICIOS:
- Desarrollo de forma independiente tanto en tecnología como equipos de desarrollo.
- Menos tiempo en desplegar una solución.
- Ya no se limita a una sola tecnología.
- Cada servicio ejecuta su propio proceso.
- Centrados en el negocio.
- DEVOPS Incluido.
- Resiliencia (tolerancia a fallos)
- Correcta gestión de transaccionalidad.

	PATRONES:
	1.- DESCROMPOSICION:
	- Descomposición por capacidad del negocio:
		- Más va apuntado a la necesidad del negocio en sí, independientemente de la tecnología que se pueda implementar.
		- Patron por subdominios (DDD):
			\- 
		- Patron Strangle
			- Cuando se hacen migraciones de on premises a cloud permite ajustar las funcionalidades a microservicios.
	2.- INFRAESTRUCTURA:
	- Configuración centralizada:
		- Un lugar donde están centralizadas todas las configuraciones, CONFIG SERVER, donde estén los archivos yaml.
		- Service discover:
			- Es el patrón donde se da la responsabilidad en un lugar único todos los microservicios registrados y se notifica cuando el microservicio está o no disponible. EUREKA Server
		- Balanceo de carga:
			- Define a qué instancia determinada se debe realizar una petición en base a la estrategia planeada.
		- Reintento / Circuit Breaker:
			- Sé garantiza la disponibilidad del servicio, se reinventa en ciertos reintentos y el circuit breaker luego de un cierto número de reintentos, puede terminar la petición o esperar la disponibilidad del servicio.
		- Green Blue:
			- Aumenta la disponibilidad de la infraestructura al tener en diferentes regiones disponibles los servicios.
	3.- INTEGRACION:
	- API GATEWAY:
		- Un punto único de acceso a la infraestructura de microservicios, expuestos por APIs, funciones de login, request o response manipulables.
		- PUBLICADOR SUSCRIPTOR:
			- Las aplicaciones están suscritas a eventos
		- COREOGRAFÍA Y ORQUESTACIÓN:
			- Son las responsabilidades que se le asignan a los microservicios, acceso a datos, procesamiento de información, publicación de información, etc.
		- SAGA:
			- Implementar soluciones para evitar problemas de transaccionalidad.
	4.- ACCESO A DATOS:
	- INDEX TABLE:
		- Índice de acceso a datos.
		- SHARD:
			- Segmentamiento de la información
		- UNA BASE DE DATO POR SERVICIO.
			- Deben ser independientes y escalables, depender en lo menos posible de datos de otros microservicios.
		- CQRS:
			- Separar lectura y escritura de datos.
	5.- OBSERVABILIDAD:
	- LOGS:
		- Centralizar los logs, por ejemplo ELK.
		- MONITOREO PUNTO FINAL:
			- Válida si los microservicios si están disponibles o no.
		- MÉTRICAS DE RENDIMIENTO:
			- KPI de negocio, para ciertos objetivos de negocio.
		- TRACING DISTRIBUIDO:
			- Darle seguimiento al request del microservicio.
	6.- INTEGRACIÓN CON SERVICIOS EXTERNOS:
	- UN BACKEND POR FRONTEND:
		- No se debe un solo backend para 2 front como móvil o web.
		- CAPA ANTICORRUPCION:
			- Cómo se debe integrar con servicios externos desde cero, que los contratos no rompan nuestros servicios. un microservicio intermedio entre servicios externos y nuestros.


### HERRAMIENTAS DE MICROSERVICIOS:
1.- Cache distribuida (REDIS | HAZELCAST):
- Es una memoria en caché compartida por varios servidores de aplicaciones, que se mantiene como un servicio externo a estos servidores.
	- Mejora el rendimiento
	- Permite aumentar el throughput (Cantidad de procesamiento de datos).
	- Reducción de costo en cloud.
	- Desempeño predecible.
	- Control de sesiones.
	- KEY + VALUE
	- Tiempo de vida

2.- Mensajería de datos:
- KAFKA
- AWS SQS, AWS SNS

3.- Centralización de configuración:
- ZOOKEEPER

4.- Bases de datos:
- MYSQL / POSTGRESQL

5.- Almacenamiento distribuido:
- ELASTICSEARCH

6.- DOCKER / KUBERNETES

## PREGUNTAS Y RESPUESTAS DE SPRING:

- DIFERENCIA ENTRE SPRING BOOT Y SPRING
	- Spring boot es un proyecto spring pero con auto configuración, servidor embebido y ya no necesita los archivos XML de configuración.

- QUE ES UN BEAN
	- Es una pieza de software que representa un objeto en spring, tienen un ciclo de vida y son reutilizables.

- QUE ES UN ÁMBITO DE UN BEAN
	- Define el ciclo de vida del BEAN y se definen con @SCOPE
	- Los disponibles son: SINGLETON, PROTOTYPE, REQUEST, SESSION, APPLICATION, WEB SOCKET

- QUÉ SON LOS STARTERS EN SPRING BOOT:
	- Es una utilidad que facilita la creación de un proyecto y configuración de aplicaciones, se añaden todas las dependencias necesarias, por ejemplo DATA, JPA, KAFKA, ETC.

- PRINCIPALES VERBOS HTTP EN SPRING:
	- Parte de SPRING MVC:
	- @GetMapping @PostMapping @PutMapping @DeleteMapping @PatchMapping

- DIFERENCIA ENTRE HIBERNATE Y JPA:
	- JPA es el Java Persistence API con interfaces ya definidas para la persistencia de datos (CRUD)
	- Hibernate es una implementación particular de JPA (Spring usa por defecto)

- SPRING INITIALIZR
	- Plataforma online para la creación de proyectos en spring boot, descarga un `.rar` que luego se importa al IDE de preferencia IntelliJ, STS o Eclipse.

- ESTEREOTIPOS:
	- Son 4, @Service @Repository @Controller y @Component
	- @Component permite que Spring reconozca este componente como un bean de spring mismo.
	- @Repository ayuda a implementar el repositorio para el acceso a datos.
	- @Service: gestiona las operaciones de negocio
	- @Controller: Gestión de comunicación entre usuario y aplicación.

- @RESTCONTROLLER:
	- Es un controlador pero específico para API REST usando SPRING MVC, combina el @controller con @responsebody

- SPRING AOP:
	- AOP: Programación orientada a aspectos
	- Permite crear aspectos en la aplicación para ser usados de forma transversal.

- @PROFILE:
	- Usa beans en particular para definir el perfil activo en spring, dev, qa, prod

- @SpringBootConfiguration
	- Se ubica en la clase principal de un proyecto Spring
	- Combina las anotaciones de @Configuration, @EnableAutoConfiguration y @ComponentScan

- QUÉ PATRONES ESTÁN PRESENTES EN SPRING / SPRING BOOT
	- Creacional: SINGLETON
	- Estructural: Proxy
	- Comportamiento: Cache, template

- @TRANSACTIONAL
	- Permite ejecutar métodos select o insert pero al punto que si algo sale mal, el estado del mismo queda  en su estado inicial.

- INYECCIÓN DE DEPENDENCIAS
	- Separa responsabilidades haciendo que el código sea desacoplado, en Spring cuando inicia se cargan los beans y luego son inyectados con la anotación @Autowired.

- FORMAS DE INYECCIÓN DE DEPENDENCIAS:
	- Inyección por atributo
	- Inyección por setter
	- Inyección por constructor.

- @VALUE
	- Permite leer configuraciones y colocarla en las propiedades anotadas.

- PUERTO POR DEFECTO SPRING:
	- 8080

- SPRING ACTUATOR:
	- Librería para herramientas de monitoreo de un API REST
	- Habilita endpoint para ser usado:	
		/env -- muestra las variables de entorno de la app
		/info -- provee información sobre la app spring ejecutándose
		/loggers -- provee acceso a los logs de la aplicación
		/health -- muestra la salud de la app
		/beans -- muestra los Beans disponibles.
		/heapdump -- Gets a heapdump of the JVM

- SPRING CLOUD:
	- Implementación de spring boot para soluciones de microservicios, Config y Api Gateway

## SPRING BOOT:
1.- SPRING CACHE:
- @Cacheable: Guardar y obtener elementos
	- @CachePut: Actualizar
	- @CacheEvict: Eliminar
	- @EnableCaching: habilitar uso de cache.


### Implementación de un sistema simple de Control de Peajes.

Se pide realizar un sistema que procese las patentes que pasaron por las cabinas de un peaje de un paso fronterizo de algún país del  Mercosur.
Las patentes Mercosur pueden ser como las del siguiente modelo:

Observar que los patrones de las patentes son los siguientes:

* Argentina: LLNNNLL 
* Brasil:        LLLNLNN
* Bolivia:      LLNNNNN
* Paraguay:  LLLLNNN
* Uruguay:   LLLNNNN

Notar que L representa letras, mientras que N representa números o dígitos. Todas las patentes Mercosur tienen la misma longitud: 7 caracteres en total (los espacios en blanco que ocasionalmente pueden aparecer en la figura adjunta o en una placa real, se colocan solo a los efectos de facilitar la lectura por parte de los humanos, pero NO se almacenan (ni deben ser cargados) internamente al gestionar una de estas cadenas en una variable. 

Se espera que la placa se cargue como una cadena de caracteres sin validar la estructura básica de la misma (asumimos que quien carga los datos lo hace correctamente, con letras en mayúscula, sin espacios en blanco, y sin caracteres que no sean ni letras ni números. Pero para agregar algún elemento básico de control, asuma que SÍ puede ser ingresada una cadena que NO tenga 7 caracteres)

 **Modificación**: Cuando decimos que vamos a cargar correctamente una patente, queremos indicar que no vamos cargar nada que NO SEAN letras ni números. NO VAMOS a cargar algo como "&%$.9+-" ni nada por estilo, y pueden asumir que las letras se cargarán en mayúscula. PERO SÍ cargaremos patentes con menos de 7 letras, o con más de 7 letras, o con 7 letras pero que no correspondan a ningún país de los 5 válidos. Y si una patente no corresponde al Mercosur, el programa tiene que informarla como "Otro" y CONTINUAR EL PROCESO DE EMISIÓN DEL TICKET EN FORMA NORMAL. TODAS LAS PATENTES SON VÁLIDAS, en el sentido de que para todas hay que emitir el ticket. Y esto es logico: cualquier auto que llegue a una cabina tiene que pagar, sea de donde sea su placa y tenga el formato que tenga. Si cargo una patente de 5 caracteres y el programa corta sin hacer nada, ESTÁ MAL, y sumarán cero puntos para ese lote. EN TODOS LOS CASOS, Y PARA TODA PATENTE CARGADA, HAY QUE EMITIR EL TICKET Y EN TODO CASO INFORMAR QUE EL PAÍS ES OTRO. NO CORTEN EL PROGRAMA si la patente tiene menos de 7 letras, o tiene más de 7 letras, o tiene 7 letras pero no corresponden a ningún país de los 5 válidos.
 
Considerar que solo es necesario aplicar contenidos desarrollados hasta la Ficha 05 para la resolución del presente Trabajo Práctico.

Solo a los efectos de este trabajo (y sin que esto sea necesariamente real), se asume que todos los países cobran un importe base por cada peaje equivalente a 300 pesos, salvo Brasil que asumiremos que cobra peajes en una base de 400 pesos, y Bolivia que cobra peajes en una base de 200 pesos. Para simplificar, asuma que en todos los países ese monto está expresado en pesos argentinos (y no se preocupe por este detalle).

El programa debe ingresar los datos de UN vehículo que se supone pasó por alguna cabina de peaje ubicada en cualquiera de los cinco países. Los datos a cargar para ese vehículo son:

* `La patente`: una cadena de caracteres). Recuerde que se asume que no necesariamente tendrá 7 caracteres, pero que no contendrá tampoco blancos ni letras minúsculas, ni caracteres diferentes de letras y números. Observe no obstante que incluso teniendo 7 caracteres podría no ser una placa válida para ninguno de los cinco países (y esto SÍ puede ocurrir en este trabajo). 


* `El tipo de vehiculo`: un número entero entre 0 y 2 que indica alguno de los siguientes tipos de vehículos: (0: motocicleta, 1: automóvil, 2: camión). Solo a los efectos de este trabajo, asuma que el formato de las placas patentes de cada país es el mismo tanto para motos, como para autos o para camiones.


* `La forma de pago`: un número entero que indica alguno de los dos siguientes tipos de pago: (1: manual, 2 telepeaje). 


* `Pais`: un número entero entre 0 y 4 para indicar el país donde está la cabina atravesada (asúmalos en el orden que prefiera) (MODIFICACIÓN: NO ASUMA LOS NÚMEROS DE PAÍS EN EL ORDEN QUE PREFIERA. La verificación y calificación de este trabajo se hará contra lotes de pruebas que asumen que los números de país son ESTRICTAMENTE los que siguen: 0: Argentina - 1: Bolivia - 2: Brasil - 3: Paraguay - 4: Uruguay).


* `Distancia`: Un número en coma flotante indicando la distancia en kilómetros que recorrió ese vehículo desde la última cabina de peaje que atravesó (asumimos que de alguna forma las cabinas se informan entre ellas esos datos). Aquí ingrese un cero para indicar que la cabina actual es la primera que ese vehículo atraviesa. 

Se solicita rigurosamente que al programar la carga de estos datos en el programa, sigan estrictamente el mismo orden en que están enumerados más arriba, y no agreguen NINGÚN otro dato más que los que se piden aquí: primero carguen la patente, luego el tipo de vehiculo, luego la forma de pago, luego el país, y finalmente la distancia, manteniendo los tipos de datos que se indicaron.  

Se pide desarrollar un programa que permita simular la emisión del ticket en base a los siguientes ítems:

* Indicar el país de procedencia del vehículo, considerando el formato de las placas de los países del Mercosur. Si la placa no cumpliera con ninguno de esos formatos, informar que el país es “Otro”.


* Indicar el importe básico a pagar por el vehículo, considerando que si el vehículo es una motocicleta se aplica un descuento del 50% sobre el importe base que cobra esa cabina, y si el vehículo es un camión se aplica un recargo del 60% sobre el importe base de la cabina. Solo los automóviles pagan el importe base.


* Considerando que si la forma de pago fue por telepeaje se aplica un descuento del 10% al importe calculado en el punto anterior, indique el valor final del ticket.


* Informe finalmente a cuánto equivale el valor promedio pagado por ese vehículo por cada kilómetro recorrido desde la última cabina (es decir: el monto cobrado en esa cabina, dividido por la cantidad de kilómetros. Recuerde que la cantidad de kilómetros puede ser cero, en cuyo caso no aplica el cálculo, y el programa debe informar eso con un mensaje). MODIFICACIÓN: Muestre el promedio redondeado a dos decimales (use para ello la función round() que el lenguaje ya provee).
# Introducción

El uso de una función de Python es el primer paso para codificar después de las estructuras de datos y los condicionales básicos. Las funciones permiten la reutilización, lo que evita la duplicación de código. Cuando los proyectos reutilizan código con funciones, se vuelven más legibles y fáciles de mantener.

## Escenario: Organización de datos sobre un cohete

Imagina que vas a crear un programa para construir información precisa sobre un cohete espacial. Las funciones reutilizables te permitirán no solo calcular información, sino también crear valores combinando entradas y salidas de otras funciones.

## ¿Qué descubrirás?
En este módulo, aprenderás a:

* Trabajar con entradas predeterminadas, obligatorias y de carácter comodín.
* Hacer que el código sea reutilizable extrayendo patrones comunes en funciones independientes.
* Devolver valores, estructuras de datos o resultados calculados.

## ¿Cuál es el objetivo principal?
Al final de este módulo, comprenderás algunas de las reglas y el comportamiento asociado a las funciones, incluida la forma de controlar las entradas y salidas.

---

## Aspectos básicos de las funciones de Python

Las funciones son el siguiente paso después de haber aprendido los conceptos básicos de programación de Python. En su forma más sencilla, una función contiene código que siempre devuelve un valor (o valores). En algunos casos, una función también tiene entradas opcionales u obligatorias.

Al empezar a escribir código que duplica otras partes del programa, se convierte en una oportunidad perfecta para extraer el código en una función. Aunque compartir código común mediante funciones es útil, también se puede limitar el tamaño del código extrayendo partes en funciones más pequeñas (y legibles).

Los programas que evitan la duplicación y evitan funciones de gran tamaño mediante funciones más pequeñas son más legibles y fáciles de mantener. También son más fáciles de depurar cuando las cosas no funcionan correctamente.

Hay varias reglas sobre las entradas de funciones que son fundamentales para aprovechar al máximo todo lo que las funciones tienen que ofrecer.

*Aunque se usa el término entrada para describir las funciones que se aceptan, estos elementos normalmente se denominan argumentos y/o parámetros. Para mantener la coherencia en este módulo, a las entradas las denominaremos argumentos.*

### Funciones sin argumentos
Para crear una función, utilizamos la palabra clave `def`, seguida de un nombre, paréntesis y, después, del cuerpo con el código de función:

```
# Defino mi función
def rocket_parts():
    print('payload, propellant, structure')
```

En este caso, rocket_parts es el nombre de la función. Ese nombre va seguido de paréntesis vacíos, que indican que no se necesitan argumentos. El último es el código, con sangría de cuatro espacios. Para trabajar con la función, debes llamarla por su nombre usando paréntesis:

```
# Llamo a mi función

>>> rocket_parts()
'payload, propellant, structure'
```

La función rocket_parts() no toma ningún argumento e imprime una instrucción sobre la gravedad. Si necesitas usar un valor que devuelve una función, puedes asignar la salida de la función a una variable:

```
>>> output = rocket_parts()
payload, propellant, structure

>>> output is None
True
```

Puede parecer sorprendente que el valor de la variable output sea None. Esto se debe a que la función rocket_parts() no ha devuelto explícitamente un valor. En Python, si una función no devuelve explícitamente un valor, devuelve implícitamente None. Actualizar la función para devolver la cadena en lugar de imprimirla hace que la variable output tenga un valor distinto:

```
>>> def rocket_parts():
...     return 'payload, propellant, structure'
...
>>> output = rocket_parts()
>>> output
'payload, propellant, structure'
```
Si necesitas usar el valor de una función, esa función debe devolver el valor explícitamente. De lo contrario; se devolverá `None`.

*No es necesario asignar siempre la devolución de una función. En la mayoría de los casos en los que una función no devuelve un valor (o valores) explícitamente, significa que no es necesario asignar ni usar el valor implícito `None` que se devuelve.*

### Argumentos opcionales y requeridos
En Python, varias funciones integradas requieren argumentos. Algunas funciones integradas hacen que los argumentos sean opcionales. Las funciones integradas están disponibles de inmediato, por lo que no es necesario importarlas explícitamente.

Un ejemplo de una función integrada que requiere un argumento es `any()`. Esta función toma un objeto iterable (por ejemplo, una lista) y devuelve `True` si algún elemento del objeto iterable es `True`. De lo contrario, devuelve `False`.

```
>>> any([True, False, False])
True
>>> any([False, False, False])
False
```

Si llamamos a `any()` sin ningún argumento, se genera una excepción útil. El mensaje de error explica que necesita al menos un argumento:

```
>>> any()
Traceback (most recent call last):
  File '<stdin>', line 1, in <module>
TypeError: any() takes exactly one argument (0 given)
```

Puedes comprobar que algunas funciones permiten el uso de argumentos opcionales mediante otra función integrada denominada `str()`. Esta función crea una cadena a partir de un argumento. Si no se pasa ningún argumento, devuelve una cadena vacía:

```
>>> str()
''
>>> str(15)
'15'
```

## Uso de argumentos en una función de Python

Ahora que sabes cómo crear una función sin entradas, el paso siguiente es crear funciones que requieran un argumento. El uso de argumentos hace que las funciones sean más flexibles, ya que pueden hacer más y condicionalizar lo que hacen.

### Exigencia de un argumento
Si vas a pilotar un cohete, una función sin entradas obligatorias es como un equipo con un botón que le indique la hora. Si presionas el botón, una voz computarizada le indicará la hora. Pero una entrada necesaria puede ser un destino para calcular la distancia del viaje. Las entradas obligatorias se denominan *argumentos* para la función.

Para requerir un argumento, agrégalo entre paréntesis:

```
def distance_from_earth(destination):
    if destination == 'Moon':
        return '238,855'
    else:
        return 'Unable to compute to that destination'
```
Intenta llamar a la función distance_from_earth() sin argumento alguno:

```
>>> distance_from_earth()
Traceback (most recent call last):
  File '<stdin>', line 1, in <module>
TypeError: distance_from_earth() missing 1 required positional argument: 'destination'
```

Python genera `TypeError` con un mensaje de error que indica que la función requiere un argumento denominado destination. Si se pide al equipo del cohete que calcule la distancia del viaje con un destino, debes solicitar que un destino es un requisito. El código de ejemplo tiene dos rutas de acceso para una respuesta, una para la Luna y la otra para cualquier otra cosa. Use la Luna como entrada para obtener una respuesta:

```
>>> distance_from_earth('Moon')
'238,855'
```

Dado que hay una condición catch-all, intenta usar cualquier otra cadena como destino para comprobar ese comportamiento:

```
>>> distance_from_earth('Saturn')
'Unable to compute to that destination'
```

### Varios argumentos necesarios
Para usar varios argumentos, debes separarlos con una coma. Vamos a crear una función que pueda calcular cuántos días se tardarán en llegar a un destino, dadas la distancia y una velocidad constante:

```
def days_to_complete(distance, speed):
    hours = distance/speed
    return hours/24
```

Ahora usa la distancia entre la Tierra y la Luna para calcular cuántos días tardaría en llegar a la Luna con un límite de velocidad común de 120 kilómetros por hora:

```
>>> days_to_complete(238855, 75)
132.69722222222222
```
### Funciones como argumentos
Puedes usar el valor de la función days_to_complete() y asignarlo a una variable y, después, pasarlo a round() (una función integrada que redondea al número entero más cercano) para obtener un número entero:

```
>>> total_days = days_to_complete(238855, 75)
>>> round(total_days)
133
```
Pero un patrón útil es pasar funciones a otras funciones en lugar de asignar el valor devuelto:

```
>>> round(days_to_complete(238855, 75))
133
```

**Sugerencia**

Aunque pasar funciones directamente a otras funciones como entrada es útil, existe la posibilidad de que se reduzca la legibilidad. Este patrón es especialmente problemático cuando las funciones requieren muchos argumentos.

## Uso de argumentos de palabra clave en Python

Los argumentos opcionales requieren un valor predeterminado asignado a ellos. Estos argumentos con nombre se denominan *argumentos de palabra clave*. Los valores del argumento de palabra clave deben definirse en las propias funciones. Cuando se llama a una función definida con argumentos de palabra clave, no es necesario usarlos en absoluto.

La misión Apolo 11 tardó unas 51 horas en llegar a la Luna. Vamos a crear una función que devuelva la hora estimada de llegada usando el mismo valor que la misión Apolo 11 como valor predeterminado:

```
from datetime import timedelta, datetime

def arrival_time(hours=51):
    now = datetime.now()
    arrival = now + timedelta(hours=hours)
    return arrival.strftime('Arrival: %A %H:%M')
```

La función usa el módulo `datetime` para definir la hora actual. Usa `timedelta` para permitir la operación de suma que da como resultado un objeto de hora nuevo. Después de calcular ese resultado, devuelve la estimación `arrival` con formato de cadena. Intentando llamarla sin algún argumento:

```
>>> arrival_time()
'Arrival: Saturday 16:42'
```

Aunque la función define un argumento de palabra clave, no permite pasar uno cuando se llama a una función. En este caso, la variable `hours` tiene como valor predeterminado `51`. Para comprobar que la fecha actual es correcta, usamos `0` como valor para `hours`:

```
>>> arrival_time(hours=0)
'Arrival: Thursday 13:42'
```

### Combinación de argumentos y argumentos de palabra clave

A veces, una función necesita una combinación de argumentos de palabra clave y argumentos. En Python, esta combinación sigue un orden específico. Los argumentos siempre se declaran primero, seguidos de argumentos de palabra clave.

Actualizando la función `arrival_time()` para que tome un argumento necesario, que es el nombre del destino:

```
from datetime import timedelta, datetime

def arrival_time(destination, hours=51):
    now = datetime.now()
    arrival = now + timedelta(hours=hours)
    return arrival.strftime(f'{destination} Arrival: %A %H:%M')
```

Dado que hemos agregado un argumento necesario, ya no es posible llamar a la función sin ningún argumento:


```
>>> arrival_time()
Traceback (most recent call last):
  File '<stdin>', line 1, in <module>
TypeError: arrival_time() missing 1 required positional argument: 'destination'
```
Usamos 'Moon' como valor para destination a fin de evitar el error:

```
>>> arrival_time('Moon')
'Moon Arrival: Saturday 16:54'
```
También podemos pasar más de dos valores, pero debemos separarlos con una coma. Se tarda aproximadamente 8 minutos (0,13 horas) en entrar en órbita, así que utilizaremos eso como argumento:

```
>>> arrival_time('Orbit', hours=0.13)
'Orbit Arrival: Thursday 14:11'
```

## Uso de argumentos de variable en Python

En Python, puedes usar cualquier número de argumentos de palabra clave y argumentos sin necesidad de declarar cada uno de ellos. Esta capacidad es útil cuando una función puede obtener un número desconocido de entradas.

### Argumentos de variable
Los argumentos en las funciones son necesarios. Pero cuando se usan argumentos de variable, la función permite pasar cualquier número de argumentos (incluido `0`). La sintaxis para usar argumentos de variable es agregar un asterisco único como prefijo (`*`) antes del nombre del argumento.

La función siguiente imprime los argumentos recibidos:

```
def variable_length(*args):
    print(args)
```
*No es necesario denominar a los argumentos de variable `args`. Puedes usar cualquier nombre de variable válido. Aunque es habitual ver *args o *a, debe intentar usar la misma convención en un proyecto.*

En este caso, `*args` indica a la función que acepta cualquier número de argumentos (incluido `0`). En la función, `args` ahora está disponible como la variable que contiene todos los argumentos como una tupla. Pruebe la función pasando cualquier número o tipo de argumentos:

```
>>> variable_length()
()
>>> variable_length('one', 'two')
('one', 'two')
>>> variable_length(None)
(None,)
```
Como puedes ver, no hay ninguna restricción en el número o tipo de argumentos que se pasan.

Un cohete realiza varios pasos antes de un lanzamiento. En función de las tareas o retrasos, estos pasos pueden tardar más de lo previsto. Vamos a crear una función de longitud variable que pueda calcular cuántos minutos quedan hasta el inicio, dado el tiempo que va a tardar cada paso:

```
def sequence_time(*args):
    total_minutes = sum(args)
    if total_minutes < 60:
        return f'Total time to launch is {total_minutes} minutes'
    else:
        return f'Total time to launch is {total_minutes/60} hours'
```
Probamos la función pasando cualquier número de minutos:

```
>>> sequence_time(4, 14, 18)
'Total time to launch is 36 minutes' 
>>> sequence_time(4, 14, 48)
'Total time to launch is 1.1 hours'
```
*Cuando se utilizan argumentos de variable, a cada valor ya no se le asigna un nombre de variable. Todos los valores ahora forman parte del nombre de variable catch-all que usa el asterisco (en estos ejemplos, args).*

### Argumentos de palabra clave variable
Para que una función acepte cualquier número de argumentos de palabra clave, debe usar una sintaxis similar. En este caso, se requiere un asterisco doble:

```
def variable_length(**kwargs):
    print(kwargs)
```

Prueba la función de ejemplo, que imprime los nombres y valores pasados como `kwargs`:
```
>>> variable_length(tanks=1, day='Wednesday', pilots=3)
{'tanks': 1, 'day': 'Wednesday', 'pilots': 3}
```

Si ya conoces bien los diccionarios de Python, observarás que los argumentos de palabra clave de longitud variable se asignan como un diccionario. Para interactuar con las variables y los valores, usamos las mismas operaciones que un diccionario.

*Al igual que con los argumentos de variable, no es necesario usar kwargs cuando se usan argumentos de palabra clave variable. Puede usar cualquier nombre de variable válido. Aunque es habitual ver **kwargs o **kw, debe intentar usar la misma convención en un proyecto.*

En esta función, vamos a usar argumentos de palabra clave variable para notificar los astronautas asignados a la misión. Dado que esta función permite cualquier número de argumentos de palabra clave, se puede reutilizar independientemente del número de astronautas asignados:

```
def crew_members(**kwargs):
    print(f'{len(kwargs)} astronauts assigned for this mission:')
    for title, name in kwargs.items():
        print(f'{title}: {name}')
```

Probando con la tripulación del Apolo 11:
```
>>> crew_members(captain='Neil Armstrong', pilot='Buzz Aldrin', command_pilot='Michael Collins')
3 astronauts assigned for this mission:
captain: Neil Armstrong
pilot: Buzz Aldrin
command_pilot: Michael Collins
```

Dado que puede pasar cualquier combinación de argumentos de palabra clave, nos aseguramos de evitar palabras clave repetidas. Las palabras clave repetidas producirán un error:

```
>>> crew_members(captain='Neil Armstrong', pilot='Buzz Aldrin', pilot='Michael Collins')
  File '<stdin>', line 1
SyntaxError: keyword argument repeated: pilot
```

---
## Resumen

Las funciones de Python permiten escribir código modular y reutilizable, calcular valores y realizar acciones basadas en el contexto. En este módulo, ha obtenido información sobre algunas de las reglas y el comportamiento asociados a las funciones. Estas reglas incluían enfrentarse a entradas y salidas. Por último, ha tenido la oportunidad de extraer y mejorar el código para que sea más legible y fácil de mantener.

Ahora conoces aspectos esenciales como estos sobre las funciones:

* Las funciones pueden requerir argumentos o convertirlos en opcionales.
* Puedes extraer código reutilizable y reutilizarlo en una función.
* Los argumentos de variable y los argumentos de palabra clave de variable son útiles cuando no se conocen las entradas exactas.
* Con estas técnicas y el conocimiento de las funciones, deberías sentirse más cómodo abordando problemas más grandes al escribir código de Python.

---

Curso Propedútico de Python para Launch X - Innovacción Virtual.

Material desarrollado con base en los contenidos de MSLearn y la metáfora de LaunchX, traducción e implementación por: Fernanda Ochoa - Learning Producer de LaunchX.

Redes:
* GitHub: [FernandaOchoa](https://github.com/FernandaOchoa)
* Twitter: [@imonsh](https://twitter.com/imonsh)
* Instagram: [fherz8a](https://www.instagram.com/fherz8a/)
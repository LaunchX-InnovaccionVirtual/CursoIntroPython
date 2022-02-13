# Introducción

Los programas informáticos son excelentes para trabajar con tareas repetitivas. Como desarrollador, a menudo tendrás que recorrer en ciclo secuencias de valores, como cadenas, números y objetos. Python proporciona dos mecanismos para realizar estas tareas: ciclos ````while```` y ``for``.

## Escenario: Trabajo con el control de flujo en una aplicación de planetario

Imagina que vas a crear una aplicación en la que los usuarios escribirán una lista de nombres de planetas. Después de que los usuarios escriban los nombres, volverás a mostrarles los resultados. Esto requerirá que se les pidas varias veces que escriban valores y, cuando terminen, el código imprimirá todos los datos de la lista. En este módulo, exploraremos cómo puedes usar los ciclos ````while```` y ``for`` para crear esta aplicación.

Al final del módulo, sabrás utilizar los ciclos ````while```` y ``for``.

## ¿Qué aprenderás?
Cuando hayas finalizado este módulo, podrás:

* Identificar cuándo se deben usar los ciclos ````while```` y ``for``.
* Ejecutar una tarea varias veces mediante ciclos ``while``.
* Recorrer en ciclo los datos de la lista mediante ciclos ``for``.

## ¿Cuál es el objetivo principal?
En este módulo, descubrirás cómo aplicar el control de flujo a tu aplicación para repetir instrucciones y trabajar con estructuras de lista.

---

## Acerca de los ciclos ``while``

Al escribir código, un desafío común es que realices una tarea un número desconocido de veces. En esta unidad, quieres permitir que un usuario escriba una lista de nombres de planetas. Desafortunadamente, no sabes cuántos nombres escribirá el usuario. Para admitir una entrada de usuario o ejecutar una tarea, un número desconocido de veces, puedes usar un ciclo ````while````.

Un ciclo ````while```` realiza una operación *mientras* (``while``, en inglés) *una determinada condición es True*. Funcionan para evaluar si hay otra línea en un archivo, si se ha establecido una marca, si un usuario ha terminado de escribir valores o bien ha cambiado algo más para indicar que el código puede dejar de realizar la operación.

> Lo más importante que se debe recordar al crear ciclos ````while```` es asegurarse de que cambia la condición. Si la condición siempre es True, Python seguirá ejecutando el código hasta que el programa se bloquee.

La sintaxis de un ciclo ``while`` es similar a la de una instrucción ``if``. Proporciona una condición, así como el código que quieres ejecutar mientras la condición sea ``True`` (Oséa, mientras la condición se cumpla o sea verdadera).

Un ciclo ``while`` tiene tres partes importantes:

* La palabra ``while``, seguida de un espacio.

* La condición que se va a probar. Si la condición es True, se ejecutará el código dentro del ciclo ``while``.

* El código que quiere ejecutar para cada elemento del objeto iterable, seguido de espacios en blanco anidados. Por ejemplo:

```
while condition:
    # lo que quieres que se ejecute
```
*Se lee de la siguiente manera: Mientras la condición se cumpla: ejecuta el código*

Veamos cómo puedes crear código para pedir a los usuarios que escriban valores y, después, permitirles usar ``done`` cuando terminen de escribir los valores. En nuestro ejemplo, usaremos la entrada de usuario como condición y, después, la probaremos al principio del ciclo ``while``.


```
user_input = ''

while user_input.lower() != 'done':
    user_input = input('Enter a new value, or done when done')
```

**Leamos el código línea por línea, el texto entre paréntesis hace referencia al fragmento del código que describimos.**

```
Definimos la variable user_input (Para guardar lo que el usuario va a escribir)

mientras(while) lo que el usuario escriba(user_input), convertido a minúsculas(.lower()) sea diferente de(!=) la palabra 'done' quiero que: 

    Guardes en la variable user_input(user_input =), lo que el usuario escriba (input), muestra un texto de ejemplo para el usuario('Enter a new value, or done when done').
    
```

Tengamos en cuenta que se usa input para preguntar a los usuarios. Cada vez que los usuarios escriben un nuevo valor, cambian la condición, lo que significa que el ciclo while se finalizará una vez que se haya escrito la palabra done, si escribes cualquier otra palabra el ciclo continuará.

Puedes usar la cadena recién escrita como lo haríamos con cualquier otra cadena capturada con input. Si quieres agregarla a una lista, puedes usar código similar al ejemplo siguiente:

```
# Creamos la variable que almacena el texto
user_input = ''
# Creamos la lista que almacena cada uno de los textos que el usuario ingresa
inputs = []

# Ciclo while
while user_input.lower() != 'done':
    # Verificamos si hay un valor en user_input
    if user_input:
        # Almacenamos ese valor en la lista
        inputs.append(user_input)
    # Capturamos un nuevo valor
    user_input = input('Enter a new value, or done when done')
```

Observa la instrucción ``if`` dentro del ciclo ``while``. Esta instrucción prueba si hay un valor de cadena dentro de ``user_input``. Si el ciclo ``while`` se ejecuta por primera vez, no hay ningún valor, por lo que no hay nada que almacenar en ``inputs``. Después de que se ejecute por primera vez, ``user_input`` siempre conserva el valor que el usuario acaba de escribir. Dado que ``while`` está probando para asegurarse de que el valor no es igual a done (la palabra que el usuario escribirá para salir de la aplicación), sabe que el valor actual es uno que puede agregar a la lista.

> Es posible que en otros lenguajes de programación hayas visto el uso del ciclo 'do', lo que permite realizar una verificación al final del ciclo. En python no existe un ciclo 'do'.

### Uso de ciclos ``for`` con listas

En Python, las listas pueden almacenar cualquier tipo de valor, como cadenas o números:

```
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
```

Puedes acceder a cualquier elemento de una lista poniendo el índice entre corchetes ([]) después del nombre de la variable. Los índices comienzan a partir de 0:

```
print("The first planet is ", planets[0])
print("The second planet is ", planets[1])
print("The third planet is ", planets[2])
```

También puede determinar el número de elementos de una lista mediante ``len``. Por lo tanto, podría usar un ciclo ``while`` y un contador para recorrer en ciclo o en iteración cada elemento de la lista. Dado que se trata de una operación tan común, Python proporciona ciclos ``for``, que puedes usar para recorrer en iteración las listas.

> Python tiene muchos tipos que se pueden recorrer en ciclo. Estos tipos se conocen como iterables.

Las listas de Python son iterables y se pueden usar con un ciclo ``for``. Se usa un ciclo ``for`` con objetos iterables que va a recorrer en ciclo un número conocido de veces, una vez para cada elemento del objeto iterable.

### Acerca de los ciclos ``for``
Este es un ciclo ``for`` de ejemplo que hace una cuenta atrás, de 4 a 0:

```
countdown = [4, 3, 2, 1, 0]
for number in countdown:
    print(number)
print("Blast off!! 🚀")
```

El ciclo ``for`` es una instrucción con cinco partes importantes:

* La palabra ``for``, seguida de un espacio.
* El nombre de la variable que quieres crear para cada valor de la secuencia (*number*).
* La palabra ``in``, entre espacios.
* El nombre de la lista (*countdown*, en el ejemplo anterior) u objeto iterable que quieres recorrer en ciclo, seguido de dos puntos (``:``).
* El código que quieres ejecutar para cada elemento del objeto iterable, separado por espacios en blanco anidados.

Vamos a cambiar el código anterior para que espere un segundo entre cada número mediante la función ``sleep()``:

```
# De la biblioteca time, importamos (traemos) la clase sleep

from time import sleep

# Creamos una lista de 5 números llamada countdown
countdown = [4, 3, 2, 1, 0]

# Para cada número en countdown
for number in countdown:
    #Muestra el número
    print(number)

    # Espera (1segundo)
    sleep(1)

# Muestra el mensaje Blast off
print("Blast off!! 🚀")
```

> La mayoría del código de Python usa cuatro espacios como la unidad del espacio en blanco (sangría). Para ahorrar tener que presionar la barra espaciadora cuatro veces, la mayoría de los editores tienen una función rápida de teclado con la tecla ``Tab``, que inserta cuatro espacios.

---
## Resumen

En este módulo, hemos creado una aplicación que solicita a los usuarios que escriban una lista de nombres de planetas, los almacenan y, después, los muestran.

Dado que no sabíamos cuántos planetas escribirían los usuarios, usamos un ciclo ``while``. Los ciclos ``while`` se usan para ejecutar un bloque de código mientras una condición es ``True``.

Hemos almacenado cada nombre del planeta en una lista.

Después de crear la lista de planetas, usamos un ciclo ``for`` para recorrerla en iteración. Los ciclos ``for`` se usan con listas y otros objetos iterables para ejecutar código un número conocido de veces, una por cada elemento de la lista de nombres de planetas.

En este módulo, has aprendido a:

* Identificar cuándo usar un ciclo ``while`` o uno ``for``.
* Usar un ciclo ``while`` para ejecutar una tarea varias veces, siempre y cuando una condición determinada siga siendo True.
* Usar un ciclo ``for`` para recorrer en ciclo los datos de la lista.


---

Curso Propedútico de Python para Launch X - Innovacción Virtual.

Material desarrollado con base en los contenidos de MSLearn y la metáfora de LaunchX, traducción e implementación por: Fernanda Ochoa - Learning Producer de LaunchX.

Redes:
* GitHub: [FernandaOchoa](https://github.com/FernandaOchoa)
* Twitter: [@imonsh](https://twitter.com/imonsh)
* Instagram: [fherz8a](https://www.instagram.com/fherz8a/)
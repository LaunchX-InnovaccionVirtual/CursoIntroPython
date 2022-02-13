# Introducción

Con frecuencia tendrás que trabajar con datos más complejos que cadenas y valores booleanos. En este módulo se te proporcionan las herramientas para hacerlo. Ahora se acotará el tema mediante el análisis de un escenario.

## Escenario: Análisis de un sistema solar

Imagina que vas a crear un programa para analizar el número de lunas en diferentes planetas del sistema solar. Quieres mostrar información al usuario y poder calcular valores diferentes, como el número total de lunas en el sistema solar. Sería tedioso hacerlo con variables, que solo pueden almacenar una cadena o un número.

En este módulo, crearás un programa que puede realizar estos tipos de operaciones. Utilizaremos diccionarios de Python para modelar los datos. Al final del módulo, podrás trabajar con diccionarios de Python para almacenar datos complejos.

## ¿Qué aprenderás?
En este módulo, podrás hacer lo siguiente:

* Identificar cuándo se debe usar un diccionario.
* Crear y modificar datos dentro de un diccionario.
* Trabajar con métodos de diccionario para acceder a los datos del diccionario.

## ¿Cuál es el objetivo principal?

Usar una estructura de diccionario dentro de la aplicación para almacenar datos en un formato que facilite la búsqueda de valores.

---

## Introducción a los diccionarios de Python

Las variables de Python pueden almacenar varios tipos de datos. Anteriormente, hemos aprendido que puedes almacenar cadenas y números:

```
name = 'Earth'
moons = 1
```

Aunque esto funciona para cantidades más pequeñas de datos, puede ser cada vez más complejo cuando se trabaja con datos relacionados. Imagina que quieres almacenar información sobre las lunas de la Tierra y la Luna.

```
earth_name = 'Earth'
earth_moons = 1

jupiter_name = 'Jupiter'
jupiter_moons = 79
```

Observa cómo se duplican las variables con prefijos diferentes. Esto puede resultar difícil de manejar. Con frecuencia tendrás que trabajar con conjuntos de datos relacionados, como por ejemplo: el promedio de precipitaciones durante varios meses en distintas ciudades, almacenarlos como valores individuales no es una opción viable. Aquí es donde los diccionarios de Python pueden ayudarnos.

Los diccionarios de Python permiten trabajar con conjuntos de datos relacionados. Un diccionario es una colección de pares clave-valor. Piensa que es como un grupo de variables dentro de una cajita, donde la clave es el nombre de la variable y el valor es el valor almacenado en su interior.

### Creación de un diccionario

Python usa llaves (``{ }``) y dos puntos (``:``) para indicar un diccionario. Puedes crear un diccionario vacío y agregar valores más adelante, o bien rellenarlo en el momento de la creación. Cada clave o valor está separado por dos puntos y el nombre de cada clave se incluye entre comillas como un literal de cadena. Como la clave es un literal de cadena, puede usar el nombre que sea adecuado para describir el valor(Sí el que tu quieras).

Ahora crearemos un diccionario para almacenar el nombre del planeta Tierra y el número de lunas que tiene:

```
planet = {
    'name': 'Earth',
    'moons': 1
}
```

Tiene dos claves, `'name'` y `'moons'`. Cada una se comporta igual que una variable: tienen un nombre único y almacenan un valor. Pero se incluyen dentro de una única variable más grande, denominada `planet`.

Como sucede con las variables convencionales, debes asegurarte de que usas los tipos de datos correctos. En el valor `moons` de `1` en el ejemplo anterior, no se han incluido comillas alrededor del número, porque se quiere usar un entero. Si hubieras usado `'1'`, Python lo vería como una cadena, lo que afectaría a la capacidad de realizar cálculos.

A diferencia de las variables convencionales, los nombres de clave *no* necesitan seguir las reglas de nomenclatura estándar para Python. Por lo que te recomendamos ser más descriptivo en el código.

### Lectura de los valores de un diccionario

Podemos leer valores dentro de un diccionario. Los objetos de diccionario tienen un método llamado `get` que puedes usar para acceder a un valor mediante su clave. Si queremos imprimir `name`, funcionaría de la siguiente manera:

```
print(planet.get('name'))

# Muestra Earth
```

Como podrías sospechar, el acceso a los valores de un diccionario es una operación común. Afortunadamente, hay un acceso directo. También puedes pasar la clave entre corchetes (`[ ]`). Utilizando menos código que `get` y la mayoría de los programadores utilizan esta sintaxis en su lugar. Podemos reescribir el ejemplo anterior de la siguiente forma:

```
# planet['name'] es idéntico a usar planet.get('name')
print(planet['name'])

# Muestra Earth
```
Aunque el comportamiento de `get` y los corchetes (`[ ]`) suele ser el mismo para recuperar elementos, hay una diferencia principal. Si una clave no está disponible, `get` devuelve `None` y `[ ]` genera un error `KeyError`.

```
wibble = planet.get('wibble') # Regresa None
wibble = planet['wibble'] # Arroja un KeyError
```

*Cómo te podrás dar cuenta, funcionan con una estructura similar a las listas. Ya que en el caso de las listas accedemos a cada uno de sus elementos a través de su índice (posición iniciando en 0) y en el caso de un diccionario, accedemos a sus elementos mediante la 'clave'*

### Modificación de valores de un diccionario

También puedes modificar valores dentro de un objeto de diccionario, con el método `update`. Este método acepta un diccionario como parámetro (sí, parámetro por que un diccionario es un rango de valores) y actualiza los valores existentes con los nuevos que proporciones. Si quieres cambiar `name` para el diccionario `planet`, puedes usar lo siguiente, por ejemplo:

```
planet.update({'name': 'Makemake'})

# name ahora es Makemake
```

Al igual que se usa el acceso directo de corchetes (`[ ]`) para leer valores, se puede utilizar para modificar valores. La principal diferencia en la sintaxis es que se usa `=` (a veces denominado operador de asignación) para proporcionar un nuevo valor. Para modificar el ejemplo anterior y cambiar el nombre, puedes usar lo siguiente:

```
planet['name'] = 'Makemake'

# name is now set to Makemake
```

La principal ventaja de usar `update` es la capacidad de modificar varios valores en una operación. Los dos ejemplos siguientes son lógicamente los mismos, pero la sintaxis es diferente. Puedes usar la sintaxis que creas más adecuada. Para actualizar valores individuales, la mayoría de los desarrolladores eligen corchetes.

En el ejemplo siguiente se hacen las mismas modificaciones en la variable `planet` y se actualizan el nombre y las lunas. Ten en cuenta que al usar `update` realizas una sola llamada a la función, mientras que el uso de corchetes implica dos llamadas.

```
# Usando update
planet.update({
    'name': 'Jupiter',
    'moons': 79
})

# Usando corchetes
planet['name'] = 'Jupiter'
planet['moons'] = 79
```

### Adición y eliminación de claves

No es necesario crear todas las claves al inicializar un diccionario. De hecho, no es necesario crear ninguna. Siempre que quieras crear una clave, asígnala como harías con una existente.

Imagina que quieres actualizar `planet` para incluir el período orbital en días:

```
planet['orbital period'] = 4333

# el diccionario planet ahora contiene: {
#   name: 'jupiter'
#   moons: 79
#   orbital period: 4333
# }
```

> Los nombres de una clave, como todo lo demás en Python, distinguen mayúsculas de minúsculas. Como resultado, 'name' y 'Name' se consideran dos claves independientes en un diccionario de Python.

Para quitar una clave, usa `pop`. `pop` devuelve el valor y quita la clave del diccionario. Para eliminar `orbital period`, puedes usar el código siguiente:

```
planet.pop('orbital period')

# el diccionario planet ahora contiene: {
#   name: 'jupiter'
#   moons: 79
# }
```

### Tipos de data complejos
Los diccionarios pueden almacenar cualquier tipo de valor, incluidos otros diccionarios. Esto te permite modelar datos complejos según sea necesario. Imagina que debes que almacenar el diámetro de `planet`, que se podría medir alrededor de su ecuador o de los polos. Puedes crear otro diccionario dentro de `planet` para almacenar esta información:

```
# Añadimos los datos
planet['diameter (km)'] = {
    'polar': 133709,
    'equatorial': 142984
}

# el diccionario planet ahora contiene: {
#   name: 'Jupiter'
#   moons: 79
#   diameter (km): {
#      polar: 133709
#      equatorial: 142984
#   }
# }
```
Para recuperar valores en un diccionario anidado, debe puedes utilizar corchetes `[ ]` o llamar a `get`.

```
print(f'{planet['name']} polar diameter: {planet['diameter (km)']['polar']}')

# Salida: Jupiter polar diameter: 133709
```

## Programación dinámica con diccionarios

En el programa, quieres realizar varios cálculos, como el del número total de lunas. Además, a medida que progreses en programación, es posible que necesites cargar este tipo de información desde archivos o una base de datos, en lugar de programarlos directamente en Python.

Para ayudar a admitir estos escenarios, Python te permite tratar las claves y los valores dentro de un diccionario como una lista. Puedes determinar de manera dinámica las claves y los valores, y realizar varios cálculos.

Imagina un diccionario en el que se almacenan cantidades mensuales de precipitaciones. Es probable que tengas claves para cada mes y sus precipitaciones asociadas. Quieres sumar el total de precipitaciones, y escribir el código para realizar la operación mediante cada clave individual sería bastante tedioso.

### Recuperación de todas las claves y valores
El método `keys()` devuelve un objeto de lista que contiene todas las claves. Puedes usar este método para iterar por todos los elementos del diccionario.

Imagina que tiene el siguiente diccionario, en el que se almacenan los últimos tres meses de precipitaciones (rainfall).

```
rainfall = {
    'october': 3.5,
    'november': 4.2,
    'december': 2.1
}
```

Imagina que quiere mostrar la lista de todas las precipitaciones. Puedes escribir el nombre de cada mes, pero sería tedioso, en este caso hacemos uso del método `keys()`.

```
for key in rainfall.keys():
    print(f'{key}: {rainfall[key]}cm')

# Salida:
# october: 3.5cm
# november: 4.2cm
# december: 2.1cm
```
*Para cada clave en las claves(keys()) contenidas en `rainfalls`:  muestra la clave que estás iterando (meses):  así como el valor (número) de la clave que estamos iterando (clave-mes : valor-número) en cm* 

### Determinando la existencia de una clave en un diccionario

Al actualizar un valor en un diccionario, Python sobrescribirá el valor existente o creará uno en su defecto, si la clave no existe. Si quieres agregar un valor en lugar de sobrescribirlo, puedes comprobar si la clave existe mediante `in`. Por ejemplo, si quieres agregar un valor a diciembre o crear uno si no existe, puedes usar lo siguiente:

```
# El valor de december: 2.1cm

# Si, 'december' existe en rainfall
if 'december' in rainfall:
    # rainfall [en la posición december] es igual a
    # rainfall [en la posición december] + 1 (2.1+1)
    rainfall['december'] = rainfall['december'] + 1

# Si no:
else:

    # rainfall [en la posición december] es igual a 1
    rainfall['december'] = 1

# Como december si existe, el valor será 3.1
```
### Recuper todos los valores de un diccionario

De forma similar a `keys()`, `values()` devuelve la lista de todos los valores de un diccionario sin sus claves correspondientes. Esto puede resultar útil cuando se usa la clave con fines de etiquetado, como en el ejemplo anterior, en el que las claves son el nombre del mes. Puedes usar `values()` para determinar el importe total de las precipitaciones:

```
#Total de precipitaciones 0
total_rainfall = 0

# Para cada valor en los valores de rainfall
for value in rainfall.values():
    
    # El total de las precipitaciones será igual a ese mismo + el valor que se está iterando

    total_rainfall = total_rainfall + value

# Muestra 'Hay un total de precipitaciones (el valor total) en centímetros en el último cuarto (haciendo referencia al cuarto del año)

print(f'There was {total_rainfall}cm in the last quarter')

# Salida:
# There was 10.8cm in the last quarter
```

## Resumen

La mayoría de los programas necesitan datos más complejos que los valores de cadena y número. En el escenario de este módulo, has intentado trabajar con información sobre los planetas del sistema solar. Esta información incluía propiedades como el número de lunas y la circunferencia.

Mediante los diccionarios, has podido crear una variable para almacenar todos los datos relacionados. Después, has usado `keys` y `values` para interactuar directamente con los datos, sin utilizar nombres de clave para realizar cálculos.

Los diccionarios de Python son objetos flexibles, lo que permite modelar datos complejos y relacionados. 

En este módulo, has aprendido a:

* Identificar cuándo se debe usar un diccionario.
* Crear y modificar datos dentro de un diccionario.
* Usar métodos de diccionario para acceder a los datos del diccionario.

---

Curso Propedútico de Python para Launch X - Innovacción Virtual.

Material desarrollado con base en los contenidos de MSLearn y la metáfora de LaunchX, traducción e implementación por: Fernanda Ochoa - Learning Producer de LaunchX.

Redes:
* GitHub: [FernandaOchoa](https://github.com/FernandaOchoa)
* Twitter: [@imonsh](https://twitter.com/imonsh)
* Instagram: [fherz8a](https://www.instagram.com/fherz8a/)
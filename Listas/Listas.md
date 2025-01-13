# Lista

## Introducción
`List` es una colección `inmutable`. Su tamaño no se puede modificar después de inicializarla. Este tipo permite duplicados y almacena elementos en un orden específico.

Supongamos que queremos guardar información sobre los coches que condujimos el año pasado. Hagámoslo con la ayuda de `List`:
````kotlin
val cars = listOf<String>("BMW", "Honda", "Mercedes")
println(cars) // output: [BMW, Honda, Mercedes]
````
Teóricamente podríamos utilizar un `MutableList`para almacenar este tipo de información:
````kotlin
val cars = mutableListOf<String>("BMW", "Honda", "Mercedes")
println(cars) // output: [BMW, Honda, Mercedes]
````
Sin embargo, esto es una mala idea porque cualquiera puede cambiar el contenido de `MutableList` en cualquier momento:
````kotlin
cars[0] = "Renault"
println(cars) // output: [Renault, Honda, Mercedes]
````
Si quieres que el contenido permanezca igual, esto puede ser un problema. `List` es inmutable, por lo que nuestro contenido no cambiará. Si intentas cambiarlo en una lista, obtendrás un error:
````kotlin
val cars = listOf<String>("BMW", "Honda", "Mercedes")
cars[0] = "Renault" // Error
````
## Inicialización
`List` es un tipo genérico. Como viste en los ejemplos anteriores, puedes inicializarlo con la ayuda de `listOf<E>`, donde `E`es el tipo de elementos contenidos en la lista:
````kotlin
val textUsMethod = listOf<String>("SMS", "Email")
````
El tipo también puede derivarse del contexto:
````kotlin
val textUsMethod = listOf("SMS", "Email")
````
Si se necesita inicializar una lista vacía, se puede utilizar el método `emptyList`:
````kotlin
val staff = emptyList<String>()
println(staff) // output: []
````
Otra forma de crear una lista es llamar a una función de construcción - `buildList()`.
````kotlin
val names = listOf<String>("Emma", "Kim")

val list = buildList {
add("Marta")
addAll(names)
add("Kira")
}
println(list) // output: [Marta, Emma, Kim, Kira]
````
## Métodos y propiedades
Recapitulemos las propiedades y métodos de `List`:

- `size` devuelve el tamaño de tu `List`.

- `isEmpty()`muestra si la lista está vacía o no.

Además, `List`tiene un método `get(index)`que devuelve el elemento en esa posición. También puedes usar `[index]`para obtener un elemento . ¡Recuerda que la indexación comienza con cero!

Supongamos que tienes una lista de invitados para una fiesta:
````kotlin
val partyList = listOf("Fred", "Emma", "Isabella", "James", "Olivia")
````
¿Cómo sabemos cuándo es el momento de empezar una fiesta? Comprobemos si los invitados ya están allí mediante el método `isEmpty`. Si la fiesta no está vacía, nos gustaría saber el número de invitados y descubrir quién recibe el primer cóctel de bienvenida.

Obtendremos algo como esto:
````kotlin
if (!partyList.isEmpty()) {
    val size = partyList.size
    val whoIsFirst = partyList[0]
    println("The party will not be lonesome! We already got $size people. And $whoIsFirst was the first to arrive today!")
// The party will not be lonesome! We already got 5 people. And Fred was the first to arrive today!
}
````

Veamos cómo trabajar con otros métodos familiares:

- `indexOf(element)`Devuelve el índice de la primera aparición del elemento especificado. Si no está en la lista, la función devuelve -1.

- `contains(element)`devuelve `true`si el elemento especificado está en la lista y `false` si no.

Emma argumentó que tenía derecho al primer cóctel. ¿Pero es así? Vamos a comprobarlo:
````kotlin
println("Emma came in ${partyList.indexOf("Emma") + 1}") // Emma came in 2
````
Parece que Emma no llegó primero, sino que llegó segundo. Ahora, James quiere saber (como siempre) si Isabella ha llegado:
````kotlin
println("Guys, is it true that Isabella came? It's ${partyList.contains("Isabella")}") // Guys, is it true that Isabella came? It's true
````
Hay muchos otros métodos `List` útiles: ¡visita [`kotlinlang.org`](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin.collections/-list/) y familiarízate con ellos!

## Iterando a través de elementos
Puedes recorrer los elementos `List` con la ayuda del bucle `for`. Veamos un ejemplo:
````kotlin
val participants = listOf("Fred", "Emma", "Isabella")

for (participant in participants) {
    println("Hello $participant!")
}

// Hello Fred!
// Hello Emma!
// Hello Isabella!
````
### Modismo
`List`es una estructura muy común en programación. Como era de esperar, tiene su propio lenguaje.

Ya has visto algunas formas de crear un archivo `List`. Como siempre, la comunidad Kotlin recomienda utilizar la forma más corta.
````kotlin
val list = listOf("a", "b", "c")
````

### Conclusión
Ahora ya conoces la diferencia principal entre `List`y  `MutableList` en Kotlin. 
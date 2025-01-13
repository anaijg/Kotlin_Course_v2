## Funciones sin nombre
Para crear una función Kotlin que no esté vinculada a su nombre, puedes usar una función anónima o una expresión lambda :

- `fun(arguments): ReturnType { body }`– esto comúnmente se llama una " función anónima ".

- { arguments -> body }`– esto comúnmente se llama una "expresión lambda".

Para entenderlo mejor, observe el siguiente ejemplo. En él, se declaran dos funciones: se declaran de formas diferentes, pero hacen lo mismo:
````kotlin
fun(a: Int, b: Int): Int {
return a * b
} // normal function but no name

{ a: Int, b: Int -> a * b } // we shifted the parameter or argument in the curly braces
````
Como veis, calculan la multiplicación de dos números.

Ambas funciones tienen un tipo razonable: (Int, Int) -> Int. Por lo tanto, los tipos funcionan aquí de la misma manera que lo hacen para las funciones 'normales'.

Tenga en cuenta que si desea declarar una lambda sin argumentos , no necesita escribir los "símbolos de flecha". Una definición de lambda sin argumentos se ve así: `{ body }`.

Te preguntarás: ¿cómo podemos usar una función sin un nombre conocido? La respuesta es: hay varias opciones.

Por ejemplo, puede asignar la función a una variable y luego invocarla invocando la variable:
````kotlin
val mul1 = fun(a: Int, b: Int): Int {
    return a * b
}

val mul2 = { a: Int, b: Int -> a * b }

println(mul1(2, 3))  // prints "6"
println(mul2(2, 3))  // prints "6" too
````
También puedes pasar dicha función como argumento o devolver dicha función desde otra función.

Por la misma razón de conveniencia, ahora hablaremos sólo de lambdas.

# Lambdas y azúcar sintáctico
Existen formas de hacer que el código sea más legible para los seres humanos sin cambiar la lógica del código. Si existe una forma de hacerlo en un lenguaje de programación y está relacionada con la sintaxis , la llamamos " azúcar sintáctico" . Kotlin promueve la programación funcional, por lo que hay un azúcar sintáctico para ello.

Recordemos este ejemplo de pasar una función como argumento:
````kotlin
fun isNotDot(c: Char): Boolean = c != '.'
val originalText = "I don't know... what to say..."
val textWithoutDots = originalText.filter(::isNotDot)
println(textWithoutDots) // I don't know what to say
````
En pocas palabras, hemos creado la función isNotDot, que retorna Boolean y luego usa originalText.filter, que iterará sobre cada carácter en la cadena, aplicará la función `isNotDot` y luego retornará una cadena sin puntos. El filtro excluye cualquier carácter en la cadena que retorna falso.

Por si acaso, hay un tema específico para filtrar elementos en una colección .

Ahora, reescribámoslo para pasar una lambda:
````kotlin
val originalText = "I don't know... what to say..."
val textWithoutDots = originalText.filter({ c: Char -> c != '.' })
println(textWithoutDots) // I don't know what to say
````
¡Funciona! En primer lugar, no necesitamos especificar una función y luego tomar la referencia de ella.

Kotlin infiere los tipos de muchos objetos y aquí cno es necesario especificar el tipo:
````kotlin
originalText.filter({ c -> c != '.' })
````
En segundo lugar, hay situaciones en las que la lambda se pasa como último argumento. En ese caso, Kotlin ofrece una forma de eliminar las secuencias de corchetes ({ }) y escribir la lambda fuera de los paréntesis:
````kotlin
originalText.filter() { c -> c != '.' }
````
Si los paréntesis quedan vacíos después de esa operación, puedes eliminarlos:
````kotlin
originalText.filter { c -> c != '.' }
````

Tenga en cuenta que, en ocasiones, la referencia a una función es más legible que una lambda y no hay una respuesta correcta sobre cuál es preferible. Sin embargo, si el código es bastante complejo, en lugar de copiar y pegar alguna lambda, puede ser mejor utilizar una referencia a una función para facilitar el mantenimiento y la reutilización.

# Nombre implícito de un único parámetro: it
Finalmente, cuando hay un solo parámetro en una lambda, existe la posibilidad de omitirlo. El parámetro está disponible bajo el nombre it. El tipo de it se infiere a partir del tipo del argumento que se pasa a la lambda. La versión final del código que elimina los puntos es esta:
````kotlin
val originalText = "I don't know... what to say..."
val textWithoutDots = originalText.filter { it != '.' }
````

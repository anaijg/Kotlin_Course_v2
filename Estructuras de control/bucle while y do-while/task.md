
El bucle `while` incluye un bloque de código y una condición , que es una expresión booleana. Si la condición es `true`, el bucle inicia las instrucciones. Se repiten hasta que la condición se convierte en false. Este bucle comprueba la condición antes de la ejecución.
Ejemplo:
````kotlin
while (condition) {
    // body: do something repetitive
}
````
El cuerpo del bucle puede contener cualquier tipo de instrucción: declaración de variables, lectura de datos de la entrada estándar, expresiones condicionales e incluso bucles anidados.

También se puede entrar en un bucle infinito si la condición permanece `true`:
````kotlin
while (true) {
    // body: do something indefinitely
}
````

Por ahora, considere el siguiente ejemplo. El programa utiliza un bucle while para imprimir números enteros solo cuando la variable es menor que 5.
````kotlin
fun main() {
var i = 0

    while (i < 5) {
        println(i)
        i++
    }

    println("Completed")
}
````

````
0
1
2
3
4
````

Los bucles se pueden utilizar para procesar caracteres, cadenas y cualquier otro tipo de datos. El programa que se muestra a continuación muestra letras en inglés en una sola línea.
````kotlin
fun main() {
var letter = 'A'

    while (letter <= 'Z') {
        print(letter)
        letter++
    }
}
````
````
ABCDEFGHIJKLMNOPQRSTUVWXYZ
````

Es posible obtener el siguiente carácter (según la tabla Unicode) utilizando el operador de incremento.

Nuestro tercer ejemplo contiene un programa que lee cualquier cantidad de palabras de la entrada estándar y luego las imprime. Utiliza la función `hasNext` de `Scanner` para verificar si la entrada tiene un valor.
````kotlin
import java.util.*

fun main() {
    val scanner = Scanner(System.`in`)
    while (scanner.hasNext()) {
        val next = scanner.next()
        println(next)
    }
}
````
````
> Kotlin is a modern language

Output:

Kotlin
is
a
modern
language
````

## Bucle do-while
Primero se ejecuta una vez el bloque de códgo y después se comprueba la condición. Si la condición es true, repite el bucle hasta que la condición se convierta en false. Por lo tanto, el cuerpo siempre se ejecuta al menos una vez.

````kotlin
do {
    // body: do something
} while (condition)
````

El programa que se muestra a continuación lee un número entero de la entrada estándar y lo muestra. Si un usuario ingresa 0, el programa lo imprime y luego se detiene. El siguiente ejemplo muestra el funcionamiento del bucle:
````kotlin
fun main() {
    do {
        val n = readln().toInt()
        println(n)
    } while (n > 0)
}
````

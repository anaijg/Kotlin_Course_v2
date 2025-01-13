## Bucle for
Kotlin proporciona el bucle `for` para iterar a través de rangos, matrices y otras colecciones de elementos. 
````kotlin
for (element in source) {
    // body of loop
}
````
El cuerpo de este bucle consta de una o más instrucciones que se ejecutan para cada elemento de la fuente especificada. El bucle se detiene después de haber procesado el último elemento.

## Iterando a través de un rango
El ejemplo más simple del uso del bucle `for` es imprimir cada elemento de un rango de números enteros.
````kotlin
for (i in 1..4) {
    println(i)    
}
````
Este bucle imprime cada número del 1 al 4.
````
1
2
3
4
````
También es posible iterar a través de un rango de caracteres:
````kotlin
for (ch in 'a'..'c') {
    println(ch)
}
````
Este bucle imprime:
````
a
b
c
````
Tenga en cuenta que no podemos utilizar un rango de cadenas como "da".."dd" para obtener el resultado deseado "da" "db" "dc" "dd". En el rango, solo podemos utilizar caracteres individuales. A partir de ahora, todos los ejemplos serán sobre números porque la iteración a través de caracteres siempre es la misma.

## Iterando a través de una cadena
También puedes iterar sobre cadenas. El código siguiente imprime cada símbolo de una cadena String:
````kotlin
val str = "Hello!"
for (ch in str) {
    println(ch)    
}
````

Este código imprime:
````
H
e
l
l
o
!
````
## Iterando en orden inverso
También puedes iterar un rango en orden inverso.
````kotlin
for (i in 4 downTo 1) {
    println(i)
}
````
Este bucle imprime números del 4 al 1.
````
4
3
2
1
````
Tenga en cuenta que es necesario utilizar `in 4 downTo 1`, no `in 4..1`, para iterar el rango en orden inverso.

## Excluyendo el límite superior
Si necesitamos excluir el límite superior de un rango, podemos restarle uno o escribir `until` en lugar de `..`:
````kotlin
for (i in 1 until 4) {
    println(i)
}
````
Este bucle imprime números del 1 al 3.

## Especificar un paso
Si no especificamos un paso, se asume que el paso es igual a uno (por ejemplo, 1, 2, 3, ...). Aunque si queremos cambiar el paso, debemos especificarlo explícitamente.

En el siguiente ejemplo, imprimimos solo números impares del rango 1..7.
````kotlin
for (i in 1..7 step 2) {
    println(i)
}
````
Este bucle imprime cuatro números:
````
1
3
5
7
````
También puedes usarlo para iterar hacia atrás.
````kotlin
for (i in 7 downTo 1 step 2) {
    println(i)
}
````
Este bucle imprime:
````
7
5
3
1
````

## Un ejemplo: el factorial de un número
Escribamos un programa que calcule el factorial de un número entero dado. Es un clásico. El factorial de n es un producto de números enteros de 1 a n inclusive. Suponiendo que el factorial de 0 es 1, el factorial de 1 también es 1.
````kotlin
fun main() {
val n = readln().toInt()
var result = 1 // starting value of the factorial

    for (i in 2..n) { // the product from 2 to n
        result *= i
    }

    println(result)
}
````
El programa anterior lee un número entero de la entrada estándar. Suponemos que el valor inicial del factorial es 1 y luego lo multiplicamos secuencialmente por números del 2 al n . Si el número de entrada es 1, el resultado es 1. Si el número de entrada es 5, el resultado es 120.

## Un ejemplo: la tabla de multiplicar de números pares
Se puede anidar un bucle `for` en el cuerpo de otro bucle `for`. Los programadores suelen utilizar bucles anidados para procesar estructuras multidimensionales como tablas (matrices), cubos de datos, etc.

Por ejemplo, el código a continuación imprime la tabla de multiplicación de números pares del 2 al 10.
````kotlin
fun main() {
    for (i in 2..10 step 2) {
        for (j in 2..10 step 2) {
            print(i * j)
            print('\t')  // print the product of i and j followed by one tab
        }
        println()
    }
}
````
Imprime:
````kotlin
4   8   12  16  20  
8   16  24  32  40  
12  24  36  48  60  
16  32  48  64  80  
20  40  60  80  100
````
## Modismos
Los distintos tipos de rangos pueden resultar difíciles de entender, pero ofrecen una forma muy cómoda y fácil de leer de escribir código. Aquí te damos un breve recordatorio de la sintaxis para iterar sobre rangos básicos:
````kotlin
for (i in 1..6) { ... }        // closed range: 1, 2, 3, 4, 5, 6
for (i in 1 until 6) { ... }   // half-open range: 1, 2, 3, 4, 5
for (x in 1..6 step 2) { ... } // step 2: 1, 3, 5
for (x in 6 downTo 1) { ... }  // closed range, backward order: 6, 5, 4, 3, 2, 1 
````
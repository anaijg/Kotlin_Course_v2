A veces, es necesario repetir un grupo de insrucciones un número determinado de veces. varias veces. 

Afortunadamente, Kotlin proporciona varias sentencias especiales para repetir bloques de código. Estas instrucciones se conocen como bucles.

## Bucle repeat
Es el bucle más simple, ejecuta n veces las instrucciones situadas llaves {...}. 
````kotlin
repeat(n) {
// statements
}
````
Por ejemplo
````kotlin
fun main() {
    repeat(3) {
        println("Hello")
    }
}
````
````
Hello
Hello
Hello
````

Si n es cero o un número negativo, Kotlin ignorará el bucle. Si n es uno, las instrucciones se ejecutarán solo una vez.

Kotlin tiene puede imprimir la iteración actual con la palabra it:
````kotlin
fun main() {
    repeat(3) {
        println(it)
    }
}
````

````
0
1
2
````

En Kotlin, declarar objetos es bastante sencillo. Puedes hacerlo utilizando varias maneras según tus necesidades, como por ejemplo, declarar un objeto de una clase existente o crear un objeto singleton. Aquí te explico las formas más comunes:

1. Declarar un objeto de una clase existente
   Para crear un objeto de una clase, simplemente puedes usar el constructor sin la palabra clave new (como en otros lenguajes como Java):

````kotlin

class Persona(val nombre: String, val edad: Int)

fun main() {
    val persona = Persona("Juan", 25)
    println("Nombre: ${persona.nombre}, Edad: ${persona.edad}")
}
````
En este ejemplo, persona es un objeto de la clase Persona.

2. Crear un objeto anónimo
   Kotlin permite crear objetos anónimos, útiles cuando necesitas implementar métodos de una interfaz o una clase sin definir una subclase explícita:

````kotlin
interface Accion {
   fun ejecutar()
}

fun main() {
   val accion = object : Accion {
      override fun ejecutar() {
         println("Ejecutando acción")
      }
   }
   accion.ejecutar()
}
````
3. Declarar un singleton
   Kotlin tiene un soporte nativo para declarar singletons mediante la palabra clave object. Un objeto singleton es una instancia única de una clase que puede ser utilizada globalmente en tu aplicación.

````kotlin
object GestorDeTareas {
   fun mostrarTarea() {
      println("Mostrando tarea...")
   }
}

fun main() {
   GestorDeTareas.mostrarTarea()
}
````
El objeto GestorDeTareas es un singleton y puede ser accedido directamente sin necesidad de instanciarlo.
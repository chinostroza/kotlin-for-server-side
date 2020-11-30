# Kotlin for Server Side
    
## Why Kotlin?

1. Kotlin is facil de aprender
	- Kotlin tiene una curva de aprendizaje incremental, es facil sentirse productivo
    
2. Kotlin es obstinado
 	- A diferencia de otros lenguajes, evita el problema social de acordar el estilo con los
      ingenieros al proporcionar una forma única y obstinada sobre cómo hacer algo.
    - Recordar que pasamos más de un 80% leyendo código.
    
3. Kotlin tiene características de lenguaje agradables
	- Inmutabilidad opcional
    - Concepto funcionales, más completos integrados en colecciones
    - Lambdas adecuadas
    - Argmentos con nombre que permiten más, con menos código
    
4. Se puede adoptar de forma incremental
	- JetBrains realmente pensó en Java Interop cuidadosamente
    - Consideró cómo se puede migrar facilmente hacia Kotlin poco a poco
    - Por ejemplo se pueden comenzar escribiendo los test, etc.
    
5. Kotlin tiene una comunidad una gran comunidad
	- Intercambio de conocimiento con la Comunidad de Android
    - Spring soporte oficial
    - Etc.
    
6. Problemas conocidos de Java
	- Null references
    - Boilerplate code
    - Mutability
   	- Esto es debido a la forma en el que el lenguaje fue desarrollado
		- Java permite la creación de variable anulables por defecto
		- Esto permite la mutación de variables por todo el código
    	- Relentiza la productividad del desarrollador
    	- Y quita tiempo a los desarrolladores, para que se efoquen en resolver necesidades comerciales
 
## Adoptando Kotlin

1. Tener la mayor cantidad de desarrolladores hablando de Kotlin
	- Identificar los desarrolladores con experiencia en Kotlin
    
2. Crear un grupo de interes para discutir los pros y contras
	- Establer un criterio común para adoptar
    
3. Entrenarse con los algunos koans , tutoriales, etc para ver fortalezas y debilidades

4. Crear un microservicio y discutir la experiencia

5. Ver al compatibilidad, con la infraestructura actual
     
    
## Referencias

<iframe width="560" height="315" src="https://www.youtube.com/embed/8xAH7RU0Y44" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/dSIIZastK58" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

 - [Building web applications with Spring Boot and Kotlin](https://spring.io/guides/tutorials/spring-boot-kotlin/)
 - [https://kotlin.link/ it's a collection of libraries, frameworks, tools](https://kotlin.link/)
 - [KotlinConf 2019: Kotlin in Space by Maxim Mazin](https://www.youtube.com/watch?v=JnmHqKLgYY4)
 - [Future of Jira Software Powered by Kotlin](https://www.youtube.com/watch?v=4GkoB4hZUnw)
 - [KotlinConf 2019: Bootiful GraphQL with Kotlin by Dariusz Kuc & Guillaume Scheibel](https://www.youtube.com/watch?v=7YJyPXjLdug)
 - [Streamlining Server-Side App Development with Kotlin](https://medium.com/adobetech/streamlining-server-side-app-development-with-kotlin-be8cf9d8b61a)
 - [How we write (backend) Kotlin code in the Content Acquisition domain of Springer Nature Digital IT.](https://github.com/springernature/kotlin-playbook)
 - [Kotlin Development Plan](https://www.intuit.com/blog/uncategorized/kotlin-development-plan/)
 - [5 Reasons Why N26 is Moving to Kotlin](https://medium.com/insiden26/5-reasons-why-n26-is-moving-to-kotlin-f920b184ab58)
 - [Why We Write Micro-Services in Kotlin](https://spruce.co/blog/why-we-write-micro-services-in-kotlin)
 - [Introducing Kotlin at ING, a long but rewarding story](https://medium.com/ing-blog/introducing-kotlin-at-ing-a-long-but-rewarding-story-1bfcd3dc8da0)
 - [QLDB at Amazon](https://talkingkotlin.com/qldb/)
 - [Kotlin for Java Developers](https://www.coursera.org/learn/kotlin-for-java-developers/home/welcome)
 
 
## Kotlin language features

## Intro

### Hello World
### Variables

1. val
	- Solo de lectura
    - Se puede asignar una sola vez
    
2. var
	- mutable
    
```kotlin
fun main(){
	val question : String = 
    	"life, the universe, " +
        "and everything"
    println("$question")
    //question = "sure?"
}
```

3. Local type inference

```kotlin
fun main(){
	val greeting = "Hi!"
	var number = 0
	println("$greeting Hola $number")
}
```
	- Kotlin is a statically-type language
    - Which means that every variable, every expression has a type
    - Even if you omit the type, the compiler just infers it for you
    
4. Why doesn't the following code compile?

```kotlin
fun main(){
	var string = 1
	string = "abc"
}
```

	1. Because you can't re-assign var
    2. Because you can't assign an integer value to a variable of String type
    3. Because you can't assign a string literal to a variable of Int type
    
5. Is it possible to modify an object stored in *val* ?

	1. yes
    2. no

6. why doesnt't the following code compile?

```kotlin
fun main(){
	val list = listOf("Java")
    list.add("Kotlin")
}
```

	1. Because you can't modify a read-only list
    2. Because you can't modify an object stored in val
    
7. *Prefer val to var*

8. Don't omit types (specify them explicitly)
   if they might be not clear from the context
   
## Functions

1. This function returns a maximum of two values

```kotlin
fun max(a: Int, b: Int): Int {
	return if ( a > b ) a else b
}

fun main(){
	println( max(1,2) )
}
```

2. If your function simply returns one expression
   you can use an alternative syntax, so-called, *"function with expression body"*
   
```kotlin
fun max(a: Int, b: Int): Int = if ( a > b ) a else b

fun main(){
	println( max(1,2) )
}
```

3. Function returning Unit

```kotlin
fun max(a: Int, b: Int): Int = if ( a > b ) a else b


fun displayMax(a: Int, b:Int) {
// fun displayMax(a: Int, b:Int) : Unit {
// es lo mismo
println( max(a,b) )
}

fun main(){
	displayMax( 1, 2 )
}
```

4. In Kotlin you can define functions everywhere

```kotlin
// Top-level function
fun topLevel() = 1
// Member function
class A {
    fun member() = 2
}

// Local function
fun other() : Int{
    fun local() = 3
    return local()
}

fun main(){
    val out = A()
    println ( out.member())
    println(other())
}
```

## Named & default arguments

1. What will be printed?

```kotlin
fun main(){
	println(listOf('a','b','c').joinToString(
    separator = "", prefix = "(", postfix =")"))
}
```

2. You can specify the names of the arguments directly in the code
   that often makes the invocation more readable
   
3. What will be printed?

```kotlin
fun displaySeparator(character: Char = '*', size: Int = 10){
	repeat(size) {
    	print(character)
    }
}

fun main(){
	displaySeparator(3,'5')
}
```

4. In Kotlin, there are no implicit conversions

5. How many argument combinations are possible?

```kotlin
fun sum(a: Int = 0, b: Int = 0, c: Int = 0) = a + b + c 

fun main(){    
	sum(a = 1, b = 2)
    sum(c = 3)
    ...
}
```

## Conditionals: if & when

1. *if* is an expression in Kotlin

```kotlin
val max = if (a > b) a else b
```

2. In Kotlin ***No*** ternay operator in Kotlin

3. ***when*** as ***switch***

```kotlin
enum class Color {
	BLUE, ORANGE, RED
}
fun getDescription(color: Color): String = 
	when (color) {
    	BLUE -> "cold"
        ORANGE -> "mild"
        RED -> "hot"
    }
```

4. You should always replace if with when ?

	1. True
    2. False

## Loops



## Exceptions

## Kotlin Scope Functions

### let
- Return : Lambda result
- Context object : it
### apply
- Return: context object
- Context object : this
### run
- Return : lambda result
- Context objetc : 
### with
- Return : lambda result
- Context object : this
### also
- Return : context object
- Context object : it
## Extensions Functions

1. Extension Functions, extends the class

```kotlin
fun String.lastChar() = this.get( this.length - 1 )
```

2. It is defined outside of the class but can be
   called as a regular member to this class
   
3. The time that the function extends is called a Receiver
   here, String is the receiver of the lastChar function
   
4. We can access the receiver by this reference

5. *this* can be ommitted

```kotlin
fun String.lastChar() = get(length - 1)
```

6. An important thing to note here is that you
   cant't define an extension and use it everywhere
   
7. You have to import it explicitly

```kotlin
import com.example.util.lastChar
val c: Char = "abc".lastChar()
```

8. How many arguments does the *repeat* function have it you call it from Java?

```kotlin
fun String.repeat(n: Int): String {
	val sb = StringBuilder(n* length)
    for (i in 1..) {
    	sb.append(this)
    }
    return sb.toString()
}
```
	1. 1
    2. 2
    3. 3
    
9. Is it possible to call a *private* member of *String* inside an extension function to *String*

```kotlin
fun String.lastChar() = get(length -1)
```


## Examples from the Standard Library

1. Extensions play an important role in the language
2. In fact, ***Kotlin standard library is just Java standard library + extensions***
3. That provides very smooth interoperability between Java code and Kotlin code

## Calling Extensions

## Importance of extensions


## Null safety

 <img src="https://www.intuit.com/blog/wp-content/uploads/2019/06/Screen-Shot-2019-06-21-at-11.26.15-AM.png" />


## Nullable types

### El error del billon de dolares


1. La idea es generar los NPE en tiempo

   de compilación y no en tiempo de ejecución

   
```kotlin

fun main(){

	val s1: String = "Nunca soy null"

    println(s1)

}	

```

2. Y si soy null?


```kotlin

fun main(){

	val s1: String = null

    println(s1)

}

```

3. Para esto tenemos los tipos Nulables


```kotlin

fun main(){

	val s2: String? = "Puedo ser null y también puedo ser String"

    println(s2)

}

```

4. Y que pasa si soy null

```kotlin

fun main(){

	val s2: String? = null

    println(s2)

}

```

### Checking for null in conditions


5. Chequear **null** con una **condición**

```kotlin

fun main(){

	val s: String? = null
    
    val length = if (s != null) s.length else null

    println(length)

}

```

### Safe Calls

6. La segunda opción es usar el **Safe Call operator** *?.*


```kotlin

fun main(){

	val s: String? = null

    val length  = s?.length

    println(length)

}

```

7. Asignando un valor

```kotlin

fun main(){

	val s: String? = null

    val length  = s?.length ?: 0

    println(length)

}

```

8. ¿ Que estamos imprimiento aquí ?


```kotlin

fun main(){

val a: Int? = null 

val b: Int? = 1 

val c: Int = 2


val s1 = (a ?: 0) + c 

val s2 = (b ?: 0) + c 

print("$s1$s2")

}

```

9. ¿ Qué va a pasar ?

```kotlin

class Name{

    val value :String = ""

}

fun isFoo1(n: Name) = n.value == "foo"

//fun isFoo2(n: Name?) = n.value == "foo"

//fun isFoo3(n: Name?) = n != null && n.value == "foo"

//fun isFoo4(n: Name?) = n?.value == "foo"



fun main(args: Array<String>) {

    isFoo1(null)

    //isFoo2(null)

    //isFoo3(null)

    //isFoo4(null)

}

```
10. ¿ Qué va a pasar ?


```kotlin

class Name{

    val value :String = ""

}

//fun isFoo1(n: Name) = n.value == "foo"

fun isFoo2(n: Name?) = n.value == "foo"

//fun isFoo3(n: Name?) = n != null && n.value == "foo"

//fun isFoo4(n: Name?) = n?.value == "foo"

fun main(args: Array<String>) {

    //isFoo1(null)

    isFoo2(null)

    //isFoo3(null)

    //isFoo4(null)

}

```

11. ¿ Qué va a pasar ?

```kotlin

class Name{

    val value :String = "foo"

}

//fun isFoo1(n: Name) = n.value == "foo"

//fun isFoo2(n: Name?) = n.value == "foo"

fun isFoo3(n: Name?) = n != null && n.value == "foo"

//fun isFoo4(n: Name?) = n?.value == "foo"

fun main(args: Array<String>) {

    //isFoo1(null)

    //isFoo2(null)

    println(isFoo3(Name()))

    //isFoo4(null)

}

```

12. ¿ Qué va a pasar ?

```kotlin

class Name{

    val value :String = "foo"

}

//fun isFoo1(n: Name) = n.value == "foo"

//fun isFoo2(n: Name?) = n.value == "foo"

//fun isFoo3(n: Name?) = n != null && n.value == "foo"

fun isFoo4(n: Name?) = n?.value == "foo"

fun main(args: Array<String>) {

    //isFoo1(null)

    //isFoo2(null)

    //println(isFoo3(Name()))

    println(isFoo4(null))

}

```

13. ¿ Que se va a imprimir ?


```kotlin

fun main(){

	val x: Int? = 1

	val y: Int = 2

	val sum = x ?: 0 + y

	println(sum)

}

```

## Lambdas

### Funciones anónimas

1. ¿ Por que se llaman funciones anónimas ?

1.1 Como es en Java


```kotlin

button.addActionListener(new ActionListener(){

	@Override

    public void actionPerformed(ActionEvent e){

    	System.out.println("Hi");

    }

});

```

### Lambdas

2. ¿ Entonces que son las funciones Lambda ?

   **son funciones anónimas que puede ser usadas como una expresión**

```kotlin

button.addActionListener { println("Hi") }

```

3. Lambda Syntax


```kotlin

 { x: Int, y: Int -> x + y }

```

```kotlin

 |--Parametros--|   |-Body-|  

 { x: Int, y: Int -> x + y }

```

4. Pasando una función Lambda como parámetro


```kotlin

list.any({ i: Int -> i > 0 })

```

5. Cuando la función Lambda es el último parámetro

   esta puede ser movida fuera de los parentesis


```kotlin

list.any() { i: Int -> i > 0 }

```

6. Y si los parentesis están vacios, estos se pueden omitir ( :) )


```kotlin

list.any { i: Int -> i > 0 }

```

7. Y si el tipo de argumento puede ser inferido

   este se puede omitir. si es claro desde el contexto


```kotlin

list.any { i -> i > 0 }

```

8. Y si el lambda tiene un solo argumento


```kotlin

list.any { it > 0 }

```

9. Si necesitas expresar alguna logica más complicada

   puedes usar **Multi-line Lambda**

   La última expresión es el resultado

  
```kotlin

list.any { 

	println("processing $it")

	it > 0 

}

```

### Common Operations on collections

10. Encuentra el resultado de está expresión

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)


enum class Gender { MALE, FEMALE }



val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

    println( heroes.last().name )

}

```

11. ¿ Cual es el resultado ?


```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)



enum class Gender { MALE, FEMALE }



val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

    println( heroes.firstOrNull { it.age == 30 }?.name )

    //println( heroes.first { it.age == 30 }.name )

}

```

12. ¿ Cual es el resultado ?

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)

enum class Gender { MALE, FEMALE }

val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){
    println( heroes.map { it.age }.distinct().size )
}

```

13. ¿ Cual es el resultado ?

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)

enum class Gender { MALE, FEMALE }

val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

    println( heroes.filter { it.age < 30 }.size )

}

```
14. ¿ Cual es el resultado ?

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)

enum class Gender { MALE, FEMALE }

val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

	val (youngest, oldest) = heroes.partition { it.age < 30 }

    println( oldest.size )

    println( youngest.size )

}

```
15. ¿ Cual es el resultado ?

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)


enum class Gender { MALE, FEMALE }


val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

	println( heroes.maxBy { it.age }?.name )

}

```

16. ¿ Cual es el resultado ?


```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)

enum class Gender { MALE, FEMALE }


val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

	println( heroes.all { it.age < 50 } )

}

```

17. ¿ Cual es el resultado ?

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)

enum class Gender { MALE, FEMALE }

val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

	println( heroes.any { it.gender == Gender.FEMALE } )

}

```

18. ¿ Cual es el resultado ?

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)

enum class Gender { MALE, FEMALE }

val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

	val mapByAge: Map<Int, List<Hero>> = 

  heroes.groupBy { it.age }

val (age, group) = mapByAge.maxBy { (_, group) -> 

  group.size

}!!

println(age))

}

```

19. ¿ Cual es el resultado ?

```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)

enum class Gender { MALE, FEMALE }

val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

	val mapByName: Map<String, Hero> = heroes.associateBy { it.name }

	println(mapByName["Frenchy"]?.age)

}

```

20. ¿ Cual es el resultado ?


```kotlin

data class Hero(

    val name: String,

    val age: Int,

    val gender: Gender?

)



enum class Gender { MALE, FEMALE }



val heroes = listOf(

    Hero("The Captain", 60, Gender.MALE),

    Hero("Frenchy", 42, Gender.MALE),

    Hero("The Kid", 9, null),

    Hero("Lady Lauren", 29, Gender.FEMALE),

    Hero("First Mate", 29, Gender.MALE),

    Hero("Sir Stephen", 37, Gender.MALE))



fun main(){

   val (first, second) = heroes

        .flatMap { heroes.map { hero -> it to hero } } 

        .maxBy { it.first.age - it.second.age }!!

	println(first.name)

}
```

## Properties

## More about Properties

## Laze or late initialization

## OPP in Kotlin

## Constructors, Inheritance syntax

1. You call a constructor as a regular function

```kotlin
class A

val a = A()
```

2. Concise primary constructor

```kotlin
class Person(val name: String, val age: Int)
```

3. The main constructor is called the primary constructor

4. Full primary constructor syntax

```kotlin
//				constructor parameter
class Person(name: String){
	// constructor body
    init {
    
    }
}
```

```kotlin
class Person(name: String){
	val name = String
    
    init{
    	this.name = name
    }
}
```

5. Is equal that :

```kotlin
class Person (val name: String)
```

6. ***val/var*** on a parameter creates a property

7. When you put val or var before the parameter

8. That automatically creates a property

9. Without val or var it's on the constructor parameter

10. Changing visibility of a constructor

```kotlin
class InternalComponent
internal constructor(name: String){
...
}
```

11. You can define Secondary constructor

```kotlin
//              primary constructor
class Rectangle(val height: Int, val width: Int){
	// secondary constructor
	constructor(side: Int) : this(side,side) { ... }
}
```

12. You call another constructor using ***this*** keywords

13. Note that if a primary or secondary constructor is present

14. ***No default constructor without arguments is generated***

15. and then later on is automatically generated only if you definne no other constructors

16. ***Different syntax for inheritance***

17. In Kotlin, the syntax to express inheritance is a bit different than in Java

18. You use colon to teplace both extends and implements

19. The same syntax for extends & implements

```kotlin
interface Base
class BaseImpl : Base

open class Parent
				//constructor call
class Child : Parent()
```

20. If you need to pass any arguments to initialize the superclass

21. You put them inside these parenthesis

```kotlin
// Calling a constructor of the parent class
open class Parent(val name: String)
class Child(name: String) : Parent(name)
```

22. Calling a constructor of the parent class

```kotlin
open class Parent(val name: String)
class Child(name: String) : Parent(name)

open class Parent(val name: String)
class Child: Parent {
	constructor(name: String, param: Int) : super(name)
}
```

23. Use the super keyword to call the constructor of the parent class from
    from the secondary constructor
    
24. Initialization order. What will be printed?

```kotlin
open class Parent {
	init { print("parent ")}
}

class Child : Parent() {
	init { print("child ")}
}

fun main() {
	Child()
}
```

1. child
2. child parent
3. parent child

25. Overriding properties. What will be printed ?

```kotlin
open class Parent {
	open val foo = 1
    init {
    	println(foo)
    }
}

class Child: Parent() {
	override val foo = 2
}

fun main(){
	Child()
}
```


## Class Modifiers I

1. In Kotlin, you can use class modifiers to add new semantics to classes.
   Modifiers can instruct the compiler to generate new methods or introduce additional
   constraints.
   
### Enum class

2. Enum class represents an enumerations like in java

3. If you need a class with a fixed number of values

4. You can define the these values as enum constants

```kotlin
enum class Color {
	BLUE, ORANGE, RED
}
```

5. The different with java is that now enum is not a separate instance

6. But a modifier before the class keywork.

7. The most common way to work with enum constants is to use when expressions

```kotlin
import Color.*

enum class Color {
	BLUE, ORANGE, RED
}

fun getDescription(color: Color) =
	when (color){
    	BLUE -> "cold"
        ORANGE -> "mild"
        RED -> "hot"
    }
```

8. You access enum constants by their full names

9. But, if you import enum constants

10. You can use them without explicit specification

```kotlin
package mypackage

import mypackage.Color.*

enum class Color {
	BLUE, ORANGE, RED
}

fun getDescription(color: Color) =
	when (color) {
    	BLUE -> "cold"
        ORANGE -> "mild"
        RED -> "hot"
    }
```

11. Inside enum class, you can define member functions and properties

```kotlin
enum class Color(
    val r: Int, val g: Int, val b: Int

){
    BLUE(0,0,255), ORANGE(255,165,0), RED(255,0,0);
    fun rgb() = ( r * 256 + g ) * 256 + b
}

fun main(){
    println(Color.BLUE.r)
    println(Color.BLUE.rgb())
}
```

### Data class

1. Data modifier generates useful methods:

	- equals, hashcode, copy, toString adn some others
    
    
2. You can call the copy method to copy an instance of

```kotlin
data class Contact(val name: String, val address: String)

val c = Contact("Carlos", "calle larga 1")
val c_copy = c.copy(address = "new address")

fun main(){
    println(c_copy)
}
```

3. What will be printed?

```kotlin
class Foo(val first: Int, val second: Int)
data class Bar(val first: Int, val second: Int)
fun main(){
	val f1 = Foo(1, 2) 
	val f2 = Foo(1, 2) 
	println(f1 == f2)
    
    val f3 = f1
    
    println(f1 == f3)

	val b1 = Bar(1, 2) 
	val b2 = Bar(1, 2) 
	println(b1 == b2)
}
```

4. For data classes the ***right equals*** and ***hasCode***
   methods are generated.
   
```kotlin
data class Bar(val first: Int, val second: Int){
	override funn equals(other: Any?): Boolean {
    	if (this === other) return true
        if (other !is Bar) return false
        return (first == other.first
        	&& second == other.second
    }
    
    override fun hashCode(): Int = first * 31 + second
}
```
   
5. We now compare the elements by their content

6. For the borrowed data class, here we again call equals under the hood

7. But now equals compares the content

8. So we have true as a result

9. Note that the compiler only uses the properties defined inside the primary constructor
   for the automatically generated functions like to-string, equals and hashCode
   
10. To exclude a property from the generated implementations

11. declare it inside the class body

12. Like the nickname property in this example

```kotlin
//Properties in primary constructor

data class User(val email: String){
	var nickname: String? = null
}

fun main(){
	val user1 = User("voldermor@gmail.com")
    user1.nickname = "Voldemort"
    println(user1) // User(email=voldemort@gmail.com)
}
```

13. Then, it won't be included in to-string


## Class modifiers II

### Sealed class

1. sealed modifier n front of the class

```kotlin
interface Expr
class Num(val value: Int): Expr
class Sum(val left: Expr, val right: Expr) : Expr

fun eval(e:Expr): Int = when (e) {
    is Num -> e.value
    is Sum -> eval(e.left) + eval(e.right)
    //else -> throw IllegalArgumentException("Unknown expression")
}

fun main(){
    // 1 + (2 + 3)
    println(eval( Sum( Num(1), Sum( Num(2),Num(3) ) ) ) )
    
}
```

2. Esto no compila, por que nada garantiza

3. Que otra implementación de ***Expr*** , sea considerada en el when

4. Por lo tanto para que pueda compilar necesitas agregar la opcion ***else***

5. As sealed modifiers solves this problem for the case when you already

6. Know you're full hierarchy

```kotlin
sealed class Expr
class Num(val value: Int): Expr
class Sum(val left: Expr, val right: Expr) : Expr

fun eval(e:Expr): Int = when (e) {
    is Num -> e.value
    is Sum -> eval(e.left) + eval(e.right)
}

fun main(){
    // 1 + (2 + 3)
    println(eval( Sum( Num(1), Sum( Num(2),Num(3) ) ) ) )
    
}
```

7. it restricts that class hierarchy

8. Now with sealed modifier

9. we don't need 'else' branch

10. Note that all the sub-classes must be

11. present in the same file as the parents sealed class

12. It works well for simple hierarchies

13. The different with the previous case is

14. that now expression is a class not an interface

15. That's connected with their underlying implementation

16. Under the hood, the sealed class has a private default constructor so

17. that you couldn't accidentally instantiate this class from Java or create
    sub-classes
    
18. I want to mention here that there is no full matching support in Kotlin

19. When with smart costs covers the majority of the cases like this one

20. When you check the upper level of expression of being a specific type

21. Because it's already so useful there is no full support 

22. from more comnplicated comparations


### Nested and inner class

1. Cuando se usan ?


### Objects, object expressions & companion objects

1. ***object*** is a snngleton en kotlin

## Constants

## Generics

## OOP design choices

## Operator Overloading

## Coventions

## (Not) usign operator overloading

## Kotlin for Spring
 

 - [Start your project on](https://start.spring.io)
 - Choose your programming model
 	- The most popular programming model, at least with Java, is annotations.
    
```kotlin
@RestController
@RequestMapping("/api/article")
class ArticleController(private val repository: ArticleRepository) {

	@GetMapping("/")
    fun findAll() = repository.findAllByOrderByAddedAtDesc()
    
    @GetMapping("/{slug}")
    fun findOne(@PathVariable slug: String) = 
    	repository.findBySlug(slug) ?:
        	throw ResponseStatusExeption(NOT_FOUND)
}
```

 - Or functional APIs?
 
```kotlin
@Bean
fun route(repository: ArticleRepository) = router {
	"/api/article".nest {
    	GET("/") {
        	ok().body{respository.findAllByOrder()
        }
        GET("/{slug}") {
        	val slug = it.pathVariable("slug")
            val article = repository.findBySlug(slug) ?:
            	throw ResponseStatusException(NOT_FOUND)
            ok().body(article)
        }
    }
}
```

 - First class Coroutines support
 	- Spring WebFlux
    - Spring MVC (new in Spring Boot 2.4)
    - Spring Data Reactive
    - Spring Messaging (RSocket)
    - Spring Vault
    
    
## Suspending functions
### Spring MVC and WebFlux

```kotlin
@GetMapping("/api/banner")
suspend fun suspendingEndpoint(): Banner {
	delay(10)
    return Banner("title", "Lorem ipsum")
}
```

## Flow
### Spring MVC and WebFlux

- Flow is the coroutines equivalent for Reactor FLux, or similar RxJava Types

```kotlin
@GetMapping("/banners")
suspend fun flow(): Flow<Banner> = client.get()
	.uri("/messages")
    .accept(MediaType.TEXT_EVENT_STREAM)
    .retrieve()
    .bodyToFlow<String>()
    .map { Banner("title", it) }
```

## RSocket

- Backpressure is a feature highlighted in reactive streams

```kotlin
class MessageHandler(private val builder: RSocketRequester.Builder) {

	// ...
    
    suspend fun stream(request: ServerRequest): ServerResponse {
    	val requester = builder
        	.dataMimeType(APPLICATION_CBOR)
            .connectTcpAndAwait("localhost", 9898)
        val replies = requester
        	.route("bot.messages")
            .dataWithType(processor)
            .retrieveFlow<Message>()
        val broadcast = requester.route("bot.broadcast").retrieveFlow<Message>()
        val messages = flowOf(replies, processor.asFlow(), broadcast).flattenMerge()
        return ok().sse().bodyAndwait(messages)
    }
}
```

# Important point's

- 100% of Spring Framework API with null-safety annotations
  -> no NPE for Spring applications written in Kotlin
  
- In Spring Boot 2.3, support for Kotlin data classes with val properties

```kotlin
@ConstructorBinding
@ConfigurationProperties("blog")
data class Blog Properties(val title: String, val banner: Banner) {
	data class Banner(val title: String? = null, val content:String)
}
```

- Spring Security Kotlin DSL
  New in Spring SEcurity 5.4
  
```kotlin
override fun configure(http: HttpSecurity) {
	http {
    	authorizeRequests {
        	authorize("/css/**", permitAll)
            authorize("/user/**", hasAuthority("ROLE_USER"))
        }
        formLogin {
        	loginPage = "/log-in"
        }
    }
}
```

## Spring Boot for Dit

1. Download IntelliJ
2. Generate with [https://start.spring.io/](https://start.spring.io/)
3. Generate github project

## Links

- [https://start.spring.io](https://start.spring.io)
- [Creating a RESTful Web Service with Spring Boot](https://kotlinlang.org/docs/tutorials/spring-boot-restful.html)
- [https://spring.io/guides/tutorials/spring-boot-kotlin](https://spring.io/guides/tutorials/spring-boot-kotlin)
- [https://github.com/spring-projects-experimental/spring-graalvm-native](https://github.com/spring-projects-experimental/spring-graalvm-native)
- [https://github.com/spring-projects-experimental/spring-fu](https://github.com/spring-projects-experimental/spring-fu)
- [Spring Native for GraalVM](https://github.com/spring-projects-experimental/spring-graalvm-native) 

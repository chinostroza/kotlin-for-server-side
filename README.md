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
    - Concepto funcionales, más completos integrados en coleeciones
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

## Named & default arguments

## Conditionals: if & when

## Loops

## Exceptions

## Extensions Functions

## Examples from the Standard Library

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

## Class Modifiers I

## Class modifiers II

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

## Links

- [https://start.spring.io](https://start.spring.io)
- [https://spring.io/guides/tutorials/spring-boot-kotlin](https://spring.io/guides/tutorials/spring-boot-kotlin)
- [https://github.com/spring-projects-experimental/spring-graalvm-native](https://github.com/spring-projects-experimental/spring-graalvm-native)
- [https://github.com/spring-projects-experimental/spring-fu](https://github.com/spring-projects-experimental/spring-fu)
 

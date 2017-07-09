## Item 23: Don't Use raw types in new code

A generic class is one which is_typesafe\_and has one or more type parameters in its declaration. Generic classes and interfaces are collectively known as\_generic types_. But in Kotlin, the compiler forces you to use parameterized type definitions or else it won't compile.

```kotlin
// Parameterized collection of Animals
val listOfAnimals: List<Animal> = listOf(Lion, Tiger, Wolf)
```

#### Benefits of using Generic and Parameterized types

* Produce _typesafe _code
* Warn during compile time rather than fail during runtime
* No manual casting when getting elements from collections.

```kotlin
// Attempt at a generic function using Any
fun random(one: Any, two: Any, three: Any): Any

// Using Type Parameter
 fun <T> random(one: T, two: T, three: T): T
 
// Called as such and infers that T is of type String
val randomGreeting: String = random("hello", "Willkommen", "bonjour")

// This would also compile since the compiler infers that T is of type Any. (The inferred type would be the lowest common supertype)
val any: Any = random("a", 1, false)

// Functions can have two type parameters as well
fun <K, V> put(key: K, value: V): Unit

// Parameterized Class
class Dictionary<K, V>
val dict = Dictionary<String, String>()
```

#### Bounded polymorphism

To limit the use of`Any`in generic usage, bounded polymorphism was introduced which helped restrict the actual parameters to being of the certain type. Kotlin supports upper bound polymorphism. As the name implies, an upper bound restricts the types to those that are subclasses of the bound. To use an upper bound,

```kotlin
fun <T : Comparable<T>> min(first: T, second: T): T {
    val k = first.compareTo(second)
    return if (k <= 0) first else second
}

// Legal since Int and String extend Comparable
val a: Int = min(4, 5)
val b: String = min("e", "c")
```



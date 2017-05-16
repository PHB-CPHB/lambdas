# lambdas

*General

A Lambda expression is a function that is declared, but immediately passed on as an expression. Also known as a "functional literal".

```kotlin
//val sum: (Int, Int) -> Int = { x, y -> x + y }
val sum = { x: Int, y: Int -> x + y }
print("37 + 34 = ")
println(sum(27,34))
```
A lambda expression in kotlin is always surrounded by curly braces, parameter declarations goes inside the parantheses and the body goes after the -> sign. 

Lambdas can also be used as parsing functions into other functions such as this example: 
```kotlin
//A function taking a function
fun <T> lick (bod: () -> T) : T {
    return bod();
}

//Another function taking a collection and a function.
var ints = arrayListOf<Int>(1, 5, 2, 4, 3)

fun <T> max(collection: Collection<T>, less: (T, T) -> Boolean): T? {
    var max: T? = null
    for (it in collection)
        if (max == null || less(max, it))
            max = it
    return max
}

//Prints the max value in the ints list
println(max(ints, {a, b -> a > b}))
```


*Anonymous Functions 

One thing missing from the lambda expression syntax presented above is the ability to specify the return type of the function. In most cases, this is unnecessary because the return type can be inferred automatically. However, if you do need to specify it explicitly, you can use an alternative syntax: an anonymous function.

```kotlin
val doubled = ints.map { it * 2 }
println("Doubled values:")
doubled.forEach { println("$it") }

//Will only print values above 2
println(ints.filter {it > 2})
```


LINQ-style code:
```kotlin
strings.filter { it.length == 5 }.sortBy { it }.map { it.toUpperCase() }
```

Underscore for unused variables (since 1.1)
If the lambda parameter is unused, you can place an underscore instead of its name:
```kotlin
//Ignores the key in the map
map.forEach { _, value -> println("$value!") }
```


    

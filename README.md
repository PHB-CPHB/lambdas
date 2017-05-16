# lambdas

*General

A Lambda expression is a function that is declared, but immediately passed on as an expression. Also known as a "functional literal".


    //val sum: (Int, Int) -> Int = { x, y -> x + y }
    val sum = { x: Int, y: Int -> x + y }
    print("37 + 34 = ")
    println(sum(27,34))
A lambda expression in kotlin is always surrounded by curly braces, parameter declarations goes inside the parantheses and the body goes after the -> sign. 

Lambdas can also be used as parsing functions into other functions such as this example: 

    //A function taking a function
    fun <T> lick (bod: () -> T) : T {
        return bod();
    }


*Anonymous Functions 

One thing missing from the lambda expression syntax presented above is the ability to specify the return type of the function. In most cases, this is unnecessary because the return type can be inferred automatically. However, if you do need to specify it explicitly, you can use an alternative syntax: an anonymous function.

    fun(x: Int, y: Int): Int = x + y

    //it: implicit name of a single parameter
    ints.map { it * 2 }

    val sum = { x: Int, y: Int -> x + y }

LINQ-style code:

    strings.filter { it.length == 5 }.sortBy { it }.map { it.toUpperCase() }

Underscore for unused variables (since 1.1)
If the lambda parameter is unused, you can place an underscore instead of its name:

    map.forEach { _, value -> println("$value!") }

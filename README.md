24. Explain pairs and triple's in Kotlin?

Kotlin doesn't have a built-in Tuple data type like some other programming languages, such as Python. Instead, Kotlin provides data classes called "Pair" and "Triple" which can be used to represent tuples with two or three values, respectively. These classes provide similar functionality to tuples in other languages, such as the ability to group related values together and pass them around as a single object.

In Kotlin, pairs and triples are special data classes that are used to represent a group of related values. Pairs represent two values, while triples represent three values. These classes are commonly used in Kotlin to return multiple values from a function or to store related data in a compact way.

Here's how you can create and use pairs and triples in Kotlin:

Creating a pair:

val pair = Pair("John", 25)

This creates a pair with a string value "John" and an integer value 25.

Accessing values in a pair or triple:

val name = pair.first
val age = pair.second

This accesses the values in the pair by using the first and second properties.

Creating a triple:

val triple = Triple("John", 25, true)

This creates a triple with a string value "John", an integer value 25, and a boolean value true.

val name = triple.first
val age = triple.second
val isMale = triple.third

This accesses the values in the triple by using the first, second, and third properties.

Packing values into a pair or triple:

val name = "John"
val age = 25
val pair = name to age // same as Pair(name, age)

val name = "John"
val age = 25
val isMale = true
val triple = Triple(name, age, isMale)

You can also pack values into a pair or triple by using the to operator or by directly creating an instance of the corresponding class.

Pairs and triples can be used in various situations in Kotlin where you need to group related data together or return multiple values from a function. Here are some common use cases:

Returning multiple values from a function: In Kotlin, a function can only return one value. However, if you need to return multiple values, you can use a pair or triple to group them together and return them as a single object. For example, a function that calculates the minimum and maximum values of an array could return a pair of the two values.

Passing multiple values to a function: Pairs and triples can also be used to pass multiple values to a function. For example, a function that sorts an array could take a pair of the array and a boolean flag indicating whether to sort it in ascending or descending order.

Storing related data: Pairs and triples can be used to store related data in a compact way. For example, a pair could represent a point in 2D space, with the x-coordinate and y-coordinate stored as the first and second values, respectively.

Destructuring: Kotlin provides a feature called destructuring that allows you to extract the values in a pair or triple and assign them to individual variables. This can make your code more readable and expressive. For example, you could destructure a pair representing a point into separate x and y variables.

--------------------------------------------------------------------------

25. Explain Null safety in Kotlin.

Nullability refers to whether a variable or object can have a null value or not. In programming, a null value represents the absence of a value. It is a special value that indicates that a variable or object does not refer to any valid value or object in memory.

In Kotlin, nullability is explicitly specified in the type system using the question mark ("?") notation. A type that ends with "?" is nullable, meaning that it can hold a null value, while a type that does not end with "?" is non-nullable, meaning that it cannot hold a null value.

A null pointer exception (NPE) is a common runtime error that occurs when a program tries to access a null reference or value. In other words, an NPE occurs when you try to use an object that has a null value, which can cause the program to crash or behave unexpectedly. NPEs are a common source of bugs in many programming languages, as they can be difficult to catch and diagnose.

Kotlin's null safety features are designed to help prevent NPEs by enforcing null safety at the language level. By making nullability explicit in the type system and providing tools like the safe call operator and the Elvis operator, Kotlin helps programmers write code that is less likely to encounter NPEs. This can lead to more robust and reliable programs that are easier to maintain and debug.

Here are some key aspects of null safety in Kotlin:

1. Nullable and non-nullable types:

In Kotlin, nullable and non-nullable types refer to whether a variable or object can hold a null value or not. Nullable types are denoted by appending a "?" to the end of the type name, while non-nullable types have no such annotation.

Here are some examples of nullable and non-nullable types in Kotlin:

Non-nullable type:

val x: Int = 10
val y: String = "hello"

In these examples, the variables "x" and "y" are both non-nullable types. This means that they cannot hold a null value. If you try to assign a null value to them, you will get a compilation error. For example:

val z: String = null // compilation error: "Null can not be a value of a non-null type String"

Nullable type:

var str: String? = null
var num: Int? = 5

In these examples, the variables "str" and "num" are nullable types. This means that they can hold a null value. You can assign a null value to them without any issues. For example:

str = null // this is allowed, as str is a nullable type
num = null // this is also allowed, as num is a nullable type

If you try to access a property or method of a nullable variable directly, you will get a compilation error, as the compiler cannot guarantee that the variable is not null. For example:

var str: String? = null
var length = str.length // compilation error: "Only safe (?.) or non-null asserted (!!.) calls are allowed on a nullable receiver of type String?"

To avoid this error, you can use the safe call operator (?.) or the Elvis operator (?:), as explained in my previous answer.

2. Safe call operator:

The safe call operator (?.) in Kotlin is a convenient way to safely access properties or methods of an object that might be null, without having to manually check for null values.

Here's an example to illustrate how the safe call operator works:

val str: String? = null
val length = str?.length

In this example, the variable "str" is a nullable String, which means it could potentially be null. If we want to get the length of the string, we would normally have to check if "str" is null before accessing the length property. However, with the safe call operator, we can simply use "?.length" to get the length of the string, without worrying about null values.

In this case, the expression "str?.length" will evaluate to null, because "str" is null. However, instead of throwing a null pointer exception (NPE), the safe call operator simply returns null. This means that the value of "length" will also be null.

The safe call operator can also be used with method calls. Here's an example:

val str: String? = null
val uppercase = str?.toUpperCase()

In this example, we are calling the toUpperCase() method on the nullable "str" variable. If "str" is null, the safe call operator will return null, and the value of "uppercase" will also be null. If "str" is not null, the toUpperCase() method will be called on the string, and the result will be assigned to "uppercase".

The safe call operator can be used in a chain with other operators, such as the Elvis operator and the not-null assertion operator (!!). This allows for more complex expressions that handle null values in a concise and safe manner.

3. Elvis operator(?:): 

The Elvis operator in Kotlin is named after the famous singer Elvis Presley, whose signature hairstyle resembles the symbol used by the operator (a stylized letter "E" with a curl resembling a quiff).

The operator was introduced in Kotlin as a shorthand way to handle null values and provide default values or fallback operations. Its name was chosen because it represents a fallback option, just like Elvis Presley was often seen as a fallback option for rock and roll music during his career.

The syntax of the Elvis operator is also similar to that of the ternary operator in many programming languages, which is used to provide a fallback value or operation in a concise way. However, the Elvis operator is specifically designed for null-safety in Kotlin, and provides a more concise and expressive way to handle null values.

The Elvis operator (?:) in Kotlin is a shorthand notation for handling null values when assigning a default value or performing a fallback operation. It allows you to provide a default value or operation to use if the left-hand side of the operator evaluates to null.

Here's an example to illustrate how the Elvis operator works:

val str: String? = null
val length = str?.length ?: 0

In this example, we are using the safe call operator (?.) to access the length property of the nullable "str" variable. If "str" is null, the safe call operator will return null. However, we are also using the Elvis operator to provide a default value of 0 in case the length property is null.

So, in this case, the expression "str?.length ?: 0" will evaluate to 0, because "str" is null. If "str" were not null, the length of the string would be returned instead.

The Elvis operator can also be used with method calls or other expressions. Here's an example:

fun foo(str: String?) {
    val uppercase = str?.toUpperCase() ?: "DEFAULT"
    // ...
}

In this example, we are passing a nullable string "str" to a function "foo". Inside the function, we are using the safe call operator to call the toUpperCase() method on "str", and the Elvis operator to provide a default value of "DEFAULT" if the result of the toUpperCase() method is null.

The Elvis operator is a useful shorthand notation for handling null values in a concise and readable way, and can be used in a variety of contexts where you need to provide a default value or fallback operation.

4. Non-null assertion / Double Bang(!!) operator: 

The non-null assertion operator (!!) in Kotlin is a way to tell the compiler that a variable or expression is not null, even if it is declared as nullable. It can be used to explicitly throw a NullPointerException (NPE) if the value is null, and is a way to assert that the value is non-null in a way that is guaranteed to produce an error if the assumption is incorrect.

Here's an example to illustrate how the non-null assertion operator works:

val str: String? = "Hello, world!"
val length = str!!.length

In this example, the variable "str" is declared as a nullable String with a value of "Hello, world!". However, we are using the non-null assertion operator (!!.) to assert that "str" is not null. This means that if "str" is null, a NullPointerException (NPE) will be thrown at runtime.

In this case, since "str" is not null, the expression "str!!.length" will evaluate to the length of the string ("13" in this case).

The non-null assertion operator can be useful in situations where you know that a variable or expression should never be null, but the compiler is unable to infer this automatically. It is often used in combination with the safe call operator (?.) to provide a fallback value or operation in case the value is null.

Here's an example:

fun foo(str: String?) {
    val length = str?.length ?: -1
    val nonNullLength = str!!.length
    // ...
}


In this example, we are defining a function "foo" that takes a nullable string "str" as a parameter. Inside the function, we are using the safe call operator (?.) to access the length property of "str", and provide a fallback value of -1 if it is null. We are also using the non-null assertion operator (!!.) to assert that "str" is not null before accessing its length property, which will throw a NPE if "str" is actually null.

The non-null assertion operator can be a powerful tool in situations where you need to ensure that a value is non-null, but should be used with caution. It is important to only use it when you are certain that the value is not null, as using it on a null value will result in a runtime error.

The term "non-null" is commonly used in Kotlin to refer to types that are declared as not nullable using the "?" operator, such as "String?", which can either hold a string value or null. In contrast, the term "not-null" is typically used in Kotlin to refer to values that are explicitly checked to ensure they are not null using the not-null assertion operator "!!".

So, while "non-null" refers to types that cannot be null, "not-null" refers to values that are verified to be not null. However, the terms are often used interchangeably in Kotlin and their distinction is not always clear.

5. Safe cast operator:

The safe cast operator (?.) in Kotlin is a way to safely cast an object to a specific type without the risk of a ClassCastException. It is used to perform a cast operation on an object only if the object is an instance of the target type, and returns null if the cast fails.

Here's an example to illustrate how the safe cast operator works:

val obj: Any? = "Hello, world!"
val str: String? = obj as? String

In this example, the variable "obj" is declared as an Any type with a value of "Hello, world!". We are using the safe cast operator (as?) to attempt to cast "obj" to a String type. Since "obj" is a String in this case, the cast will succeed and the variable "str" will be assigned the value "Hello, world!".

If "obj" were not a String, the cast would fail and the safe cast operator would return null, resulting in "str" being assigned a value of null.

The safe cast operator is particularly useful when working with types that are not guaranteed to be of a specific type. For example, when working with JSON data, the type of a value may be uncertain and may require casting to a specific type. By using the safe cast operator, you can avoid potential ClassCastException errors and handle unexpected values more gracefully.

Here's another example:

fun printLength(obj: Any?) {
    if (obj is String) {
        val length = obj.length
        println("The length of the string is $length")
    } else {
        println("The object is not a string")
    }
}

val obj: Any? = "Hello, world!"
printLength(obj) // Output: The length of the string is 13

In this example, we are defining a function "printLength" that takes an object "obj" as a parameter. Inside the function, we are using an if statement and the "is" operator to check if "obj" is a String. If it is, we are using the safe cast operator to cast "obj" to a String and access its length property. If it is not a String, we print a message indicating that it is not a string.

By using the safe cast operator, we can ensure that our code handles unexpected values gracefully and avoids potential errors.

26. What is 'as' keyword in kotlin?

The "as" keyword in Kotlin is used for type casting or type coercion, which allows you to convert an object of one type to another type.

Here's an example to illustrate how the "as" keyword works in Kotlin:

val obj: Any = "Hello, world!"
val str: String = obj as String

In this example, we have a variable "obj" of type Any that holds a string value "Hello, world!". We want to cast "obj" to a string type and assign it to the variable "str". To do this, we use the "as" keyword followed by the target type "String". This tells the compiler that we are certain that "obj" is actually of type "String" and should be cast to that type.

If "obj" were not actually a string, a ClassCastException would be thrown at runtime.

The "as" keyword can also be used to perform smart casts, which are a way for the Kotlin compiler to automatically cast objects based on the context in which they are used. For example:

fun printLength(obj: Any) {
    if (obj is String) {
        val strLength = obj.length
        println("The length of the string is $strLength")
    } else {
        println("The object is not a string")
    }
}


In this example, we have a function "printLength" that takes an object of type Any as a parameter. Inside the function, we use the "is" operator to check if the object is actually a string. If it is, we can safely cast it to a string type and use the length property to print the length of the string. If it's not a string, we print a message indicating that the object is not a string.

The "as" keyword is a powerful feature in Kotlin that allows you to work with different types of objects and perform type conversions safely and efficiently. However, it should be used with caution and care, as incorrect use of the "as" keyword can result in runtime errors such as ClassCastException.

27. What is 'in' keyword in kotlin?

The "in" keyword in Kotlin is used for checking whether an element belongs to a collection or a range. It is also used in the "for" loop to iterate over a collection or a range.

Here's an example to illustrate how the "in" keyword works in Kotlin:

val list = listOf("apple", "banana", "orange")
val result = if ("apple" in list) {
    "The list contains an apple"
} else {
    "The list does not contain an apple"
}
println(result)

In this example, we have a list of strings and we check if the string "apple" is in the list using the "in" keyword. If the list contains "apple", the value of the "result" variable will be "The list contains an apple". Otherwise, it will be "The list does not contain an apple".

The "in" keyword can also be used to iterate over a collection or a range using a "for" loop. Here's an example:

val range = 1..5
for (num in range) {
    println(num)
}

In this example, we have a range of integers from 1 to 5 and we use the "in" keyword to iterate over the range in a "for" loop. The loop will print each number in the range from 1 to 5.

The "in" keyword is a simple and intuitive feature in Kotlin that allows you to check if an element is in a collection or a range and to iterate over them in a concise and readable way.

28. Explain Kotlin ranges.

Ranges in Kotlin are a way to represent a sequence of values, typically numeric values, between a start value and an end value, with an optional step value. Ranges are commonly used in looping constructs to iterate over a sequence of values.

There are two types of ranges in Kotlin: ClosedRange and HalfOpenRange.

ClosedRange:

A ClosedRange is a range that includes both the start and end values. It is defined using the .. operator, like this:

val range = 1..10

In the example above, range is a ClosedRange that includes all the integers between 1 and 10 (inclusive).

Some of the commonly used methods available on ClosedRange are:

- contains(element: T): Boolean: Checks if the given element is within the range.
- isEmpty(): Boolean: Checks if the range is empty.
- endInclusive: T: Returns the inclusive end of the range.

```
println(range.contains(5)) // Output: true
println((10..1).isEmpty()) // Output: true
println(range.endInclusive) // Output: 10
```

HalfOpenRange:

A HalfOpenRange is a range that includes the start value but excludes the end value. It is defined using the until operator, like this:

val range = 1 until 10

In the example above, range is a HalfOpenRange that includes all the integers between 1 and 9 (inclusive of 1, exclusive of 10).

```
fun main() {
    // closed range example
    val closedRange = 1..10
    for (i in closedRange) {
        print("$i ")
    }
    // Output: 1 2 3 4 5 6 7 8 9 10
    
    // half-open range example
    val halfOpenRange = 1 until 10
    for (i in halfOpenRange) {
        print("$i ")
    }
    // Output: 1 2 3 4 5 6 7 8 9
}
```

In the example above, we have created a ClosedRange from 1 to 10 and a HalfOpenRange from 1 to 9. We then used a for loop to iterate over the values in each range and print them to the console.

Ranges in Kotlin are not only limited to integers. Ranges can be created for any types that implement the Comparable interface. The Comparable interface defines the compareTo function, which is used to compare two objects of the same type.

For example, we can create a range of characters:

val charRange = 'a'..'z'

In the example above, charRange is a ClosedRange of characters from 'a' to 'z' (inclusive).

We can also create a range of strings:

val stringRange = "apple".."banana"

In the example above, stringRange is a ClosedRange of strings from "apple" to "banana" (inclusive).

When using ranges with custom types, it's important to make sure that the objects being compared are compatible with each other. This means that the objects should have a well-defined ordering that is consistent with the compareTo function. If the objects being compared are not compatible, the code may produce unexpected results or compile-time errors.

Ranges can be used in various ways in Kotlin. For example, they can be used in "for" loops to iterate over a sequence of values, or they can be used to create a subset of an existing collection by filtering out elements that fall outside the range. Ranges are a useful tool for working with sequences of values in Kotlin.

29. How to take input and give output in kotlin?

Input

Using readLine() function

The readLine() function is the simplest way to read input from the console in Kotlin. It reads a line of text from the standard input stream and returns it as a string. You can use the function like this:

fun main() {
    print("Enter your name: ")
    val name = readLine()
    println("Hello, $name!")
}

In this example, we prompt the user to enter their name using the print() function, read the user's input using the readLine() function, and then use string interpolation to print a greeting that includes the user's name.

Using Scanner class

Another way to read input from the console in Kotlin is to use the Scanner class from the Java standard library. The Scanner class provides methods for reading various types of input, such as integers, doubles, and strings. Here's an example:

import java.util.Scanner

fun main() {
    val scanner = Scanner(System.`in`)
    print("Enter your age: ")
    val age = scanner.nextInt()
    println("You entered $age.")
}

In this example, we create a Scanner object and pass the standard input stream as a parameter. We then use the nextInt() method to read an integer value entered by the user, and print the value using string interpolation.

Output

Using print() and println() functions

The print() function is used to print a message to the console without adding a new line, while the println() function is used to print a message and add a new line. Here's an example:

fun main() {
    print("Hello, ")
    println("world!")
}

In this example, we use the print() function to print "Hello, " without a new line, and then we use the println() function to print "world!" with a new line.

Using formatted strings

Kotlin supports string interpolation, which allows you to embed variables and expressions in a string. You can use this feature to format output in a specific way. Here's an example:

fun main() {
    val name = "Alice"
    val age = 30
    println("$name is $age years old.")
}

In this example, we use string interpolation to create a formatted string that includes the user's name and age.

Using printf() function

Kotlin also supports the printf() function, which is similar to the printf() function in C. The printf() function allows you to format output using placeholders for values. Here's an example:

fun main() {
    val name = "Bob"
    val age = 40
    printf("%s is %d years old.", name, age)
}

In this example, we use the printf() function to create a formatted string that includes the user's name and age.

These are some of the ways you can take input and give output in Kotlin. Depending on your specific needs, you may need to use other functions or libraries to work with input and output in Kotlin.

some examples:

readLine()!! - You can use the not-null assertion operator to make sure that the input value is not null. This can be useful when you are sure that the user will enter a value.

readLine()?.toInt() - The safe call operator ?. can be used to check if the user's input can be converted to a number before using the toInt() function.

BufferedReader - The BufferedReader class can be used to read input from the console. It provides methods for reading lines of text, integers, and other data types.

FileReader and FileWriter - The FileReader and FileWriter classes can be used to read and write files in Kotlin.

println() and print() with format specifiers - You can use format specifiers to format the output in a specific way. For example, %d is used to format integers, %f is used to format floating-point numbers, and %s is used to format strings.

System.out.printf() - This method allows you to print output to the console using format specifiers, similar to the printf() function in C.

kotlin.io package - This package provides functions for reading and writing files, working with the console, and more. For example, the readBytes() and writeBytes() functions can be used to read and write binary data from files.

30. Explain Kotlin operator's.

An operator is a symbol that tells the compiler to perform specific mathematical or logical manipulations. 

In Kotlin there are many types of operators:

1. Arithmetic Operators
2. Relational Operators
3. Assignment operator
4. Unary operator
5. Logical operator
6. Bitwise operator
7. In Operator
8. Range Operators
9. Elvis Operator
10. Safe Call Operator

1. Arithmetic Operator

Arithmetic operators are used to perform basic mathematical operations such as addition (+), subtraction (-), multiplication (*), division (/) etc.

|Operator | Description | Expression | Translate to|
|---------|-------------|------------|-------------|
|+	    |	Addition	| a+b		 | a.plus(b)   |
|-	    | Subtraction	| a-b		 | a.minus(b)  |
|*	    | Multiply	| a*b		 | a.times(b)  |
|/	    | Division	| a/b		 | a.div(b)    |
|%	    | Modulus	| a%b		 | a.rem(b)    |

Here are some examples of using arithmetic operators in Kotlin:

```
val x = 10
val y = 5
val z = x + y // z = 15
val a = x - y // a = 5
val b = x * y // b = 50
val c = x / y // c = 2
val d = x % y // d = 0
```

2. Relation / Comparison Operator

Relation operator shows the relation, compares between operands and return a Boolean value (true or false) based on the comparison. Comparison operators are often used in conditional statements, such as if statements, to control the flow of a program based on the comparison result.

| Operator | Description | Expression | Translate to |
| -------- | ----------- | ---------- | ------------ |
| >        | greater than | a>b | a.compareTo(b)>0 |
| <        | Less than | a<b | a.compareTo(b)<0 |
| >=       | greater than or equal to | a>=b | a.compareTo(b)>=0 |
| <=       | less than or equal to | a<=b | a?.equals(b)?:(b===null) |
| ==       | is equal to | a==b | a?.equals(b)?:(b===null) |
| !=       | not equal to | a!=b | !(a?.equals(b)?:(b===null)) |

Here are some examples of using comparison operators in Kotlin:

```
val x = 10
val y = 5

val result1 = x == y // result1 is false
val result2 = x != y // result2 is true
val result3 = x > y // result3 is true
val result4 = x < y // result4 is false
val result5 = x >= y // result5 is true
val result6 = x <= y // result6 is false
```

3. Assignment operator

Assignment operator "=" is used to assign a value to another variable. The assignment of value takes from right to left.

| Operator | Description | Expression | Convert to |
| -------- | ----------- | ---------- | --------- |
| +=       | add and assign | a+=b | a.plusAssign(b) |
| -=       | subtract and assign | a-=b | a.minusAssign(b) |
| *=       | multiply and assign | a*=b | a.timesAssign(b) |
| /=       | divide and assign | a/=b | a.divAssign(b) |
| %=       | mod and assign | a%=b | a.remAssign(b) |

Here are some examples of using the assignment operator in Kotlin:

```
var x = 5 // assigns the value 5 to variable x
var y: Int // declares a variable y of type Int
y = 10 // assigns the value 10 to variable y

val message: String // declares a constant message of type String
message = "Hello, world!" // assigns the value "Hello, world!" to the constant message
```

In the first example, the variable x is assigned the value 5. In the second example, the variable y is declared and assigned the value 10 in separate steps. In the third example, a constant message is declared and assigned the value "Hello, world!".

The assignment operator can also be used with other operators to create compound assignment operators. For example, the expression x += 2 is equivalent to x = x + 2. Here are some examples of using compound assignment operators in Kotlin:

```
var count = 0
count += 5 // equivalent to count = count + 5
count -= 3 // equivalent to count = count - 3
count *= 2 // equivalent to count = count * 2
count /= 4 // equivalent to count = count / 4
```

Compound assignment operators can make code shorter and easier to read, especially when the same variable is being modified multiple times.

4. Unary Operator

Unary operator is used with only single operand. Following are some unary operator given below.

| Operator | Description | Expression | Convert to |
| -------- | ----------- | ---------- | --------- |
| +        | unary plus | +a | a.unaryPlus() |
| -        | unary minus | -a | a.unaryMinus() |
| ++       | increment by 1 | ++a | a.inc() |
| --       | decrement by 1 | --a | a.dec() |
| !        | not | !a | a.not() |

Here are some examples of using unary operators in Kotlin:

```
var x = 5
var y = -x // y is -5
var isTrue = true
var isFalse = !isTrue // isFalse is false
```

Unary operators can be used to perform simple operations on a single value, or to change the sign or logic of a value. They are often used in combination with other operators and control structures to create more complex expressions and algorithms.

5. Logical Operator

Logical operators are used to check conditions between operands.

| Operator | Description | Expression | Convert to |
| -------- | ----------- | ---------- | --------- |
| &&       | return true if all expression are true | (a>b) && (a>c) | (a>b) and (a>c) |
| \|\|       | return true if any expression are true | (a>b) \|\| (a>c) | (a>b) or(a>c) |
| !        | return complement of expression | !a | a.not() |

Here are some examples of using logical operators in Kotlin:

```
var x = 5
var y = 10
var z = 3

// logical AND
if (x < y && y > z) {
    println("x is less than y and y is greater than z")
}

// logical OR
if (x < y || x > z) {
    println("x is either less than y or greater than z")
}

// logical NOT
var isTrue = true
if (!isTrue) {
    println("isTrue is false")
}
```

Logical operators are commonly used in conditional statements and loops to control program flow based on the result of Boolean expressions.

6. Bitwise Operation

In Kotlin, there is not any special bitwise operator. Bitwise operation is done using named function. Bitwise operators are used to perform operations on individual bits of a binary number. In Kotlin, there are six bitwise operators:

	and - bitwise AND
	or - bitwise OR
	xor - bitwise XOR
	inv - bitwise inversion (complement)
	shl - bitwise left shift
	shr - bitwise right shift

| Named Function | Description | Expression |
| -------------- | ----------- | ---------- |
| shl (bits)     | signed shift left | a.shl(b) |
| shr (bits)     | signed shift right | a.shr(b) |
| ushr (bits)    | unsigned shift right | a.ushr(b) |
| and (bits)     | bitwise and | a.and(b) |
| or (bits)      | bitwise or | a.or(b) |
| xor (bits)     | bitwise xor | a.xor(b) |
| inv()          | bitwise inverse | a.inv() |

Here are some examples of using bitwise operators in Kotlin:

```
var x = 0b10101010
var y = 0b11001100

// bitwise AND
var z = x and y // z is 0b10001000

// bitwise OR
z = x or y // z is 0b11101110

// bitwise XOR
z = x xor y // z is 0b01100110

// bitwise inversion
z = x.inv() // z is 0b01010101

// bitwise left shift
z = x shl 2 // z is 0b1010101000

// bitwise right shift
z = x shr 2 // z is 0b101010
```

Bitwise operators are often used in low-level programming and for optimizing certain algorithms. They are commonly used in conjunction with bit masks to manipulate individual bits of data.

7. The in Operator

The in operator is used in Kotlin to check if a value exists in a collection or not. It is a very useful operator that can save a lot of time and effort while working with collections.

The in operator is used in the following way:

```
if (value in collection) {
    // do something
}
```

In the above code, value is the value that you want to check and collection is the collection that you want to check for the presence of value. If value exists in collection, then the code inside the if block is executed.

The in operator can be used with many types of collections in Kotlin, including arrays, lists, sets, and maps. For example:

```
val list = listOf("apple", "banana", "orange")
if ("apple" in list) {
    println("Found apple in the list")
}
```

In the above code, listOf("apple", "banana", "orange") creates a list of strings. The if condition checks if the string "apple" exists in the list. Since it does, the message "Found apple in the list" is printed to the console.

You can also use the !in operator to check if a value does not exist in a collection. For example:

```
if ("grape" !in list) {
    println("Did not find grape in the list")
}
```

In the above code, the if condition checks if the string "grape" does not exist in the list. Since it does not, the message "Did not find grape in the list" is printed to the console.



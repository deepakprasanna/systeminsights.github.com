---
layout: post
title: First love with Scala - Functions
date: 2012-09-08 12:36
comments: true
categories: scala
author: deepakprasanna
---

Learning Scala has been fun. Personally for me it was like watching Lord of the Rings. Every damn time I watch, it never gets bored and there is
always something new that I would notice. And coming from a dynamic programming background with strong exposure in Ruby and Javascript, static typing
initially was a bit frustrating. But now I have got a better appreciation for the language.

### Functions

The most common way to divide pieces of code and make it manageable is to write functions. Scala offers different flavours when it comes to writing
functions.

``` scala Basic function
def max(x: Int, y: Int): Int = {
  if (x > y) x
  else y
}
```

The above example shows a function named `max` which takes two parameters `x` and `y` of type `Int`. At the end of the argument parenthesis, you will
find `: Int` which means that we are telling the compiler that the function `max` returns a value of type `Int`,commonly known as the *return type*.
The function's body is contained within the curly braces. The equals sign before the function's body states the function defines an expression which
returns a value.  In our case the function's body contains an if statement which evaluates to either `x` or `y` depending on whatever is greater.  So
when the function max is executed, either `x` or `y` is returned.

What if we had to write a function which has no need of returning a value. Like a function for starting a task or just printing some fancy numbers on
screen.  Well in that case we simply omit the equals sign. The return type of a function without equals sign is set to `Unit`.  `Unit` in _Scala_ is
similar to `NULL` in _Java_ and `nil` in _Ruby_, which marks to nothing.

``` scala Basic function(no parameters, no return value)
def sayHi() {
  println("Hi")
}
``` 

The above example shows a function `sayHi` which takes no parameters, returns `Unit` and just prints a "Hi" on the STDOUT while execution.

### REPL 

Let's try out some code in the scala REPL.

``` bash REPL basics
  deepak@cheeseburst:~$ scala 
  scala> 1 + 2
  res0: Int = 3

  scala> val a = 5
  a: Int = 5

  scala> val name = "Deepak"
  name: java.lang.String = Deepak

  scala> println("Prasanna")
  Prasanna
 
  scala> a + 10
  res1: Int = 15

  scala> 
``` 

To start the scala REPL just type `scala` in bash and you will prompted with the scala interpreter. You can pretty much try out most of the scala
code in the REPL except for few. Couple of points to note, after evaluating every expression the interpreter tells the return type of the expression.
In case if the expression returns Unit, the interpreter will remain silent with respect to the return type. Checkout the print statement where there
is no information about the return type is shown. 

``` bash REPL basics
scala> 3
res0: Int = 3

scala> 15
res1: Int = 15
 
scala> res1 + res0
res2: Int = 18

scala> 
```
The resX indentifier holds the returned value through out the session. It can be used at a later point of time.    

### Syntactic sugar

This is my favorite part while writing scala code. Scala gives you some syntactic sweetness when you are writing smaller functions.

``` scala Basic Function(without parenthesis)
//Dah, boring function
def multiply(x:Int, y:Int): Int = {
  x*y
}

//If the body of your function is a single line, you can get rid of the parenthesis.
def multiply(x:Int, y:Int) :Int = 
  x * y

//You can also complete writing the entire function in a single line.
def multiply(x: Int, y:Int) :Int = x * y
```

Let's try out this code in the REPL.

``` scala Function Invocation in REPL
scala> def multiply(x: Int, y:Int) :Int = x * y
multiply: (x: Int, y: Int)Int

scala> multiply(9,10)
res1: Int = 90

scala> 
```

The first step marks the function definition and the second marks the method invocation. When you create a function in the REPL, the interpreter
throws back some information about the defined function. In our case `multiply: (x: Int, y: Int)Int` means you have created a function called multiply
which takes two integers as parameters namely x and y, and it returns a value of type Int. 

In all our previous functions, we have been explicitly conveying the compiler about the return type by adding ` :Int` after the argument
parenthesis.  But Scala can be very smart in figuring out the return type of most of the functions. So if we omit the return type from our function
definition, the compiler will figure out the return type. 

``` scala Basic functions(without return type)
def multiply(x: Int, y:Int) = x * y
//like a boss, huh?
```

There are situations where you have to explicitly specify the return type in the function declaration. I will cover about them in my next post. But
to give you a glimpse, if your function is recursive the compiler expects you to specify the return type. Hence you can write a function in different
ways and yet they all count to same thing. Not just chaining with mere semicolons, its more about giving different choices to choose your level of
expressiveness. This is neat! 

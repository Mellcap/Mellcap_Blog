---
title: 1. Introduction to Java
categories:
- CS 61B
tags:
- CS 61B
- Introduction to Java
---

# Introduction to Java

## Essentials

### Build a simple Java program which prints "Hello World"

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

#### Some key syntactic features

* The program consists of a class declaration, which is declared using the keywords `public class`. In Java, all codes lives inside of classes.
* The code that is run inside of a method called main, which is declared as `public static void main(String[] args)`.
* We use curly braces `{` and `}` to denote the beginning and the end of a section of code.
* Statements must end with semi-colons `;`.

#### Java syntax reference book
[A Java Reference](http://www-inst.eecs.berkeley.edu/~cs61b/fa14/book1/java.pdf)

### Running a Java program

![compilation_figure](/assets/post_imgs/20180710_compilation_figure.svg)

Example:

```bash
$ javac HelloWorld.java  # Compiler
$ java HelloWorld  # Interpreter, do not inclue '.class'
Hello World!
```

### Variables and Loops

```java
public class HelloNumbers {
    public static void main(String[] args) {
        int x = 0;
        while (x < 10) {
            System.out.println(x);
            x = x + 1;
        }
    }
}
```

#### Some interesting features

* Our variable **x** must be declared **before** it is used, and it must be **given a type**!
* Our loop definition is contained inside of curly braces, and the boolean expression that is tested is contained inside of parentheses.


### Static Typing

One of the most important features of Java is that all variables and expressions have a so called `static type`. Java variables can contain values fo that type, and only that type. Furthermore, the type of a variable can never change.

One of the key features of the Java compiler is that it performs a static type check, it rejects the program with wrong type before it even runs. This is in contrast to dynamically typed languages like Python, where users can run into type errors during execution.

To summarize, static typing has the following advantages:

* The compiler ensures that all types are compatible, making it easier for the programmer to debug their code.
* Since the code is guaranteed to be free of type errors, users of your compiled programs will never run into type errors.
* Every variable, parameter, and function has a declared type, making it easier for a programmer to understand and reason about code.

#### Extra Thought

In Java, we can say `System.out.println(5 + "horse");`. But in Python, we can't say `print(5 + "horse")`. Why is that so?

Consider these two Java statements:

`String h = 5 + "horse";`

`Int h = 5 + "horse";`

The first one of these will succeed; the second will give a compiler error. Since Java is strongly typed, if you tell it `h` is a `string`, it can concatenate the elements and give you a string.

Python doesn't constrain the type, and it can't make an assumption for what type you want. Is `s = 5 + "horse"` supposed to be a number? A string? Python doesn't know, so it errors.

### Defining Functions in Java

Since all Java code is part of a class, we must define functions so that they belong to some class. Functions that are part of a class are commonly called "methods", we will use the terms interchageably throughtout the course.

```java
public class LargerDemo {
    public static int larger(int x, int y) {
        if (x > y) {
            return x;
        }
        return y;
    }

    public static void main(String[] args) {
        System.out.println(larger(-5, 8));
    }
}
```
The new piece of syntax here is that we decleared our method using the keywords `public static`, which is a very rough analog of Python's `def` keyword.

### Code Style, Comments, Javadoc

Code can be beautiful in many ways. In this course, we'll work hard to try to keep our code readable. Some of the most important features of good coding style are:

* Descriptive naming (variables, functions, classes), e.g. variables or functions with names like `year` or `getUserName` instead of `x` or `f`.
* Avoidance of repetitive code: You should almost never have two significant blocks of code that are nearly identical except for a few changes.
* Comments where appropriate. Line comments in Java use the `//` delimiter. Block (a.k.a. multi-line comments) comments use `/*` and `*/`.

The golden rule is this: Write your code so that it is easy for a stranger to understand.

Often, we are willing to incur slight performance penalties, just so that our code is simpler to [grok](https://en.wikipedia.org/wiki/Grok).

#### Comments

Almost all of your classes should be described in a comment using the so-called [Javadoc](https://en.wikipedia.org/wiki/Javadoc) format.

The widely used [javadoc tool](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html) can be used to generate HTML descriptions of your code.

## Objects

### Static vs. Non-Static Methods

#### Static Methods

All code in Java must be part of a class, most code is written inside of methods. Let's consider an example:

```java
public class Dog {
    public static void makeNoise() {
        System.out.println("Bark!");
    }
}
```

If we try running the `Dog` class, we'll simply get an error. 

To actually run this class, we'd either need to add a main method to the `Dog` class, or we could create a separate `DogLauncher` class that runs methods from the `Dog` class.

```java
public class DogLauncher {
    public static void main(String[] args) {
         Dog.makeNoise();
    }
}
```

A class that uses another class is sometimes called a **client** of that class, i.e. `DogLauncher` is a client of `Dog`.

#### Instance Variables and Object Instantiation (Non-Static Methods)

Not all dogs are alike. Often, we write programs to mimic features of the universe we inhabit.

```java
public class TinyDog {
    public static void makeNoise() {
        System.out.println("yip yip yip yip");
    }
}

public class MalamuteDog {
    public static void makeNoise() {
        System.out.println("arooooooooooooooo!");
    }
}
```

Classes can be instantiated, and instances can hold data. This leads to a more nature approach, where we create instances of the `Dog` class and make the behavior of the `Dog` methods contingent upon the properties of the specific `Dog`.

```java
public class Dog {

    public int weightInPounds;

    public void makeNoise() {
        if (weightInPounds < 10) {
            System.out.println("Yiiiip!");
        } else if (weightInPounds < 30) {
            System.out.println("Barrrrk!");
        } else {
            System.out.println("Wooooof!");
        }
    }
}
```

An example of using such a Dog;

```java
public class DogLauncher {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.weightInPounds = 50;
        d.makeNoise();
    }
}
```

Some key observations and terminology:


* An `Object` in Java is an **instance** of any class.
* The `Dog` class has its own variables, also known as **instance variables** or **non-static variables**. These must be declared inside the class, unlike languages like Python, where new variables can be added at runtime.
* The method that we created in the `Dog` class did not have the `static` keyword. We call such methods **instance methods** or **non-static methods**.
	1. Idea: If the method is going to be invoked by an instance of the class, then it should be non-static. Roughly speaking: If the method need to use **my instance variables**, the method must be non-static.
* To call the `makeNoise` method, we had first **instantiate** a `Dog` using the `New` keyword, and then make a specific `Dog` bark. In other words, we called `d.makeNoise()` instead of `Dog.makeNoise()`.
* Variables and methods of a class are also called **members** of a class, which can accessed using dot notation.

#### Constructors in Java

We usually construct objects oriented languages using a constructor `Dog d = new Dog(50);`.

The instantiation is parameterized, to enable such syntax, we need only add a "constructor" to our Dog class, as shown below:

```java
    /* Constructor of the Dog class */
    public Dog(int w) {
        weightInPounds = w;
    }
```

The constructor with signature `public Dog(int w)` will be invoked anytime that we try to create a `Dog` using the `new` keyword and a single integer parameter. It is very similar to the `__init__` method in Python.

#### Array Instantiation, Arrays of Objects

We can create arrays of instantiated objects in Java, e.g.

```java
public DogArrayDemo() {
    public static void main(String[] args) {
        // Create an array of two dogs.        
        Dog[] dogs = new Dog[2];
        dogs[0] = new Dog(20);
        dogs[1] = new Dog(50);
        
        // Barrrrk! will result, since dogs[0] has weight 20.        
        dogs[0].makeNoise();
    }
}
```

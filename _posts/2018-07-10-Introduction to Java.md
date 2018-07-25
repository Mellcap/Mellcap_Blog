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
* COmments where appropriate. Line comments in Java use the `//` delimiter. Block (a.k.a. multi-line comments) comments use `/*` and `*/`.

The golden rule is this: Write your code so that it is easy for a stranger to understand.

Often, we are willing to incur slight performance penalties, just so that our code is simpler to [grok](https://en.wikipedia.org/wiki/Grok).

#### Comments

Almost all of your classes should be described in a comment using the so-called [Javadoc](https://en.wikipedia.org/wiki/Javadoc) format.

The widely used [javadoc tool](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html) can be used to generate HTML descriptions of your code.


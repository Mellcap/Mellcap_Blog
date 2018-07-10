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
		System.out.println("Hello world");
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
$ javac HelloWorld.java  #Compiler
$ java HelloWorld  #Interpreter, do not inclue '.class'
Hello World!
```



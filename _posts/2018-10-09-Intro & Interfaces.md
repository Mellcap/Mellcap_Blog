---
title: 4. Inheritance & Implements
categories:
- CS 61B
tags:
- CS 61B
- Inheritance & Implements
---

# Intro & Interfaces

### Hypernyms, Hyponyms, and Interface Inheritance

##### The Problem

Write a class `WordUtils` that includes a function which calculates the longest String in a SLList.

```java
public static String longest(SLList<String> list) {
    int maxDex = 0;
    for (int i = 0; i < list.size(); i += 1) {
        String longestString = list.get(maxDex);
        String thisString = list.get(i);
        if (thisString.length() > longestString.length()) {
            maxDex = i;
        }
    }
    return list.get(maxDex);
}
```

If we need to make this method work for AList, we need to write an exactly same method:

```java
public static String longest(AList<String> list){...}
```

It is ugly, repetitive and hard for us to maintain.

<!-- more -->

###### Inheritance

**Hypernym**: Dog is called a *hypernym* of poodle, husky, etc.
**Hyponym**: Husky is *hyponym* of dog.

These words form a hierarchy of "is-a" relationship:
* a husky "is-a" dog
* a dog "is-a" canine
* a canine "is-a" carnivore
* a carnivore "is-an" animal

The same hirerarchy goes for SLList and AList.
1. Define a type for general list hypernym, e.g.List61B
2. Specify that SLList and AList are hyponyms of that type.

Then, SLList class is **subclass** of the List61B class, and List61B class is a **superclass** of the SLList class.

🌟 The new List61B is what Java calls **interface**, specifies **what a list must be able to do, but doesn't provide any implementation for those behaviors.**

```java
public interface List61B<Item> {
    public void addFirst(Item x);
    public void add Last(Item y);
    public Item getFirst();
    public Item getLast();
    public Item removeLast();
    public Item get(int i);
    public void insert(Item x, int position);
    public int size();
}
```

Now, we need to specify that AList and SLList are hyponyms of the List61B class, by add a relationship-defining word: **implements**

```java
public class AList<Item> implements List61B<Item>{...}
```

Now we can edit out `longest` method in `WordUtils` to take in a List61B, because AList and SLList share an "is-a" relationship.

##### Overriding

When implementing the required functions in the subclass, it's useful to include the `@Override` tag right on top of the method signature. It will help you avoid typo and other mistakes.

```java
@Override
public void addFirst(Item x) {
    insert(x, 0);
}
```

##### 🌟 GROE

`List61B<String> someList = new SLList<String>();`

SLList shares "is-a" relationship with List61B, which means an SLList should be able to fit into a List61B box.

##### Default Methods

List61B can implements the default method use `default` keyword.

```java
default public void print() {
    for (int i = 0; i < size(); i += 1) {
        System.out.print(get(i) + " ");
    }
    System.out.println();
}
```

But this is inefficient for SLList, we need to override it in `SLList.java`.

```java
@Override
public void print() {
	System.out.print("Here is the SLList"); // to declear that it runs in SLList.java
    for (Node p = sentinel.next; p != null; p = p.next) {
        System.out.print(p.item + " ");
    }
}
```

### Dynamic Method

Variable in java have a type.

```java
List61B<String> lst = new SLList<String>();
```

In the above declaration and instantiation, `lst` is of type "List61B". This is called the "static type".

But, because the object itself was instantiated using the SLList constructor, We call this its "dynamic type".

When Java runs a method that is overriden, it searches for the appropriate method signature in it's **dynamic type** and runs it. So it will print "Here is the SLList" when runs `print()` function.

**IMPORTANT**: This does not work for overloaded methods!

##### Overloaded Methods

```java
public static void peek(List61B<String> list) {
    System.out.println(list.getLast());
}
public static void peek(SLList<String> list) {
    System.out.println(list.getFirst());
}
```

When you run this code

```java
SLList<String> SP = new SLList<String>();
List61B<String> LP = SP;
SP.addLast("elk");
SP.addLast("are");
SP.addLast("cool");
peek(SP);
peek(LP);
```

The first call to peek() will use the second peek method that takes in an SLList. The second call to peek() will use the first peek method which takes in a List61B.

This is because the only distinction between two overloaded methods is the types of the parameters, when Java checks to see which method to call, it checks the **static type** and calls the method with the parameter of the same type.

##### Note

🌟 When you are creating these hierarchies, remember that the relationship between a subclass and a superclass should be an **"is-a"** relationship. You should not be defining them using a "has-a" relationship.

Cat should only implement Animal, Cat **is an** Animal. Cat **has-a** Claw, but Cat definitely should not be implementing Claw.


# Extends, Casting & Higher Order Functions

### Extends

We can use `extends` to define a hierarchical relationship between classes.

Define a `RotatingSLList` to extend from `SLList`, and a `rotateRight` method which rotates every element one spot to the right.

```java
public class RotatingSLList<Item> extends SLList<Item> {
	public void rotateRight() {
	    Item x = removeLast();
	    addFirst(x);
	}
}
```

Noticed that we were able to use methods defined outside of RotatingSLList. By using the `extends` keyword, subclass inherit all **members** of the parent class, include:

* All instance and static variables
* All methods
* All nested classes

Except **constructors** and **private members**.

### Super

Create a new class `VengefulSLList` that collects the removed element.

In an effort to *reuse* code, we can **override** the `removeLast` methods, and call the `removeLast` method defined in the parent class uding the `super` keyword.

```java
public class VengefulSLList<Item> extends SLList<Item> {
    SLList<Item> deletedItems;

    public VengefulSLList() {
	    super(); //Java will automatically make a call to the superclass's **no-argument** constructor for us.
        deletedItems = new SLList<Item>();
    }

    @Override
    public Item removeLast() {
        Item x = super.removeLast();
        deletedItems.addLast(x);
        return x;
    }

    /** Prints deleted items. */
    public void printLostItems() {
        deletedItems.print();
    }
}
```

##### The Object Class

Every class in Java is descendant of the Object class.

As seen in [Documentation for the Obejct class](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html), the Obejct class provides operations that every Object should be able to do.

### Encapsulation

Encapsulation is one of the fundamental principles of object oriented programming, and is one of the approaches that we take as programmers to resist our biggest enemy: *complexity*.

**Hiding information** that others don't need is another fundamental approach when managing a large system.

##### How Inheritance Breaks Encapsulation

E.g. We implement `bark` and `barkMany` in a Dog class:

```java
public void bark() {
    barkMany(1);
}

public void barkMany(int N) {
    for (int i = 0; i < N; i += 1) {
        System.out.println("bark");
    }
}
```

And we define VerboseDog class and override `barkMany` method

```java
@Override
public void barkMany(int N) {
    System.out.println("As a dog, I say: ");
    for (int i = 0; i < N; i += 1) {
        bark();
    }
}
```
So, it will throw an error when we called `vd.barkMany(3);`. An infinite loop.

### Type Checking and Casting

Java complier checks the type at compile-time, checks their **static-type**, so it will throw an error below:

```java
VengefulSLList<Integer> vsl = new SLList<Integer>();
```

But sometimes we need the **dynamic-type**:

```java
Poodle frank = new Poodle("Frank", 5);
Poodle frankJr = new Poodle("Frank Jr.", 15);

Dog largerDog = maxDog(frank, frankJr);
Poodle largerPoodle = maxDog(frank, frankJr); //does not compile! Right hand side has compile-time type Dog
```

##### Casting

Java has a special syntax where you can tell the compiler that a specific expression has a specific compile-time type. This is called **casting**.

Since we know `frank` and `frankJr` are both Poodles, we can cast:

```java
Poodle largerPoodle = (Poodle) maxDog(frank, frankJr); // compiles! Right hand side has compile-time type Poodle after casting
```

### Higher Order Functions

A higher order function is a function that treats other functions as data. 

```python
def tenX(x):
    return 10*x

def do_twice(f, x):
    return f(f(x))
```

In Java 7 and ealier, memory boxes (variables) could not contain pointers to functions, so we need interface inheritance to implient this.

We need a class `IntUnaryFunction` to represent a concrete function:

```java
// IntUnaryFunction.java
public interface IntUnaryFunction {
    int apply(int x);
}

// TenX.java
public class TenX implements IntUnaryFunction {
    /* Returns ten times the argument. */
    public int apply(int x) {
        return 10 * x;
    }
}

// HOF_demo.java
public static int do_twice(IntUnaryFunction f, int x) {
    return f.apply(f.apply(x));
}

System.out.println(do_twice(new TenX(), 2));
```


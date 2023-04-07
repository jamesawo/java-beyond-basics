# Java Beyond Basics

Java Beyond Basics is a repository that provides a collection of code samples and examples for advanced Java concepts. This repository covers various topics such as Collections API, Streams, Java IO, Date Time API, and more.

### Getting Started

To get started with JavaBeyondBasics, you will need to clone the repository to your local machine using the following command:

### Table of Contents

---

-   Introduction

    -   [What is Java Beyond Basics?](#q-what-is-java-beyond-basics)
    -   [Why Learn Advanced Java?](#q-why-learn-advanced-java)

-   Advanced Language Features

    -   [Enumerations](#enumerations)
    -   [Annotations](#annotations)
    -   [Lambdas and Functional Interfaces](#lambdas-and-functional-interfaces)
    -   [Default and Static Methods in Interfaces]()
    -   [Type Inference with the var Keyword]()

-   Concurrency and Multithreading

    -   [Threads and Runnable]()
    -   [Synchronization]()
    -   [Locks and Conditions]()
    -   [Executors and Thread Pools]()
    -   [CompletableFuture]()

-   Collections Framework
    -   [Iterable and Iterator]()
    -   [List and ArrayList]()
    -   [Set and HashSet]()
    -   [Map and HashMap]()
    -   [Queue and Deque]()
    -   [Comparators and Ordering]()
    -   [Collections Utility Class]()
-   Input and Output
    -   [Byte Streams and Character Streams]()
    -   [File and Directory Operations]()
    -   [Object Serialization]()
    -   [NIO and Channels]()
    -   [Serialization with Protocol Buffers]()
-   Database Programming
    -   [JDBC API]()
    -   [Connection Pooling]()
    -   [ORM with Hibernate]()
-   Networking
    -   [TCP and UDP Sockets]()
    -   [HTTP and HTTPS Clients]()
    -   [WebSockets]()
-   Security
    -   [Cryptography and Encryption]()
    -   [Hashing and Salting]()
    -   [Digital Signatures and Certificates]()
    -   [OAuth and OpenID Connect]()

### Introduction

#### Q. What is Java Beyond Basics?

---

Java Beyond Basics is a repository that provides a collection of code samples, popular questions and answers to advanced concepts and topics in Java.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Why Learn Advanced Java?

---

Advanced Java concepts can improve your coding skills and make you a better Java programmer and can help you write high-performance Java applications.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Advanced Language Features

#### Enumerations

#### Q. Can Enum constants can be declared as static and final?

---

Yes. Enum constants are public static and final and are accessible directly using enum name.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can a constructor be invoked using an Enum

---

Yes we can use the constructor with the name of Enum.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can we extend an Enum to add elements?

---

No, we cannot extend Enum further in the Code. It is defined only with keyword Enum and filled with elements but these elements cannot be added further in the program using some alternative method.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can we create object of Enum?

---

No, it is not possible to create an object from an Enum.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What does ordinal() method do in Enum?

---

Ordinal method returns the order in which Enum instance are declared inside Enum. For example in a DayOfWeek Enum, you can declare days in order they come e.g.

```java
public enum WeekDay{
  MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
}
```

Ordinal arranges or assigns numbers to each element. If we call WeekDay.Thursday.ordinal() it will return 3.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Annotations

#### Q. What Are Annotations? What Are Their Typical Use Cases?

---

Annotations are metadata bound to elements of the source code of a program. Their typical uses cases are:

-   Information for the compiler – with annotations, the compiler can detect errors or suppress warnings
-   Compile-time and deployment-time processing – software tools can process annotations and generate code, configuration files, etc.
-   Runtime processing – annotations can be examined at runtime to customize the behavior of a program

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. How Can You Create an Annotation?

---

Annotations are a form of an interface where the keyword interface is preceded by @, and whose body contains annotation type element declarations that look very similar to methods

```java
public @interface CustomAnnotation {
    String value();

    int[] types();
}
```

After the annotation is defined, yon can start using it in through your code:

```java
@CustomAnnotation(value = "an element", types = 1)
public class Element {
    @CustomAnnotation(value = "an attribute", types = { 1, 2 })
    public Element nextElement;
}
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What Are Meta-Annotations?

---

Are annotations that apply to other annotations.

All annotations that aren't marked with @Target, or are marked with it but include ANNOTATION_TYPE constant are also meta-annotations:

```java
@Target(ElementType.ANNOTATION_TYPE)
public @interface CustomAnnotation {
    // ...
}
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What Are Repeating Annotations?

---

These are annotations that can be applied more than once to the same element declaration.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Is It Possible to Extend Annotations?

---

No. Annotations always extend java.lang.annotation.Annotation, as stated in the Java Language Specification.

If we try to use the extends clause in an annotation declaration, we'll get a compilation error:

```java
public @interface AnAnnotation extends OtherAnnotation {
    // Compilation error
}
```

 <p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Lambdas and Functional Interfaces

#### Q. What is lambda expression of Java 8?

---

As it's name suggests its an expression which allows you to write more succinct code in Java 8. For example (a, b) -> a + b is a lambda expression (look for that arrow ->) which is equal to following code:

```java
public int value(int a, int b){
   return a + b;
}
```

It's also called anonymous function because you are essentially writing the code you write in function but without name.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can you pass lambda expression to a method? When?

---

Yes, you can pass a lambda expression to a method provided it is expecting a functional interface. For example, if a method is accepting a Runnable, Comparable or Comparator then you can pass a lambda expression to it because all these are functional interface in Java 8.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is functional interface in Java 8?

---

A functional interface in Java 8 is an interface with single abstract method. For example, Comparator which has just one abstract method called compare() or Runnable which has just one abstract method called run(). There are many more general purpose functional interface are introduced in JDK on java.util.function package. They are also annotated with @FunctionalInterface but that's optional.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### What is map operation in Java 8?

---

The map operation is used to transform one type to another type but applying a function. For example, if you have list of integer number but you want a List of String then you can use map operation to convert that list of integer into list of String by applying toString() function on each element. It came from functional programming paradigm but now Java 8 also has this.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

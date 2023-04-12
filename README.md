# Java Beyond Basics

Java Beyond Basics is a repository that provides a collection of code samples and examples for advanced Java concepts. This repository covers various topics such as Collections API, Streams, Java IO, Date Time API, and more.

### Getting Started

To get started with JavaBeyondBasics, you can read through the topic in table of content section or click on it to jump to a specific topic, there you can read through the questions and answers for better clarity.

You can also go to a directory like `0.DataStructuresInJava` to see some sample code and example on that specific topic in Java.

### Table of Contents

---

-   Introduction

    -   [What is Java Beyond Basics?](#q-what-is-java-beyond-basics)
    -   [Why Learn Advanced Java?](#q-why-learn-advanced-java)

-   Advanced Language Features

    -   [Enumerations](#enumerations)
    -   [Annotations](#annotations)
    -   [Lambdas and Functional Interfaces](#lambdas-and-functional-interfaces)
    -   [Default and Static Methods in Interfaces](#default-and-static-methods-in-interfaces)
    -   [Type Inference with the var Keyword](#type-inference-with-the-var-keyword)

-   Concurrency and Multithreading

    -   [Threads and Runnable](#threads-and-runnable)
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

#### Q. What is map operation in Java 8?

---

The map operation is used to transform one type to another type but applying a function. For example, if you have list of integer number but you want a List of String then you can use map operation to convert that list of integer into list of String by applying toString() function on each element. It came from functional programming paradigm but now Java 8 also has this.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Default and Static Methods in Interfaces

#### Q. Can we make the Default method static in Java?

---

No, You cannot make the default method static in Java. If you declare static method and default together, you will get a compilation error.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can an interface contain more than one Default method?

---

Yes, any Java interface can contain more than one default method.
But, it is not common to find reasons for adding multiple default methods on an interface.

```java
interface Vehicle{
    default void first(){
        System.out.println("first default method");
    }

    default void second(){
        System.out.println("Second default method");
    }

    default void third(){
        System.out.println("Third default method");
    }
}
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can default method override equals(), hashCode() or toString() from Object class?

---

No, the default method cannot override any method from java.lang.Object, trying to override toString(), equals() or hashCode() as the default method in an interface on Java 8, will throw a compile-time error.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can we declare Default methods inside a class in Java?

---

No, you can't, but just think about why do you need default methods for Java classes, unlike implementation of an interface, there is no requirement for all subclasses to implement a new method added inside a Java class. A class can evolve without requiring a change in its subclasses.

Of course, when you add a new abstract method inside an abstract class, then it will break your subclasses, but you don't need a default method to save there, a normal method will do the job.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Type Inference with the var Keyword

#### Q. Why have var in Java?

---

Local variables are the workhorse of Java. They allow methods to compute significant results by cheaply storing intermediate values. Unlike a field, a local variable is declared, initialized, and used in the same block. The name and initializer of a local variable are often more important for a reader’s understanding than the type. Commonly, the name and initializer carry just as much information as the type:

```java
Person person = new Person();
```

The role of var in a local variable declaration is to stand in for the type, so that the name and initializer stand out:

```java
var person = new Person();
```

The compiler infers the type of the local variable from the initializer. Using var can make code more concise without sacrificing readability, and in some cases it can improve readability by removing redundancy.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Does this make Java dynamically typed? Is this like var in JavaScript?

---

No and no. Java is still a statically typed language, and the addition of var doesn’t change this. var can be used in a local variable declaration instead of the variable’s type. With var, the Java compiler infers the type of the variable at compile time, using type information obtained from the variable’s initializer.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Is a var variable final?

---

No. Local variables declared with var are non-final by default. However, the final modifier can be added to var declarations:

```java
final var person = new Person();
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Where can var be used?

---

var can be used for declaring local variables, including index variables of for-loops and resource variables of the try-with-resources statement.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Why is an initializer required on the right-hand side of var?

---

The type of the variable is inferred from the type of the initializer. This means, of course, that var can only be used when there is an initializer.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Why can’t you use var with null?

---

Consider this declaration (which is illegal):

```java
var person = null; // ERROR
```

The null literal denotes a value of a special null type that is the subtype of all reference types in Java. The only value of the null type is null itself, therefore, the only value that could ever be assigned to a variable of the null type is null. This isn’t very useful.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can you use var with a diamond on the right-hand side?

---

Yes, it works, but it’s probably not what you want. Consider:

```java
var list = new ArrayList<>();
```

This will infer the type of list to be ArrayList<Object>. In general, it’s preferable to use an explicit type on the left with diamond on the right, or use var on the left with an explicit type on the right.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Concurrency and Multithreading

#### Threads and Runnable

#### Q. What is the thread?

---

A thread is a lightweight subprocess. It is a separate path of execution because each thread runs in a different stack frame. A process may contain multiple threads. Threads share the process resources, but still, they execute independently.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is multithreading?

---

Multithreading is a process of executing multiple threads simultaneously. Multithreading is used to obtain the multitasking. It consumes less memory and gives the fast and efficient performance. Its main advantages are:

-   Threads share the same address space.
-   The thread is lightweight.
-   The cost of communication between the processes is low.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Differentiate between process and thread?

---

These are some differences between the process and thread.

-   A Program in the execution is called the process whereas; A thread is a subset of the process
-   Processes are independent whereas threads are the subset of process.
-   Process have different address space in memory, while threads contain a shared address space.
-   Context switching is faster between the threads as compared to processes.
-   Inter-process communication is slower and expensive than inter-thread communication.
-   Any change in Parent process doesn't affect the child process whereas changes in parent thread can affect the child thread.
    <p>
        <small>
            <a href="#getting-started"> back to top</a>
        </small>
    </p>

#### Q. What do you understand by inter-thread communication?

---

-   The process of communication between synchronized threads is termed as inter-thread communication.
-   Inter-thread communication is used to avoid thread polling in Java.
-   The thread is paused running in its critical section, and another thread is allowed to enter (or lock) in the same critical section to be executed.
-   It can be obtained by wait(), notify(), and notifyAll() methods.

<p>
    <small>
    <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is the purpose of wait() method in Java?

---

The wait() method is provided by the Object class in Java. This method is used for inter-thread communication in Java. The java.lang.Object.wait() is used to pause the current thread, and wait until another thread invokes the notify() method or the notifyAll() method for this object. In other words, this method behaves exactly as if it simply performs the call wait(0).

<p>
<small>
<a href="#getting-started"> back to top</a>
</small>
</p>

#### Q. Why must wait() method be called from the synchronized block?

---

We must call the wait method otherwise it will throw java.lang.IllegalMonitorStateException exception. Moreover, we need wait() method for inter-thread communication with notify() and notifyAll(). Therefore It must be present in the synchronized block for the proper and correct communication.

<p>
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What are the advantages of multithreading?

---

Multithreading programming has the following advantages:

-   Multithreading allows an application/program to be always reactive for input, even already running with some background tasks
-   Multithreading allows the faster execution of tasks, as threads execute independently.
-   Multithreading provides better utilization of cache memory as threads share the common memory resources.
-   Multithreading reduces the number of the required server as one server can execute multiple threads at a time.

<p>
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What are the states in the lifecycle of a Thread?

A thread can have one of the following states during its lifetime:

-   New: In this state, a Thread class object is created using a new operator, but the thread is not alive. Thread doesn't start until we call the start() method.
-   Runnable: In this state, the thread is ready to run after calling the start() method. However, the thread is not yet selected by the thread scheduler.
-   Running: In this state, the thread scheduler picks the thread from the ready state, and the thread is running.
-   Waiting/Blocked: In this state, a thread is not running but still alive, or it is waiting for the other thread to finish.
-   Dead/Terminated: A thread is in terminated or dead state when the run() method exits.

<p>
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is the difference between preemptive scheduling and time slicing?

---

-   Under preemptive scheduling, the highest priority task executes until it enters the waiting or dead states or a higher priority task comes into existence.

-   Under time slicing, a task executes for a predefined slice of time and then reenters the pool of ready tasks. The scheduler then determines which task should execute next, based on priority and other factors.

<p>
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is context switching?

---

In Context switching the state of the process (or thread) is stored so that it can be restored and execution can be resumed from the same point later. Context switching enables the multiple processes to share the same CPU.

<p>
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Describe the purpose and working of sleep() method.

---

The sleep() method in java is used to block a thread for a particular time, which means it pause the execution of a thread for a specific time.

The SleepMessages example below use sleep to print messages at four-second intervals:

```java
public class SleepMessages {
    public static void main(String args[]) throws InterruptedException {

        for (int i = 0; i < 5; i++) {
            //Pause for 4 seconds
            Thread.sleep(4000);
            //Print a message
            System.out.println("Greetings no:  "+ [i]);
        }
    }
}
```

<p>
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

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
    -   [Synchronization](#synchronization)
    -   [Locks and Conditions](#locks-and-condition)
    -   [Executors and Thread Pools](#executors-and-thread-pools)
    -   [CompletableFuture](#completable-future)

-   Collections Framework
    -   [Iterable and Iterator](#iterable-and-iterator)
    -   [List and ArrayList](#list-and-arraylist)
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
<p align="right">
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

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is the purpose of wait() method in Java?

---

The wait() method is provided by the Object class in Java. This method is used for inter-thread communication in Java. The java.lang.Object.wait() is used to pause the current thread, and wait until another thread invokes the notify() method or the notifyAll() method for this object. In other words, this method behaves exactly as if it simply performs the call wait(0).

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>
#### Q. Why must wait() method be called from the synchronized block?

---

We must call the wait method otherwise it will throw java.lang.IllegalMonitorStateException exception. Moreover, we need wait() method for inter-thread communication with notify() and notifyAll(). Therefore It must be present in the synchronized block for the proper and correct communication.

<p align="right">
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

<p align="right">
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

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is the difference between preemptive scheduling and time slicing?

---

-   Under preemptive scheduling, the highest priority task executes until it enters the waiting or dead states or a higher priority task comes into existence.

-   Under time slicing, a task executes for a predefined slice of time and then reenters the pool of ready tasks. The scheduler then determines which task should execute next, based on priority and other factors.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is context switching?

---

In Context switching the state of the process (or thread) is stored so that it can be restored and execution can be resumed from the same point later. Context switching enables the multiple processes to share the same CPU.

<p align="right">
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

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Synchronization

#### Q. What is synchronization of threads?

---

Since Threads run in parallel, a new problem arises. What if thread1 modifies data which is being accessed by thread2? How do we ensure that different threads don’t leave the system in an inconsistent state? This problem is usually called synchronization problem.

Let’s first look at an example where this problem can occur. Consider the code in the setAndGetSum method.

```java
int setCell(int a1, int a2, int a3) {
    cell1 = a1;
    sleepForSomeTime();
    cell2 = a2;
    sleepForSomeTime();
    cell3 = a3;
    sleepForSomeTime();
    return cell1 + cell2 + cell3;
}
```

If following method is running in two different threads, funny things can happen. After setting the value to each cell, there is a call for the Thread to sleep for some time. The value of cell1 can be updated by another thread and this will lead to unexpected results.

The way you can prevent multiple threads from executing the same method is by using the **synchronized** keyword on the method. If a method is marked synchronized, a different thread gets access to the method only when there is no other thread currently executing the method.

Let’s mark the method as synchronized:

```java
synchronized int setCell(int a1, int a2, int a3) {
    cell1 = a1;
    sleepForSomeTime();
    cell2 = a2;
    sleepForSomeTime();
    cell3 = a3;
    sleepForSomeTime();
    return cell1 + cell2 + cell3;
}
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can you give an example of a synchronized block?

---

All code which goes into the block is synchronized on the current object.

```java
 void synchronizedExample2() {
        synchronized (this){
        //All code goes here..
        }
    }
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can a static method be synchronized?

---

Yes. Static methods and block are synchronized on the class. Instance methods and blocks are synchronized on the instance of the class i.e. an object of the class. Static synchronized methods and instance synchronized methods don’t affect each other. This is because they are synchronized on two different things. Consider the example below.

```java
synchronized static int getCount(){
        return count;
    }

    static int getCount2(){
        synchronized (SynchronizedSyntaxExample.class) {
            return count;
        }
    }
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is the use of join method in threads?

---

Join method is an instance method on the Thread class. Let's see a small example to understand what join method does. Let’s consider the thread's declared below: thread2, thread3, thread4

```java
ThreadExample thread2 = new ThreadExample();
ThreadExample thread3 = new ThreadExample();
ThreadExample thread4 = new ThreadExample();
```

Let’s say we would want to run thread2 and thread3 in parallel but thread4 can only run when thread3 is finished. This can be achieved using join method.Look at the example code below: thread3.join() method call forces the execution of main method to stop until thread3 completes execution. After that, thread4.start() method is invoked, putting thread4 into a Runnable State.

```java
thread3.start();
thread2.start();
thread3.join();//wait for thread 3 to complete
System.out.println("Thread3 is completed.");
thread4.start();
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Locks and Condition

#### Q. What is Condition Interface

---

A java.util.concurrent.locks.Condition interface provides a thread ability to suspend its execution, until the given condition is true. A Condition object is necessarily bound to a Lock and to be obtained using the newCondition() method.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Differences Between Lock and Synchronized Block

---

There are a few differences between the use of synchronized block and using Lock APIs:

-   A synchronizedblock is fully contained within a method. We can have Lock APIs lock() and unlock() operation in separate methods.
-   A synchronized block doesn't support the fairness. Any thread can acquire the lock once released, and no preference can be specified. We can achieve fairness within the Lock APIs by specifying the fairness property. - It makes sure that the longest waiting thread is given access to the lock.
-   A thread gets blocked if it can't get an access to the synchronized block. The Lock API provides tryLock() method. The thread acquires lock only if it's available and not held by any other thread. This reduces blocking time of thread waiting for the lock.
-   A thread that is in “waiting” state to acquire the access to synchronized block can't be interrupted. The Lock API provides a method lockInterruptibly() that can be used to interrupt the thread when it's waiting for the lock.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can a thread enter a synchronized block without acquiring a lock-in Java?

---

No, it's not possible. A thread must acquire the lock required by a synchronized block before entering. The synchronized keyword acquires the lock when a Thread enters and releases the lock Thread leaves the block.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What happens to the thread after calling the wait() method? Does it return lock?

---

Well, when a thread sees that condition to proceed further is not ok, it decides to wait by calling the wait() method, but it does release the lock. Yes, this is really important, a thread is not proceeding further but the lock is released so that other threads waiting for the lock can proceed.

This is also the key difference between the sleep() and the wait() method, which is used to pause a thread

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Executors and Thread Pools

#### Q. What Do You Understand By Executor Framework In Java?

---

Executor Framework in java has been introduced since JDK 5. Executor Framework handles creation of thread, creating the thread pool and checking health while running and also terminates if needed.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What Is The Role Of Executorservice In Java?

---

ExecutorService provides different methods to start and terminate thread. There are two methods execute() and submit() in ExecutorService. Execute() method is used for threads which is Runnable and submit() method is used for Callable threads.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What Is The Role Of Futuretask And Future In Java?

---

FutureTask is a cancellable asynchronous computation in java. It can cancel the task which is running. Once the FutureTask will be cancelled, it cannot be restarted. Future is result of asynchronous computation. Future checks if task is complete and if completed it gets the output.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What Is Difference Between Shutdownnow() And Shutdown() In Executor Framework In Java?

---

shutdown() and shutdownNow() methods belongs to ExecutorService. shutdown() method tries to stop the threads and do not accept new task to execute but it completes the execution which has been submitted. shutdownNow() methods also tries to stop the running threads and will not execute any task which has been submitted but not started.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What Are The Different Policy In Executor Framework?

---

There are different policy within ThreadPoolExecutor in java.

-   **ThreadPoolExecutor.AbortPolicy** : AbortPolicy is a handler for rejected task. It handles those task which has been rejected.

-   **ThreadPoolExecutor.CallerRunsPolicy **: This also handles the rejected task and runs the rejected task directly.

-   **ThreadPoolExecutor.DiscardOldestPolicy** : This handles those rejected task that is oldest and unhandled. It discards those that oldest task.

-   **ThreadPoolExecutor.DiscardPolicy** : This is the handler for those rejected task that are rejected silently.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Completable Future

#### Q. What is CompletableFuture?

---

CompletableFuture is a class that is part of the Java 8 concurrency API. It allows you to create a task that can be completed in the future, and provides methods for composing and combining multiple CompletableFutures into a single task.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can you explain what a completion stage is?

---

A completion stage is a stage of a computation that can be completed by a Future. The completion stage can be used to trigger an action upon completion of the Future, or to compose multiple Futures together.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. How do you create a completable future in Java?

---

You can create a completable future in Java by using the CompletableFuture.completedFuture() method. This method takes a value as an input and returns a new CompletableFuture that is already completed with that value.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Does creating an instance of CompletableFuture automatically start its execution? If not, then how can it be started?

---

No, creating an instance of CompletableFuture does not automatically start its execution. In order to start its execution, you must call the .run() or .start() method on the CompletableFuture instance.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Is there any limit to the number of asynchronous tasks that can run concurrently using CompletableFuture?

---

There is no limit to the number of asynchronous tasks that can run concurrently using CompletableFuture.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Can you explain the difference between blocking and non-blocking calls? Which type of call do you prefer to use? Why?

---

Blocking calls are those where the thread making the call will wait until the call returns before continuing. Non-blocking calls, on the other hand, allow the thread to continue executing while the call is being processed. I prefer to use non-blocking calls whenever possible, as they can help to improve performance by allowing the thread to continue working on other tasks while waiting for the results of the call.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

### Collections Framework

#### Iterable and Iterator

#### Q. What are Iterator or cursor in Java?

---

An iterator in Java is a special type of object that provides sequential (one by one) access to the elements of a collection object. It is introduced in Java 1.2 Collections Framework.

We use iterator in the Collections Framework to retrieve elements sequentially (one by one). It is called a universal Iterator or cursor.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What are the types of Iterators in Java?

---

There are four types of iterators or cursors available in Java. They are as:

-   Enumeration
-   Iterator
-   ListIterator
-   Spilterator

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is Iterable Interface in Java?

---

The Collection interface extends Iterable interface that is present at the top of the collection hierarchy.
The iterable interface is present in java.lang.Iterable package .

It provides a uniform way to retrieve the elements one by one from a collection object.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. The iterable interface provides which method in Java?

---

The iterable interface provides just one method named iterator() which returns an instance of Iterator and provides access one by one to the elements in the collection object.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. How to create Iterator object in Java?

We create Iterator object by calling iterator() method which is present in the iterable interface.
The general syntax for creating Iterator object is as follows:

```java
Iterator itrA = c.iterator(); // c is any collection object.
Iterator<Type> itrB = c.iterator(); // Generic type.
```

For example:

```java
Iterator<String> itr = c.iterator();
Iterator<Integer> itr = c.iterator();
```

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What are Iterator methods provided by Iterator interface in Java?

---

The Iterator interface provides three methods in Java. They are as:

-   `public boolean hasNext()`: Return true if the iteration has more elements to traverse (iterate) in the forward direction.

-   `public Object next()`: Return next element in the collection. It will throw NoSuchElementException when the iteration is complete.

-   `public void remove()`: Removes the last or the most recent element returned by the iterator

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What are the advantages of iterating elements of collections using iterator?

---

Java Iterator provides the following advantages. They are:

-   An iterator can be used with any collection classes.
-   We can perform both read and remove operations.
-   It acts as a universal cursor for collection API.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What are the limitation of Iterator in Java?

---

Iterator has the following limitations or drawbacks. They are:

-   By using Iterator, we can iterate elements of collection only in the forwarding direction. We cannot iterate in the backward direction. Hence, these are called single-direction cursors.
-   We can perform either read operation or remove operation.
-   We cannot perform the replacement of new objects.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. What is fail-safe Iterator?

---

When an Iterator doesn’t throw any exception while modifying the collection during iteration, it is called fail-safe iterator.

Fail-safe iterator makes the copy of the original collection to traverse over the elements. Thus, the original collection remains structurally unchanged.

Some examples of fail-safe iterators are ConcurrentHashMap, CopyOnWriteArrayList, etc.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Explain different ways to iterate over collection in Java.

---

There are many ways to iterate over elements of a collection in Java. Following are the most common methods.

-   Using enhanced For loop: The following code is an example.

```java
Collection<String> collection = Arrays.asList("John", "Harvey", "Jacob");

for(String s : collection) {
    System.out.println(s);
}
```

-   Using Iterator method: The following code is an example.

```java

Collection<String> collection = Arrays.asList("One", "Two", "Three", "Four", "Five");

Iterator<String> itr = collection.iterator();
while(itr.hasNext()) {
    System.out.println(itr.next());
}

```

-   Using Simple For loop: A sample code is as:

```java
List<String> list = Arrays.asList("One", "Two", "Three", "Four");
for( int i = 0; i < list.size(); i++ )
{
System.out.println(list.get(i));
}
```

-   Using forEach method: An example code is as:

```java
Collection<String> collection = Arrays.asList("Apple", "Orange", "Banana", "Guava");
collection.forEach(s -> System.out.println(s));
```

This is recently introduced in Java 8. It can be invoked on any Iterable and takes one argument implementing the functional interface java.util.function.Consumer.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### List and ArrayList

#### Q. How to remove duplicates from ArrayList in Java?

---

Since the List interface allows duplicates, ArrayList also allowed it but if you remember Set interface doesn't allow duplicates, which means you can remove duplicates from ArrayList by converting it into a Set and then back to ArrayList, but how will you keep the order intact?
You can keep the order intact by using a LinkedHashSet

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. How to reverse ArrayList in Java?

---

You can reverse ArrayList by using the Collections.reverse() method. There are a couple of more ways like iterating through the list and copying elements into a new list.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Difference between an array and an ArrayList in Java?

---

The main difference between array and ArrayList is that the former is static and the latter is dynamic. You cannot change the size of the array once created, but ArrayList can grow and increase its size automatically.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. How to synchronize ArrayList in Java?

---

ArrayList is not thread-safe, its not synchronized either, which means you cannot share it between multiple threads if one of them modifies it. You can synchronize ArrayList by using `Collections.synchronizedList()` method.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. When to use ArrayList and LinkedList in Java?

---

Since array provides constant-time search operation, it's better to use ArrayList if search outnumbers add and remove operation, otherwise use LinkedList which provides constant time add and remove operation.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

#### Q. Difference between ArrayList and HashSet in Java?

---

The main difference is the former is List while the later is Set which means ArrayList allowed duplicates, keeps elements in order while HashSet doesn't allow duplicates and provides no ordering guarantee.

<p align="right">
    <small>
        <a href="#getting-started"> back to top</a>
    </small>
</p>

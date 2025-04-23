
---
## 🚀 Introduction to Multithreading

Multithreading in Java enables the **concurrent execution** of multiple parts of a program (threads) to **maximize CPU usage**.

### ✅ Key Concepts

- Java's multithreading support comes from the **`java.lang` package**.
- In **single-core** systems:  
    Threads take turns using the CPU (via **time-slicing**) — gives an illusion of parallelism.
- In **multi-core** systems:  
    Threads can run **in true parallel**, distributed by the **JVM and OS**.
- A **thread** is a **lightweight process** — the smallest unit of CPU execution.
- Java provides two ways to create threads:
    1. Extending the `Thread` class
    2. Implementing the `Runnable` interface

---

## 🧵 The Main Thread

- Every Java application starts with a **main thread**.
- This thread runs the `main()` method.
- From here, additional threads can be created.

---

## 🧱 Creating a Thread using the `Thread` Class


### ✅ Steps of Creating a Thread in `Thread` class:

- A new class `World` is created that extends `Thread`.
- The `run()` method is overridden to define the code that constitutes the new Thread.
- `start()` method is called to initiate the new thread.

### ✅ Code:

```java
class World extends Thread{
  @Override
  public void run(){
    System.out.println(Thread.currentThread().getName());
  }
}

public class createThreadUsingThreadClass{
  public static void main(String[] Google){
      World w = new World();
      w.start();
      System.out.println(Thread.currentThread().getName());
  }
}
```

### 🧠 Explanation:

- `World` extends the `Thread` class and overrides the `run()` method.
- `start()` is called to launch the new thread, which internally invokes `run()`.
- Never call `run()` directly — that runs on the current thread, not a new one.

---

## 🧱 Creating a Thread using the `Runnable` Interface


### ✅ Steps of Creating a Thread in `Runnable` Interface:

- A new class `World` is created that implements `Runnable`.
- The `run()` method is overridden to define the code that constitutes the new thread.
- A Thread object is created by passing an instance of MyRunnable.
- `start()` method is called on the Thread object to initiate the new thread.


### ✅ Code:

```java
class World implements Runnable{
  public void run(){
    System.out.println(Thread.currentThread().getName());
  }
}

public class createThreadUsingRunnableInterface{
  public static void main(String[] Google){
    World w = new World();
    Thread t1 = new Thread(w);
      t1.start();
  }
}
```


### 🧠 Explanation of Line 9 & 10:

- `World w = new World();`  
    → Creates an object of the class that implements `Runnable`.
- `Thread t1 = new Thread(w);`  
    → Passes the `Runnable` object to the `Thread` constructor. This links the thread with the task defined in `run()`.

---

## 📝 Table

|Concept|Explanation|
|---|---|
|`Thread` class|Extending this lets you create a new thread directly|
|`Runnable`|Implementing this is a flexible way to define thread logic|
|`run()`|The code that the thread executes|
|`start()`|Starts a new thread and internally calls `run()`|
|`main thread`|The initial thread of a Java program|

---
## Thread Lifecycle

- There are five states in which a thread goes through in his life time:
	- **New**: A thread is in this state when it is created but not yet started.
	- **Runnable**: After the start method is called, the thread becomes runnable. it's ready to run and is waiting for CPU time.
	- **Running**: The thread is in this state when it is executing.
	- **Blocked/Waiting**: A thread is in this state when it is waiting for a resource or for another thread to perform an action
	- **Terminated**: A thread is in this state when it has finished executing.

---
## Different States of Threads

```java
public class threadState extends Thread{
    @Override
    public void run(){
      System.out.println("RUNNING");
      try{
             Thread.sleep(1000); 
      } catch (InterruptedException e) {
        System.out.println("Jay Ganesh");
      }
    }
  public static void main(String[] Google) throws InterruptedException{
    threadState t1 = new threadState();
    System.out.println(t1.getState());
    t1.start();
    System.out.println(t1.getState());
    Thread.sleep(1000);
    System.out.println(t1.getState());
    t1.join();
    System.out.println(t1.getState());
  }
}
```

#### Output:-
```java
NEW
RUNNABLE
RUNNING
RUNNABLE
TERMINATED
```

### 🧠 **Step-by-step Explanation**

- **Class Definition**:
	- A class `threadState` extends the `Thread` class, meaning it's now a thread itself.
	- Inside the `run()` method, we:
		- Print `"RUNNING"` to show the thread has started.
		- Use `Thread.sleep(1000)` to pause the thread for 1 second (simulate work).
		- If this sleep is interrupted, it prints `"Jay Ganesh"`.
- **In `main()` Method**:
	- `threadState t1 = new threadState();`
		- Creates a thread object, but the thread hasn't started yet.
		- `t1.getState()` prints `NEW`
	- `t1.start();`
		- Starts the thread it begins executing `run()` in parallel.
		- Immediately after starting, `getState()` prints `RUNNABLE` the thread is ready/running.
	- `Thread.sleep(1000);`
		- The **main thread** sleeps for 1 second to give `t1` time to finish its execution.
- `t1.getState();`
	- Now we check `t1`'s state again:
		- It could be `TIME_WAITING` if it's still sleeping.
		- `RUNNABLE` if it's still working
		- or `TERMINATED` if it's finished.
- `t1.join();`
	- Makes the **main thread wait** until `t1` is done executing.
	- this method makes sure that the `t1` class should complete all the tasks assigned to it till then the main thread waits and then after finishing the task main thread gets executed. 
- Final `t1.getState();`
	- Prints `TERMINATED` because the thread has completely finished running.

- In Java there is no state called `RUNNING` there is only `RUNNABLE` state in java if the thread is ready to run or it's running the state will be `RUNNABLE`
---
## Thread Class V/S Runnable Interface

We know that java doesn't support multiple inheritance in such case if there is a class who want to inherit a property from its parent class and also want to extend the Thread class in such case it is not possible to extend thread class because multiple inheritance is not there in such case we can use the Runnable interface
### Example:-

```java
class A {
	...
}
class B extends A, Thread{
	// Error
}

class B extends A, implements Runnable{
	void run(){
		System.out.println("This Will Work");
	}
}
```

----
## Thread Methods

1. `t1.start()` -> This method is used to start the thread it is declared inside the main function and the `t1` is the object of the class.
**Example**:-
```java
public class threadMethods{
  public static void main(String[] Google){
      A a1 = new A();
      Thread t1 = new Thread(a1);
      t1.start();
  }
}
```
here in this example we have a class A and we have created the object of Thread class and passed the reference of A class means passed its object to the Thread class and then the `t1` object started a thread of A class.

2. `public void run()` -> This method is where we code our logic its overriden in our class 
**Example**:- 
```java
class A extends Thread{
  @Override
  public void run(){
    System.out.println("Thread is Running......");
  }
}
```
here we have inherited the `run()` method from Thread class and implemented it we can write whatever logic we want inside this method and can run it using `t1.start()` method

3. `Thread.sleep(1000)` -> This method suspends the execution of thread for given time.
**Example**:-
```java
class A extends Thread{
  @Override
  public void run(){
    for(int i = 0;i <= 10;i++){
      try{
        Thread.sleep(1000); 
      } catch(InterruptedException e){
        System.out.println(e);
      }
      System.out.println(i);
    }
  }
}
```
we have to write the `Thread.sleep()` method in `try catch` block always and also the exception is `InterruptedException` the time is in milliseconds 

4. `t1.join()` -> This method blocks the **main thread** till other thread getting executed means if there is a process going on another thread then this method will **pause** the main thread will let the another thread to finish its process then it will tell the **main thread** to finish its execution.
**Example**
```java
class A extends Thread{
  @Override
  public void run(){
          try{
        Thread.sleep(5000); 
      } catch(InterruptedException e){
        System.out.println(e);
      }
    }
}

public class threadMethods{
  public static void main(String[] Google) throws InterruptedException {
      A a1 = new A();
      Thread t1 = new Thread(a1);
      t1.start();
      t1.join();
      System.out.println("Jay Ganesh");
  }
}
```
In this program the `t1` thread will run and its execution will take 5 seconds because of the sleep and after the thread process gets finished then only the main thread will execute and `Jay Ganesh` will print on our screen after 5 seconds

---
## How to give name to a thread

To give a name to the thread of our choice for that we have to create a constructor of the class in which we have extended the Thread class it should be **parameterized constructor** it should accept a string and then from that constructor we will access the name of the thread from the Thread class using the `super` keyword.
**Example**:-
```java
class A extends Thread{
  public A(String name){
    super(name);
  }
  @Override
  public void run(){
      for(int i = 0;i < 5; i++){
	      System.out.println(Thread.currentThread().getName() + " - Count" + i);
      } 
    }
}

public class threadMethods{
  public static void main(String[] Google) throws InterruptedException {
    A a1 = new A("Jay Ganesh");
      a1.start();
  }
}
```

---
## Priority Of the Thread
we can set priority to the thread by our own using `setPriority()` method the maximum we can set is **10** the minimum is **1** and the Normal is **5**.

**Example**
```java
class A extends Thread{
  public A(String name){
    super(name);
  }
  @Override
  public void run(){
      for(int i = 0;i < 5; i++){
        System.out.println(Thread.currentThread().getName() + " - Priority: " + Thread.currentThread().getPriority() + " - count "+ i);
      } 
    }
}

public class threadMethods{
  public static void main(String[] Google) throws InterruptedException {
    A a1 = new A("Jay Ganesh");
    A a2 = new A("HarHarMahadev");
    A a3 = new A("Jay Shree Ram");
    a1.setPriority(Thread.MIN_PRIORITY);
    a2.setPriority(Thread.MAX_PRIORITY);
    a3.setPriority(Thread.NORM_PRIORITY);
    a1.start();
    a2.start();
    a3.start();
  }
}
```
This priorities are just the **hint** for the JVM its not like the highest priority thread will get executed first these are just hints it doesn't decides the order of execution

**OUTPUT**:-
```java
Minimum Priority - Priority: 1 - count 0
Minimum Priority - Priority: 1 - count 1
Minimum Priority - Priority: 1 - count 2
Minimum Priority - Priority: 1 - count 3
Minimum Priority - Priority: 1 - count 4
Mormal Priority - Priority: 5 - count 0
Maximum Priority - Priority: 10 - count 0
Mormal Priority - Priority: 5 - count 1
Mormal Priority - Priority: 5 - count 2
Mormal Priority - Priority: 5 - count 3
Mormal Priority - Priority: 5 - count 4
Maximum Priority - Priority: 10 - count 1
Maximum Priority - Priority: 10 - count 2
Maximum Priority - Priority: 10 - count 3
Maximum Priority - Priority: 10 - count 4
```
Here we can see in the output the order is not serialized it is random.
The `setPriority()` method actually works on **Single Core CPU's** where the parallel programming is not possible.

---
## Thread Interruption
It is a method that interrupts a thread and stops it from doing whatever it is doing like if the thread is sleeping the `interrupt()` method will make sure the thread gets interrupted and stops.

**Example**
```java
class A extends Thread{
  public void run(){
    try{
      Thread.sleep(1000);
      System.out.println("Thread is Running....");
    } catch(InterruptedException e){
      System.out.println("Thread Interrupted "+ e);
    }
  }
}

public class threadInterrupted{
  public static void main(String[] Google){
    A a1 = new A();
    a1.start();
    a1.interrupt();
  }
}
```

**OUTPUT**
```java
Thread Interrupted java.lang.InterruptedException: sleep interrupted
```

---
## `yield()` method

This method gives hints to the compiler or the schedular that it's not necessary to execute me fully and then execute another thread you can execute another thread and then can execute me.

**Example**
```java
class A extends Thread{
  public void run(){
    for(int i = 0;i<5;i++){
      System.out.println(Thread.currentThread().getName()+ "- Count: - "+i);
      Thread.yield();
    }
  }
}
public class threadYield{
  public static void main(String[] Google){
    A a1 = new A();
    A a2 = new A();
    a1.start();
    a2.start();
  }
}
```

**OUTPUT**
```java
Thread-1- Count: - 0
Thread-1- Count: - 1
Thread-0- Count: - 0
Thread-1- Count: - 2
Thread-1- Count: - 3
Thread-0- Count: - 1
Thread-0- Count: - 2
Thread-1- Count: - 4
Thread-0- Count: - 3
Thread-0- Count: - 4
```
Here in the output we can see that the threads are running simaltenously not like thread 0 executs first then thread 2.

---
## Daemon threads
This are the threads that runs in the background JVM doesn't waits till there execution gets finished it works in the background and if there are more threads then JVM will run those threads and the Daemon threads will run in the background without interrupting main process.

**Example**:-
```java
class A extends Thread{

  @Override
  public void run(){
    while (true) {
      System.out.println("Jay Ganesh"); 
    }
  }
}

public class threadDeamon{
  public static void main(String[] Google){
    A a1 = new A();
    a1.setDaemon(true);
    a1.start();
    System.out.println("Main Done");
  }
}
```

**OUTPUT**
```java
Main Done
Jay Ganesh
Jay Ganesh
Jay Ganesh
Jay Ganesh
Jay Ganesh
Jay Ganesh
```
in this code we have used `setDaemon()` method that sets the `a1` thread as daemon thread and JVM checks if every thread is done executing and if yes then it stops the execution of daemon thread also in this code we have a infinite loop in the daemon thread running but it stops as soon as the main thread stops.

---
## Synchronization

Synchronization means two threads sharing same resource but with a proper sync between then because of one another is not affected that is synchromization.

**Example**
```java
class Counter {
  private int count = 0;
  public synchronized void increment(){
    count++;
  }
  public int getCount(){
    return count;
  }
}

class MyThread extends Thread{
  private Counter counter;
  public MyThread(Counter counter){
    this.counter = counter;
  }

  @Override
  public void run(){
    for(int i = 0 ; i< 1000;i++){
      counter.increment();
    }
  }
}

public class threadSync{
  public static void main(String[] Google){
    Counter counter = new Counter();

    MyThread t1 = new MyThread(counter);
    MyThread t2 = new MyThread(counter);
    t1.start();
    t2.start();
    try{
      t1.join();
      t2.join();
    }catch (Exception e){
    }
    System.out.println(counter.getCount());
  }
}
```
here there is an single object class `Counter` and there are two objects sharing a single object of class `MyThread` so what happens in this code is that the threads will increase the counter by 1 and at the end it returns the final count but here we have used the `synchronized` keyword before the method `increment()` because both thread are trying to increase the count of the count variable and because of that keyword it gives output 2000 always if the `synchronized` keyword is not used then it will not return 2000 count always.

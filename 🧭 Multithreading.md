
---
## 🧵Basics of Threads in Java

### 🤔 What is a Thread?
- A **thread** is a **lightweight unit of execution** inside a process.
- A **Java Program by default has one thread**, called the `main thread`
- You can create more threads to **do multiple tasks at once**.

---
### 🧠 Analogy:

> Think of a **process as a restaurant**, and **threads as chefs**
> The restaurant (process) can hire 1 chef (single-threaded) or many chefs(multi-threaded) to cook multiple dishes in parallel.

---
### 🧪 Let’s Prove it in Code: Single-threaded Java

```java
public class SingleThread{
	public static void main(String[] Google){
		System.out.println("Start");
		cook(); // doing 2 thing at a time
		serve();
		System.out.println("Done");
	}

	static void cook(){
		System.out.println("Cooking...");
	}
	static void serve(){
		System.out.println("Serving...");
	}
}
```
Output is always in order, because there’s only **one thread**: `main`.

---
## Extra Point

why to use `static` keyword here:-
You're calling `cook()` and `serve()` **directly from `main()`**, which is also:
```java
public static void main(String[] Google)
```
So here's the rule:

---
### 🔑 Rule: `main()` is a static method → it can **only call other static methods directly**

Because `main()` belongs to the **class** (not to an object), it can't access **non-static methods** without creating an object.

----
## 🔥 Creating Threads in Java

### ✅ Way 1: Extend `Thread` class

```java
class MyThread extends Thread {
	public void run(){
		System.out.println("Thread Running: "+ getName());
	}
}

public class ThreadExample{
	public static void main(String[] Google){
		MyThread t1 = new MyThread();
		t1.start(); // starts a new thread
	}
}
```

- `start()` creates a new thread and calls `run()` in parallel.
- `run()` by itself does **not** start a new thread(interview trick question).

---
### ✅ Way 2: Implement `Runnable` interface (Preferred Way)

```java
class MyRunnable implements Runnable {
	public void run(){
		System.out.println("Runnable Running in: "+ Thread.currentThread().getName());
	}
}
public class RunnableExample {
	public static void main(String[] Google){
		Thread t1 = new Thread(new MyRunnable());
		t1.start();
	}
}
```

- **Why is this better ?**
	- Because Java doesn't support multiple inheritance.
	- With `Runnable`, you can extend other classes too.

---
## 🧪 Practice Tasks

1. Create a class that extends Thread, override `run()`, print numbers 1 to 5.

```java
class Parent extends Thread{
  public void run(){
    System.out.println("This is Thread Process "+getName());
  }
}

class Child extends Parent{
  @Override
  public void run(){
    for(int i = 1;i<=5;i++){
      System.out.println("Thread: "+getName() + "-> "+ i);
    }
  }
} 

public class ThreadPrac{
  public static void main(String[] Google){
    Parent p = new Child();
    p.start();
  }
}
```

**Output**
```java
Thread: Thread-0-> 1
Thread: Thread-0-> 2
Thread: Thread-0-> 3
Thread: Thread-0-> 4
Thread: Thread-0-> 5
```

---
#### What is Practiced in the code
- Inheritance with threads
- Overriding `run()`
- Using `start()` to trigger threading
- Polymorphism with threads(Parent ref = Child Object)

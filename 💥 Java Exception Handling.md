
---
## 🧠 1. What is an Exception?

In the real world, imagine you're withdrawing cash from an ATM.
You:
- Insert Card
- Enter PIN
- Request 10,000
- _But the bank system crashes because of a bug or insufficient balance_

This is a **runtime problem**.
In java, such unexpected problems are called **Exceptions**

> **Definition**: An **exception** is an event that occurs during the **execution of a program** that disrupts the normal flow of instructions.

---
## 📌 2. Types of Problems in Java


| Type               | What it is?                           | Example                    |
| ------------------ | ------------------------------------- | -------------------------- |
| Compile-Time Error | Detected before running code          | Missing `;`, syntax issues |
| Logical Error      | Code runs but gives wrong result      | Wrong formula              |
| Exception(RunTime) | Happens **while** running the program | Divide by 0, null access   |

---
## 🚦 3. Exception Hierarchy

Java has a class Called `Throwable` that splits into:

```java
Throwable
├── Error (Serious problems, typically unrecoverable)
│   ├── OutOfMemoryError
│   ├── StackOverflowError
│   └── VirtualMachineError
│
└── Exception (Problems we can recover from)
    ├── Checked Exceptions (Must be handled or declared)
    │   ├── IOException
    │   ├── SQLException
    │   └── FileNotFoundException
    │
    └── Unchecked Exceptions (Runtime; optional to handle)
        ├── NullPointerException
        ├── ArithmeticException
        ├── ArrayIndexOutOfBoundsException
        └── NumberFormatException
```

Exception is an event that disrupts the normal flow of the program. it is an object which is thrown at runtime.

## 🔄 Basic Flow of Exception Handling

```java
try {
	// Code that might cause exception
} catch (ExceptionType e){
	// Handle the exception here
} finally {
	// Optional: Cleanup code that always runs
}
```
---
## 🔨 Example: Divide By Zero

```java
public class ExceptionExample{
	public static void main(String[] Google){
		int a = 10;
		int b = 0;

		try {
			int result = a / b;
			System.out.println("Result: "+ result);
		} catch (ArithmeticException e){
			System.out.println("You cannot divide by zero !");
		} finally {
			System.out.println("Finally block always runs.");
		}
	}
}
```
### Output:

```java
You Cannot divide by zero!
Finally block always runs.
```
---
## 🔍 Types of Exceptions


| Type      | Description                        | Example               |
| --------- | ---------------------------------- | --------------------- |
| Checked   | Checked at compile time            | FileNotFoundException |
| Unchecked | Caught at runtime (not compulsory) | ArithmaticException   |
| Errors    | Serious JVM issues                 | StackOverflowError    |

---
## Checked vs Unchecked Exceptions

- **Checked Exception**: These exceptions are checked at **compile time**, forcing the programmer to handle them **explicitly.
- **Unchecked Exception**: These exceptions are checked at **runtime** and do not require **explicit handling at compile time**

### Difference Between Checked and Unchecked Exceptions

| Feature              | Checked Exception                                                                                           | Unchecked Exception                                             |
| -------------------- | ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Behaviour            | Checked exceptions are checked at compile time.                                                             | Unchecked exceptions are checked at run time                    |
| Base Class           | Derived from Exception                                                                                      | Derived from RuntimeException                                   |
| Cause                | External factors like file I/O and database connection cause the checked exception                          | Programming bugs like logical errors cause unchecked exceptions |
| Handling Requirement | Checked exceptions must be handled using a **try-catch block** or must be declared using the throws keyword | No handling is required                                         |
| Examples             | IOException, SQLException, FileNotFoundException                                                            | NullPointerException, ArrayIndexOutOfBoundsException.           |


---
## ✅ Common Exception Types


| Exception             | Triggered When               |
| --------------------- | ---------------------------- |
| ArithmeticException   | Divide By Zero               |
| NullPointerException  | Access method on null object |
| ArrayIndexOutOfBounds | Access invalid array index   |
| NumberFormatException | Invalid number conversion    |
| FileNotFoundException | File path doesn't exist      |

---
## 🔁 `finally` Block

- Runs **every time**, regardless of exception
- Used to **release resources** like file streams or DB connections.

```java
try {
	// File read logic
} catch (...){
	// error
} finally {
	// close file
}
```
---
## 💣 Throwing Exceptions Manually

```java
public void setAge(int age){
	if(age < 0){
		throw new IllegalArgumentException("Age can't be negative");
	}
	this.age = age;
}
```
---
## 📦 `throws` Keyword
Used when a method wants to **pass the responsibility** of handling the exception to the caller.

```java
void readFile throws IOException {
	// File reading logic
}
```
---
## 🧠 Pro Tips for Developers
- Catch **specific exceptions** first, then general
- Avoid catching `Exception` unless you must
- Always clean up in `finally` or use **try-with-resources**
- Don't **ignore** exceptions(bad: `catch(Exception e) {})`

---
## 🎯 Summary

| Keyword   | Meaning                           |
| --------- | --------------------------------- |
| `try`     | Block where risky code goes       |
| `catch`   | Handles the error                 |
| `finally` | Runs always                       |
| `throw`   | Used to manually throw exception  |
| `throws`  | Declares exception responsibility |

## Practice Questions

1. What's the difference between `throw` and `throws`?
	-> `throw` - **_you are manually throwing an exception right now_**
	> You, the developer, say: "This situation is **not acceptable**, I'm throwing this error myself !"

✅ **Used to actually throw the exception object**

```java
if(age < 0){
	throw new IllegalArgumentException("Age Cannot be negative");
}
```
💬 Think of it as: **"throw this now!"**

---
`throws` - **_you're warning others: "This method might throw an exception. Be ready._**

> You're not throwing it yourself, you're saying: "If something goes wrong, i **might** throw this exception whoever calls me should handle it."

✅ **Used in method signature**

```java
void readFile(String fileName) throws IOException {
	FileReader file = new FileReader(fileName); // might throw IOException
}
```
💬 Think of it as: **"this method might throw this"**

---
### 🔄 Summary Table

|Feature|`throw`|`throws`|
|---|---|---|
|Purpose|Actually **throws** an exception|**Declares** a possible exception|
|Used inside|Method body|Method signature|
|Followed by|Object of exception (`new`)|Name of exception class|
|Example|`throw new ArithmeticException();`|`public void read() throws IOException`|
|Who handles it|The caller or try-catch block|The caller of the method|

---
2. What is the purpose of the `finally` block and when is it executed?
	-> The `finally` block in Java is used to **guarantee the execution of code**, no matter what happens in the `try` or `catch` blocks.
	The Purpose of `finally`:
		1. Closing database Connections
		2. Releasing file handles
		3. Releasing memory, sockets, threads, etc.
 **✅ Example**:
 
 ```java
 public class FinallyExample {
	 public static void main(String[] Google){
		 try {
			 System.out.println("Opening File....");
			 int a = 10 / 0; // will throw exception 
		 } catch (ArithmeticException e){
			 System.out.println("Caught: "+ e);
		 } finally {
			 System.out.println("Closing File... (Finally block)");
		 }
	 }
 }
```

**Output**:
```java
Opening file...
Caught: java.lang.ArithmeticException: / by zero
Closing file... (finally block)
```
---
### 🧠 Bonus Insight (Pro-Level)
If the program **terminates with `System.exit(0)`** before `finally`, then it will not run:
```java
try {
	System.exit(0);
} finally{
	System.out.println("Will not be printed");
}
```
---
 3. What happens if you **don’t handle** a runtime exception?
	-> If a runtime exception (also called an **unchecked exception**) is **not handled**, the program will:
		1. Crash Unexpectedly
		2. Print a stack trace
		3. Terminate Immediately from the point of exception
		
##  🧠 What actually happens under the hood?

- Java **creates an exception object**
- It **searches up the call stack** for a `try-catch` block that can handle it
- If non is found, the JVM:
	- Prints a detailed **error message and stack trace**
	- **Terminates** the program

## What is Stack Trace in Java

> A **stack trace** is a **list of method calls** that the program was executing **at the time an exception occurred**.
> A stack trace helps developers **pinpoint the exact place** where the exception occurred and **understand the method call chain** that led to it

It's the **roadmap of how the program reached the error** and helps developers **debug** the issue.

### 🧱 Real Life Analogy:

Imagine a courier truck crashed while delivering a package.  
The GPS tracker shows:

- 📍 Left the warehouse
- 📍 Reached City A
- 📍 Took a wrong turn
- 💥 Crash happened here

💡 **That’s your stack trace!**  
A breadcrumb trail of what happened before the crash 🧩


---
 4. Is it mandatory to handle checked exceptions? Why?
	-> Yes, it is **mandatory** to handle checked exceptions in java because they are **verified at compile time** if not handled properly, your code will **fail to compile**
	
### Why?
Java wants to make sure that you **either handle the exception** or **explicitly declare that it may happen**, because:
- These exceptions are **predictable**
- They occur due to **external factors**(like file systems, datatbases, etc).

### How to handle them?
To handle them we can use **try-catch block** or using **throws(deceleration)**

#### Example

1. **Using try-catch**
```java
try {
	FileReader file = nre FileReader("data.txt");
} catch {
	System.out.println("File Not Found !!");
}
```

2. **Using throws(deceleration)**
```java
public void readFile() throws FileNotFoundException {
	FileReader file = new FileReader("data.txt");
}
```

---

 4. Write a real-world analogy for exception handling (your own example).
  	-> Imagine you're flying from **India to Australia**.
- ✈️ In the **`try` block**, you plan to catch your original flight.
- 🚫 If the flight gets **delayed or canceled**, you enter the **`catch` block**, where you look for **alternate flights or solutions**.
- 🧳 No matter what happens, you still **go to the airport** — that's the **`finally` block**. It runs **regardless** of whether you flew or not.
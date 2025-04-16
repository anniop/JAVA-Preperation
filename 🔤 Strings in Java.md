
-----
## 📌 Basic Definition
> A **String** in Java is a **sequence of characters**, enclosed in **double quotes**(`""`).

```java
String name = "Jay Ganesh";
```
- It is **not a primitive** type like `int` or `char`
- It is an **object** of the `String` **class** in the `java.lang` package
----
## 📦 How Strings are Stored Internally?
Behind the scenes:
```java
String s = "Ganesh";
```
is stored like:
```java
char[] arr = {'G', 'a', 'n', 'e', 's', 'h'};
```
So, internally, **Java stores Strings as a character array**.

----
## 🔐 Are Strings Mutable or Immutable?
### ✅ **Strings are Immutable in Java**
> Once a string object is created, it **cannot be changed**

```java
String s = "Hello";
s.concat(" World"); // This creates a NEW string
System.out.println(s); // "Hello" (NOT "Hello World")
```
**Why ?**
- For **security** (used in DB credentials, file paths, etc)
- For **string pool reuse**(helps in memory efficiency)
- For **thread-safety**(Immutable objects are always safe to share)
----
## ✨ Ways to Create a String
### 1️⃣ Using String Literal (Recommended)
```java
String a = "Java";
String b = "Java"; // 'b' points to the same memory as 'a'(in String pool)
```
✅ Efficient  
✅ Stored in the **String Constant Pool**  
✅ Reused if same string already exists

----
### 2️⃣ Using `new` Keyword
```java
String c = new String("Java");
```
❌ Always creates a **new object in heap memory**, even if the same content exists  
❌ Not memory efficient  
✅ Sometimes useful when we explicitly want a new object

------
## 📦 What is the String Constant Pool?
Java maintains a **special area in memory called the String Constant Pool** to store **unique string literals**.
```java
String s1 = "Hello";
String s2 = "Hello";
```
✅ Both s1 and s2 point to the **same object in the pool**

---

## ⚙️ String Methods – Must-Know

| Method               | Example                   | Description                      |
| -------------------- | ------------------------- | -------------------------------- |
| `length()`           | `s.length()`              | Get number of characters         |
| `charAt(i)`          | `s.charAt(2)`             | Get character at index `i`       |
| `equals()`           | `s1.equals(s2)`           | Compare content                  |
| `equalsIgnoreCase()` | `s1.equalsIgnoreCase(s2)` | Compare content (ignore case)    |
| `substring()`        | `s.substring(2, 5)`       | Extract part of string           |
| `indexOf('a')`       | `s.indexOf('a')`          | First occurrence of char         |
| `lastIndexOf()`      | `s.lastIndexOf('a')`      | Last occurrence                  |
| `contains("abc")`    | `s.contains("abc")`       | Checks substring presence        |
| `startsWith()`       | `s.startsWith("He")`      | Checks prefix                    |
| `endsWith()`         | `s.endsWith("ld")`        | Checks suffix                    |
| `replace()`          | `s.replace("a", "b")`     | Replace character or string      |
| `toUpperCase()`      | `s.toUpperCase()`         | All caps                         |
| `toLowerCase()`      | `s.toLowerCase()`         | All lowercase                    |
| `trim()`             | `s.trim()`                | Removes leading/trailing spaces  |
| `split(" ")`         | `s.split(" ")`            | Splits into array based on space |


---

## 🧠 String Comparison: `==` vs `.equals()`

| Operator    | Compares       | Example         | Result                  |
| ----------- | -------------- | --------------- | ----------------------- |
| `==`        | Memory address | `s1 == s2`      | true if same object     |
| `.equals()` | Content        | `s1.equals(s2)` | true if content is same |


---

## 🧾 String in Java Summary

| Property       | String                 |
| -------------- | ---------------------- |
| Mutable        | ❌ No                   |
| Stored in pool | ✅ Yes (if literal)     |
| Thread-safe    | ✅ Yes                  |
| Performance    | ❌ Slower when modified |

------
# 🔧 `StringBuilder` and `StringBuffer` in Java

> How to build and **modify strings efficiently** 🔁

---

## 🔸 Why do we need `StringBuilder`?

### Problem with `String`:

Strings are **immutable**, so every time you "modify" them, Java creates a **new object**.

```java
String s = "Hello"; s = s + " World"; // 👈 A new object is created behind the scenes
```

This is **slow and memory-wasteful**, especially in **loops or large operations**.

---

## ✅ What is `StringBuilder`?

> `StringBuilder` is a **mutable** sequence of characters — like a flexible version of `String`.


```java
StringBuilder sb = new StringBuilder("Hello"); sb.append(" World"); System.out.println(sb); // Hello World
```

- **Efficient** for modifying strings (like appending, deleting) 
- Does **not create a new object** every time 
- **Faster than `String`** for modifications 

---

## 🧱 StringBuilder Common Methods

| Method                     | Example                  | Description                       |
| -------------------------- | ------------------------ | --------------------------------- |
| `append()`                 | `sb.append("Java")`      | Adds to end                       |
| `insert(index, str)`       | `sb.insert(5, "Hello")`  | Insert at position                |
| `delete(start, end)`       | `sb.delete(2, 4)`        | Deletes chars between start & end |
| `deleteCharAt(index)`      | `sb.deleteCharAt(3)`     | Deletes single char               |
| `replace(start, end, str)` | `sb.replace(1, 3, "oo")` | Replaces part of string           |
| `reverse()`                | `sb.reverse()`           | Reverses the string               |
| `toString()`               | `sb.toString()`          | Converts to regular `String`      |
| `setCharAt(i, ch)`         | `sb.setCharAt(2, 'z')`   | Change specific character         |
| `length()`                 | `sb.length()`            | Number of characters              |

---

## ✂️ Example Code

```java
public class Demo {    
public static void main(String[] args) {

	StringBuilder sb = new StringBuilder("Ganesh");    
	    
		sb.append(" Patil");       
		System.out.println(sb); // Ganesh Patil   
		    
		sb.insert(0, "Mr. ");        
		System.out.println(sb); // Mr. Ganesh Patil   
		
		sb.replace(0, 3, "Dr.");        
		System.out.println(sb); // Dr. Ganesh Patil       
		
		sb.deleteCharAt(2);       
		System.out.println(sb); // Dr Ganesh Patil     
		     
		sb.reverse();         
		System.out.println(sb); // lit aP h saneG .rD     
		
	} 
}
```

---

## 🧠 What is `StringBuffer` then?

> `StringBuffer` is **same as `StringBuilder`**, but it is **thread-safe** (synchronized).

```java
StringBuffer sb = new StringBuffer("Hello"); sb.append(" Java"); System.out.println(sb); // Hello Java
```

### But…

- It’s **slower** than `StringBuilder` (because of synchronization) 
- You’ll only use it when **multiple threads** are accessing the same string 

---

## 🧪 Difference Between String, StringBuilder, StringBuffer

| Feature     | `String`      | `StringBuilder`        | `StringBuffer`          |
| ----------- | ------------- | ---------------------- | ----------------------- |
| Mutable     | ❌ No          | ✅ Yes                  | ✅ Yes                   |
| Thread-safe | ✅ Yes         | ❌ No                   | ✅ Yes                   |
| Speed       | 🚫 Slowest    | ✅ Fastest              | ⚠️ Slower (thread sync) |
| Use case    | Fixed content | Single-threaded modify | Multi-threaded modify   |

---

## 🚀 Interview Tip:

> If you're modifying a string **many times in a loop**, always use **StringBuilder**.

```java
// Bad
String s = "";
for (int i = 0; i < 1000; i++) {
    s += i; // new object every time 😓
}

// Good
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i); // efficient 🚀
}

```
---


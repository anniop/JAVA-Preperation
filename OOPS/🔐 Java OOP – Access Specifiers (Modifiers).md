
---
## What Are Access Specifiers?

> **Access Specifiers** (Also called **access modifiers**) in Java define **where** you can **access a class, method, or variable** from.

They help you control the **visibility** of your code

---
## 🔐 Types of Access Specifiers in Java

| Modifier     | Within Class | Same Package | Subclass (Different Pkg) | Outside Class |
|--------------|--------------|--------------|---------------------------|----------------|
| `private`    | ✅ Yes        | ❌ No         | ❌ No                      | ❌ No           |
| (default)    | ✅ Yes        | ✅ Yes        | ❌ No                      | ❌ No           |
| `protected`  | ✅ Yes        | ✅ Yes        | ✅ Yes                     | ❌ No           |
| `public`     | ✅ Yes        | ✅ Yes        | ✅ Yes                     | ✅ Yes          |
### 🔒 `private`

- Accessible **only inside the same class**.
- Often used to **hide data**.
- Helps achieve **encapsulation**

```java
private int accNo;
```

✅ Accessible: inside the class  
❌ Not Accessible: from outside or even subclass

------------
### 🌐 (default) — No Keyword!
- When you **don't write any modifier**, java assumes **default access**
- Accessible **only inside the same package**.

```java
int rollNo; // default access
```

✅ Accessible: inside the same package  
❌ Not Accessible: from outside the package

------
### 🛡️ `protected`
- Accessible in:
	- Same class
	- Same package
	- Subclasses in different packages

```java
protected String name;
```

✅ Great for **inheritance with some access control**

----
### 🌍 `public`
- Accessible **from anywhere**.
- Used for methods like `main()` and utility functions.

```java
public vid display(){
	....
}
```
✅ Use for APIs, main class, and shared utilities

----
## 🧠 Quick Use Case Table

| Use Case                      | Modifier    |
| ----------------------------- | ----------- |
| Hide sensitive data           | `private`   |
| Allow access only in same pkg | default     |
| Allow subclass access         | `protected` |
| Allow full access everywhere  | `public`    |

----
## 🔁 Example Code

```java
class Student{
	private int age = 20;
	public String name = "Ganesh";
	protected course = "Java";
	int rollNo = 83; // default

	void showDetails(){
		System.out.println(name + ", " + age + ", " + rollNo + ", " + course);
	}
}
```

---
## ✅ What is Polymorphism?

> **Polymorphism** means **many forms**.
> In Java, it allows you to use **one method name or reference** to behave **differently** depending on the object or context.

----
### 🎯 Real-Life Example
- You say "open()" to:
- 📱 a phone → it opens an app
-  📦 a box → it opens the lid
- 🧑‍💼 a file → it opens in an editor

✅ **Same word → Different behavior**

---
## 🔥 Two Types of Polymorphism in Java

| Type                   | Also Known As            | How It Works          | Example         |
|------------------------|--------------------------|------------------------|------------------|
| **Compile-Time**       | Method Overloading        | Decided at compile time| Same class       |
| **Run-Time**           | Method Overriding         | Decided at runtime     | Inheritance-based|

---
## 1️⃣ Compile-Time Polymorphism – Method Overloading

### What is It ?
> Same method name, but different **parameters** within the same class.

```java
class MahtOps {
	int add(int a, int b){
		return a + b;
	}

	double add(double a, double b){
		return a + b;
	}

	int add(int a, int b, int c){
		return a + b + c;
	}
}
```
📌 This is called **name mangling**. The compiler distinguishes methods based on **parameter type/count/order**.

---
### 🧠 Rules of Overloading:

- ✅ Same method name
- ✅ Different parameter list (type, number, order)
- ❌ Return type alone is NOT enough

-----
## 2️⃣ Run-Time Polymorphism – Method Overriding

### ✅ What is it?
> Same method name, **same parameters**, but defined in **child class**.

```java
class Animal {
	void sound(){
		System.out.println("Animal makes sound");
	}
}

class Dog extends Animal{
	@Override
	void sound(){
		System.out.println("Dog Barks");
	}
}
```

### ✅ Key Concept:
```java
Animal a = new Dog(); // reference is parent, object is child
a.sound(); // Dog's version is called (not Animal's!)
```
This is **runtime polymorphism** in action Java decides at **runtime** which version to run based on object type.

---
## 🔑 Differences Summary

| Feature              | Overloading                 | Overriding                               |
| -------------------- | --------------------------- | ---------------------------------------- |
| Based on             | Parameters                  | Object type                              |
| Happens at           | Compile time                | Runtime                                  |
| Inheritance required | ❌ No                        | ✅ Yes                                    |
| Class                | Same class                  | Parent-child                             |
| Return type          | Can be different (optional) | Must be same or covariant                |
| Annotation           | ❌ Not used                  | ✅ `@Override` (optional but recommended) |

---
## 💡 Bonus: `@Override` Annotation

```java
@Override
void sound(){
	...
}
```
Helps compiler catch mistakes (e.g wrong signature)

---
## 📌 Why is Polymorphism Useful?
- Clean, reusable code.
- Better structure for large systems
- Supports **open-closed principle**(open for extension, closed for modification)

----
## 🎯 Practice Challenge

1. Create a class `Shape` with a method `area()`
2. Create subclasses `Circle`, `Rectangle`, `Square`
3. Override `area()` in each subclass
4. Create a `Shape` reference and assign it to each object (upcasting)
5. Call `area()` and observe different results
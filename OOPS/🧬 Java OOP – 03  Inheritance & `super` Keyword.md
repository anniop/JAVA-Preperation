
---
## ✅ What is Inheritance?

> **Inheritance** is when one class **acquires properties and behaviours** of another class

📦 In simple terms:
- Parent class -> gives values (Like DNA)
- Child class -> Inherits from the parent

✅ This promotes **code reusability** and **clean structure**

-----------
## 🔁 Why Use Inheritance?

- 🔄 Reuse code from existing classes
- 👶 Create specialized versions of general classes
- 🔧 Avoid duplication
- 🔥 Enables **polymorphism** (which we’ll do next!)

------
## 📦 Basic Syntax

```java
class Parent{
	// parent fields and methods
}

class Child extends Parent {
	// child can use and add to parent features
}
```
-----
## 📗 Example

```java
class Animal {
	void speak(){
		System.out.println("The animal makes a sound");
	}
}

class Dog extends Animal {
	void bark(){
		System.out.println("The dog barks");
	}
}
public class Main {
	public static void main(String[] Google){
		Dog d = new Dog();
		d.speak(); // Inherited from Animal
		d.bark(); // its own method
	}
}
```
---
## 🧠 Types of Inheritance in Java

| Type                 | Syntax Support | Explanation                                  |
| -------------------- | -------------- | -------------------------------------------- |
| Single               | ✅              | One parent, one child                        |
| Multilevel           | ✅              | Child of a child                             |
| Hierarchical         | ✅              | One parent, multiple children                |
| Multiple (via class) | ❌              | Not supported directly (only with interface) |
| Hybrid               | ❌              | Also not supported directly                  |

----
## 🔑 `super` Keyword
> `super`refers to the **parent class**.

#### Used to:
1. Call parent class's **constructor**
2. Access **overridden** methods from parent
3. Access **parent variables** if shadowed
-----
### 🧪 Example 1: `super()` Method call

```java
class Vehicle{
	void start(){
		System.out.println("The vehicle has Started");
	} 
}

class Car extends Vehicle{
	void drive(){
		super.start();
		System.out.println("The Car is Moving");
	}
}

class Main{
	public static void main(String[] Google){
		Car c = new Car();
		c.drive();
	}
}
```
#### Output:-
```java
The Vehicle has Started
The Car is Moving
```

---

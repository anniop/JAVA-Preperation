
-----
## ✅ What is a Class?

> A **class** is a **blueprint** or **template** for creating objects.

- It defines **what an object will look like**
- Contains **fields (Variables)** and **methods (functions)**.

📦 Think of a **class like a design of a car** — it tells you what the car should have (engine, wheels, etc.), but it’s not an actual car.

----
## ✅ What is an Object?

>  An **object** is a **real-world instance** of a class.

- When you create an object, you **allocate memory**
- You can **access variables and methods** of that object

🚗 Think of an object as a **real car built from the car blueprint** (class).

----
## 🧠 Key Terminology

| Term   | Meaning                          |
| ------ | -------------------------------- |
| Class  | Blueprint (doesn’t take memory)  |
| Object | Instance of class (takes memory) |
| Field  | Variable inside a class          |
| Method | Function inside a class          |

----
## 🧱 Class Syntax

```java
class ClassName {
	// fields (variables)
	dataType variableName;

	// methods
	returnType methodName(parameters) {
		// logic
	}
}
```

---
## 📦 Object Creation Syntax

```java
ClassName objectName = new ClassName();
```

- `new` keyword is used to create the object
- Object gets memory in **heap**

---
## 🚀 Example

```java
class Car {
	String brand;
	int year;

	void start() {
		System.out.println(brand + " started");
	}
}

public class Main {
	public static void main(String[] Google){
		Car myCar = new Car(); // object creation
		myCar.brand = "Toyota"; // accessing fields
		myCar.year = 2025;

		myCar.start(); // calling method
		System.out.println(myCar.year); 
	}
}
```

### 🧠 Output:
```java
Toyota started
2025
```

---
## 🧪 Real Life Analogy
|Real World|Java|
|---|---|
|Mobile|Object|
|Mobile Design|Class|
|Features|Fields/Methods|

---
## 💡 Why Use Classes and Objects?
- Reusability
- Cleaner code
- Better structure for big projects
- Forms the base of OOP features like inheritance and polymorphism.

----
## 📌 Important Notes
- A class **does not occupy memory** until you create an object from it.
- You can create **multiple objects** from the same class
- Methods help define the **behaviour** of the object.
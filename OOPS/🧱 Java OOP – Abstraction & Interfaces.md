
---
## ✅ What is Abstraction?

> **Abstraction** means **hiding complex implementation** and showing only the **essential details**.

🧠 Think of it like:
- You **drive** a car -> you don't need to know how the engine works.
- You **click** a button -> you don't see what's happening behind it.

---
## 🔹 Why Abstraction?

- 🧼 Keeps code **clean and focused**
- 🔐 Helps with **security**
- 🧱 Makes systems **modular and scalable**
---
## 🔸 Ways to Achieve Abstraction in Java

| Technique          | Description                  |
| ------------------ | ---------------------------- |
| **Abstract Class** | Partial abstraction (0-100%) |
| **Interface**      | Full abstraction (100%)      |

---
# 📘 Abstract Class

### ✅ What is it?

> A class declared with the `abstract` keyword that **cannot be instantiated**.
> It can contain **abstract methods** (no body) and **regular methods** (with body).

---
### 🧱 Syntax

```java
abstract class Animal {
	abstract void sound(); // no body

	void eat(){
		System.out.println("Eating...");
	}
}
```

```java
class Dog extends Animal{

	@Override
	void sound(){
		System.out.println("Bark");
	}
}
```

---
### 🔒 Notes:
- You **cannot create objects** of abstract classes.
- Subclasses **must override** all abstract methods
- Can have **constructor, fields, non-abstract methods**
----
# 🌐 Interface

### ✅ What is it?

> An `interface` is a **completely abstract class** where :

- All methods are **public and abstract** by default (until java 7)
- Cannot have implementation(except static/default methods from java 8+)
---
### 💻 Syntax

```java
interface Shape {
	void area();
}
```

```java
class Circle implements Shape {
	public void area(){
		System.out.println("Area of Circle is: ......");	
	}
}
```
---
## 🔄 Abstract Class vs Interface

|Feature|Abstract Class|Interface|
|---|---|---|
|Inheritance|`extends`|`implements`|
|Method Types|Abstract + Concrete|Only abstract (Java 7), can use `default` from Java 8|
|Constructors|✅ Yes|❌ No|
|Fields|Can have variables|Only `public static final`|
|Multiple Inheritance|❌ Not allowed|✅ Allowed via interfaces|
|Use Case|Shared base class|Full abstraction / capability-based|

----
## 🧠 When to Use What?

- Use **abstract class** when:
	- You want to provide **default implementation**
	- You expect **hierarchical relationships**
- Use **interface** when:
	- You want to define **contract-like rules**
	- You want to support **multiple inheritance**
---
## 📌 Recap in One Line:
> **Abstract Class** = "is-a" relationship with optional shared code
> **Interface** = "can-do" capability with contract enforcement

## Code for Interface and Abstract Class

#### This is Of Abstract class
```java
abstract class Appliance {
  String brand;
  int power;

  Appliance(String brand, int power){
    this.brand = brand;
    this.power = power;
  }

  abstract void turnOn();

  void showInfo(){
    System.out.println("The brand is "+brand+" and power is "+power+" W");
  }
}

class Fan extends Appliance{
  
  Fan(String brand, int power){
    super(brand, power);
  }
  @Override
  void turnOn(){
    System.out.println("Fan is Spinning");
  }
}

class WashingMachine extends Appliance{
  
  WashingMachine(String brand, int power){
    super(brand, power);
  }
  @Override
  void turnOn(){
    System.out.println("Washing Machine is running");
  }
}

public class Abstract{
  public static void main(String[] Google){
    Appliance f = new Fan("Crompton", 60);
    f.turnOn();
    f.showInfo();
    Appliance w = new WashingMachine("LG", 300);
    w.turnOn();
    w.showInfo();
  }
}
```

#### Output:-
```java
Fan is Spinning
The brand is Crompton and power is 60 W
Washing Machine is running
The brand is LG and power is 300 W
```

---
### Interface

```java
interface PaymentGateway{
  void processPayment(double amount);
}

class UPIPayment implements PaymentGateway {
  
  @Override
  public void processPayment(double amount){
    System.out.println("Processing ₹amount through UPI "+ amount);
  }
}

class CardPayment implements PaymentGateway{

  @Override
  public void processPayment(double amount){
    System.out.println("Processing ₹amount through Card "+ amount);
  }
}

class CashPayment implements PaymentGateway{

  @Override
  public void processPayment(double amount){
    System.out.println("Received ₹amount in Cash "+amount);
  }
}

public class InterPrac{
  public static void main(String[] Google){
    PaymentGateway payment;
    payment = new UPIPayment();
    payment.processPayment(34000);
    payment = new CardPayment();
    payment.processPayment(5000);
    payment = new CashPayment();
    payment.processPayment(56000);
  }
}
```

#### Output

```java
Processing ₹amount through UPI 34000.0
Processing ₹amount through Card 5000.0
Received ₹amount in Cash 56000.0
```

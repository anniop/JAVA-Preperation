
### 🧠 What is Typecasting?
> **Typecasting** in java means **converting one data type into another**.

Java is **strongly types**, so it doesn't allow mixing of different types without explicit instructions. That's where **typecasting** comes in.
### 🔀 Types of Typecasting in Java
Java has **two** types of typecasting:

| Type      | Also called       | Done how?      |
| --------- | ----------------- | -------------- |
| Widening  | Automatic casting | By java itself |
| Narrowing | Manual casting    | Done by you    |

---
### ✅ 1. Widening (Implicit Casting)
> Converting a **smaller data type to a larger** one automatically;

#### 🧪 Example:
```java
int x = 200;
long y = x; // No error, automatic
float z = y; // Still safe
```
No data loss, no need for extra code -> **safe and automatic**
#### 🔢 Widening Conversion Order:
```java
byte → short → int → long → float → double
         char →↑
```

#### 🧠 Why does it work?
Because Java is sure the new type can **hold more data**, so no risk of overflow or precision loss.

----
### ⚠️ 2. Narrowing (Explicit Casting)
> Converting a **larger data type to a smaller** one **manually**

You have to use **typecasting syntax**:
```java
<targetType> variableName = (<targetType>) source;
```
#### 🧪 Example:
```java
double price = 99.99;
int roundedPrice = (int) price; // Decimal part lost
System.out.println(roundedPrice); // 99
```
#### ⚠️ Possible Issues:
- **Data Loss**
- **Overflow or wrap-around**
```java
int big = 130;
byte b = (byte) big;
System.out.println(b) // ! Output : -126 (overflow)
```
----
### 🧠 Typecasting with Characters
```java
char ch = 'A';
int code = ch; // Widening
System.out.println(code); // 65

int num = 66;
char letter = (char) num; // Narrowing
System.out.println(letter); // 'B'
```
----
### 📥 Typecasting in Input
When using `Scanner`, everything is a **String**, so you often do **parsing**:
```java
Scanner sc = new Scanner(System.in);
int age = Integer.parseInt(sc.nextLine());
double salary = Double.parseDouble(sc.nextLine());
```

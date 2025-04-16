
---
## 🧠 What is Scanner?
> `Scanner` is a **built-in Java class** that allows us to **take input from the user**.

It's part of the package:
```java
java.utils
```
---
## 🔧 Why do we use Scanner?
Because Java doesn't have a direct function like `cin` in C++ or `input()` in Python.
So we use `Scanner` to take inputs like:
- Strings(names, words)
- Integers
- Floats/ Doubles
- Boolean values
- Whole lines
---
## 📦 How to Use Scanner?
### ✅ Step 1: Import the Scanner class
```java
import java.util.Scanner;
```

### ✅ Step 2: Create a Scanner object
```java
Scanner sc = new Scanner(System.in);
```
- `System.in` tells Scanner to take input from **keyboard**.

### ✅ Step 3: Use its methods to take input

| Input type         | Method          | Example                           |
| ------------------ | --------------- | --------------------------------- |
| Integer            | `nextInt()`     | `int age = sc.nextInt();`         |
| Float              | `nextFloat()`   | `float price = sc.nextFloat();`   |
| Double             | `nextDouble()`  | `double pi = sc.nextDouble();`    |
| Long               | `nextLong()`    | `long l = sc.nextLong();`         |
| String ( 1 word)   | `next()`        | `String s = sc.next();`           |
| String (Full line) | `nextLine()`    | `String s = sc.nextLine();`       |
| Boolean            | `nextBoolean()` | `boolean val = sc.nextBoolean();` |

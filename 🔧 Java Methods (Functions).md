## ✅ What is a Method?
> A **method** in java is a **block of code** that performs a specific task.
> It's the Java version of a **function** in other languages.

```java
public int add(int a, int b){
	return a + b;
}
```
---
## 🔨 Why Use Methods?
- Code **reusability**: write once, use many times
- Code **organization**: improves readability
- **Avoids Repetition**
- Used in **modular, object-oriented design**.

-----
## 🧱 Method Syntax

```java
<access_modifier> <return_type> <method_name>(<parameters>){
	// method body
	return value; // if needed
}
```

### Example:
```java
public int multiply(int x, int y){
	return x * y;
}
```

| Part            | Example        | Meaning                |
| --------------- | -------------- | ---------------------- |
| Access Modifier | `public`       | Who can access it      |
| Return Type     | `int`          | What it gives back     |
| Method Name     | `multiply`     | Your method's name     |
| Parameters      | `int x, int y` | Input values           |
| Method Body     | `{ ... }`      | Logic of your function |

-----
## 🔁 Calling a Method

```java
int result = multiply(10, 5); // returns 50
```
- You **call** the method by name
- Pass values as arguments

---

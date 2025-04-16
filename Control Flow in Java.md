
----
Let's break it down into three parts:
1. **Conditional Statements**
	- `if`, `else`, `else if`
2. **Loops**
	- `for`,`while`, `do-while`
----
### 🧠 Why Control Flow?
Control flow allows us to make **decisions** and perform **repetitive tasks** in code.
It's the heart of **logic building**, which is super important for interviews and real-world coding.

----
## `if`, `else if`, and `else` statements in Java

----
### 🧠 What is `if-else`?
> The `if` statement allows your program to **make decisions** and **execute code conditionally** based on a given condition.

----
## 🧾 Syntax

```java
if(condition) {
	// code block if condition is true
} else if (another_condition) {
	// code block if second condition is true
} else {
	// code block if none of the above conditions are true
}
```
-----
## 🔎 Example 1: Check if a number is positive, negative or zero
```java
import java.util.Scanner;

public class CheckNum{
	Scanner sc = new Scanner(System.in);

	System.out.println("Enter Number");
	int num = sc.nextInt();

	if(num > 0){
		System.out.println("The Number is Positive");
	} else if(num < 0) {
		System.out.println("The Number is Negative");
	} else {
		System.out.println("The Number is Zero");
	}

	sc.close();
}
```
----
## 📘 Explanation:

| Code Part           | Meaning                           |
| ------------------- | --------------------------------- |
| `if (num > 0)`      | Check if number is greater than 0 |
| `else if (num < 0)` | If not, check if it's less than 0 |
| `else`              | If neither, then it's exactly 0   |

-------
## 🔁 Comparison Operators

|Operator|Meaning|
|---|---|
|`==`|Equal to|
|`!=`|Not equal to|
|`>`|Greater than|
|`<`|Less than|
|`>=`|Greater than or equal|
|`<=`|Less than or equal|

---
## 🧪 Practice
- Write a program to check if age is:
	- < 18: Minor
	- 18 to 60: Adult
	- 60: Senior Citizen
---
## 🔄 `switch-case` Statement in Java

A cleaner alternative to `if-else-if` chains when checking **one value against multiple constants**

---
### 🧠 What is `switch`?
> The `switch` statement in Java allows you to test the **value of a variable** against a **list of possible cases**.
> If a match is found, the corresponding block is executed.

-----
### 📦 Syntax:

```java
switch (expression) {
	case value1:
		// code block
		break;
	case value2:
		// code block
		break;
	case value3:
		// code block
		break;
	...
	default:
		// default block
}
```
----
### 🔑 Key Points:

- `expression` must evaluate to: `int`, `char`, `String`, `byte`, `short`, or `enum`
- Use `break` to stop checking further cases
- `default` is optional but executes when no match is found

----
### ✅ Example: Days of the Week

```java
import java.util.Scanner;

public class switchCase{
	public static void main(String[] args) {
	Scanner sc = new Scanner(System.in);

	System.out.println("Enter day number (1 to 7): ");
	int num = sc.nextInt();

	switch(num){
		case 1:
			System.out.println("Monday");
			break;

		case 2:
			System.out.println("Tuesday");
			break;

		case 3:
			System.out.println("Wednesday");
			break;

		case 4:
			System.out.println("Thrusday");
			break;

		case 5:
			System.out.println("Friday");
			break;

		case 6:
			System.out.println("Saturday");
			break;

		case 7:
			System.out.println("Sunday");
			break;

		default:
			System.out.println("Enter a Valid number");
	}
	}
}
```

## 🔁 Java Loops

Loops are used to **repeat a block of code** multiple times.

-----
### 🔄 Types of Loops in Java
|Loop Type|Best When You Know…|Syntax Style|
|---|---|---|
|`for` loop|How many times to repeat|Clean & concise|
|`while` loop|Condition to continue is known|Entry-controlled|
|`do-while` loop|You want to run **at least once**|Exit-controlled|

-----
## ✅ 1. `for` Loop

> Best used when you **know the exact number of iterations**
### 📦 Syntax:
```java
for(initialization; condition; update){
	//code block
}
```

### 🧪 Example:
```java
for(int i = 0;i <= 5;i++){
	System.out.println("Jay Ganesh");
}
```
🧠 Output:
```java
Jay Ganesh
Jay Ganesh
Jay Ganesh
Jay Ganesh
Jay Ganesh
```

---

## ✅ 2. `while` Loop

> Best when you **don't know how many times** and want to repeat **as long as condition is true**

### 📦 Syntax:
```java
while(condition){
	// code block
}
```
### 🧪 Example:
```java
int i = 0;
while(i < 5){
	System.out.println("Jay Ganesh");
	i++;
}
```
🧠 Output:
```java
Jay Ganesh
Jay Ganesh
Jay Ganesh
Jay Ganesh
Jay Ganesh
```

---

## ✅ 3. `do-while` Loop

> Best when you **want to execute the code at least once**, even if the condition is false.

### 📦 Syntax:
```java
do {
	// code block
} while (condition);
```

### 🧪 Example:
```java
int i = 0;
do {
	System.out.println("Jay Ganesh");
	i++;
} while(i <= 5);
```

✅ Even if `i = 10`, the loop will run **once** before checking condition.

------
## 🧠 Summary Table
| Loop       | Condition Check  | Runs Minimum | Use When               |
| ---------- | ---------------- | ------------ | ---------------------- |
| `for`      | Before each loop | 0 times      | You know count         |
| `while`    | Before each loop | 0 times      | Condition controlled   |
| `do-while` | After loop body  | 1 time       | Always run once needed |
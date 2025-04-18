
----
## ✅ What is a Constructor?

> A **constructor** is a special method in a class that is **automatically called** when an object is created.

### 🔧 Why use it?
- To **initalize values** of an object **at the time of creation**.
- Cleaner than manually setting values after object creation

----
## 🧪 Constructor Syntax

```java
class ClassName {
	ClassName() {
		// constructor body
	}
}
```
🚨 Note:
- Constructor **name must match the class name**
- Constructors **have no return type**, not even `void`

---
## 🧃 Types of Constructors

|Type|Description|
|---|---|
|**Default Constructor**|No parameters, initializes default values|
|**Parameterized**|Takes arguments, initializes with custom values|
|**Copy Constructor**|Creates a new object by copying values from another one|

----
## 🔹 Default Constructor (Created by Java if you don’t)

```java
class Student {
	String name;
	int rollNo;

	// Default Constructor
	Student(){
		name = "Aniket";
		rollNo = 83;
	}

	void display(){
		System.out.println("Name : "+ name+ "Roll No : " +rollNo);
	}
}

class Main{
	public static void main(String[] Google){
		Student s = new Student();
		s.display();
	}
}
```

---
## 🔸 Parameterized Constructor

```java
class Student {
	String name;
	int rollNo;

	// Parameterized Constructor
	Student(String s, int r){
		name = s;
		rollNo = r;
	}

	void display(){
		System.out.println("Name : "+name+"Roll No : "+rollNo);
	}
}

class Main{
	public static void main(String[] Google){
		Student s = new Student("Aniket", 83); // Initialization
		s.display();
	}
}
```

----
## 🔁 Copy Constructor (Manual in Java)

```java
class Student {
	String name;
	int rollNo;

	// Parameterized Constructor
	Student(String s, int r){
		name = s;
		rollNo = r;
	}

	// Copy Constructor
	Student(Student s){
		this.name = s.name;
		this.rollNo = s.rollNo;
	}

	void display(){
		System.out.println("Name : "+name+"Roll No : "+rollNo);
	}
}

class Main{
	public static void main(String[] Google){
		Student s1 = new Student("Aniket", 83);
		Student s2 = new Student(s1);
		s1.display();
		s2.display();
	}
}
```
----
## 🔑 `this` Keyword

> `this` refers to the **current object** inside a class

#### Used when:
- Field name and parameter name are **same**
- You want to call another constructor (`this()`)
- You want to pass current object as a parameter

-----
## 📌 Notes
- You can **overload constructors** (just like methods)
- Use `this()` to call another constructor from current one
- Use `this.var` to resolve ambiguity between field and parameter names

---
## 🧠 Practice Idea

- Create a `Book` class with title, author
- Add default constructor, parameterized constructor
- Add display method and create 2–3 objects using both constructors

---
```java
class Study {
  String title;
  String author;

  Study(){
    title = "Harry Potter";
    author = "J K Rowling";
  }
  Study(String t, String a){
    title = t;
    author = a;
  }
  void display(){
    System.out.println("Title Of the book " + title + " ,Author: "+ author);
  }
}

public class Book {
  public static void main(String[] Google){
    Study s = new Study();
    Study s1 = new Study("Wings of Fire", "APJ Abdul Kalam");
    Study s2 = new Study("The Subtle art of not giving a Fuck", "Mark Manson");
    s.display();
    s1.display();
    s2.display();
  }
}
```
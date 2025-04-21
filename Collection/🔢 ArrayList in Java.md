
---
## 📦 What is an ArrayList?

> `ArrayList` is a **resizable array** in Java it can grow and shrink **dynamically**, unlike traditional arrays.

🔍 Behind the scenes, it uses an **array internally**, but it **automatically increases size** when needed.

## ✨ Features of `ArrayList`:

| Feature            | Details                                                   |
| ------------------ | --------------------------------------------------------- |
| Dynamic Size       | Grows automatically                                       |
| Maintains order    | Elements are ordered(like an array)                       |
| Allows duplicates  | YES                                                       |
| index-based access | YES                                                       |
| Not thread-safe    | Use `vector` or `Collections.synchronizedList()` for that |

---
## 🧪 Basic Syntax:

```java
import java.util.ArrayList;

public class ArrayLists{
  public static void main(String[] Google){
      ArrayList<String> fruits = new ArrayList<>();

	// Adding Elements
	fruits.add("Apple");
	fruits.add("Banana");
	fruits.add("Mango");

	//Accessing Elements
	System.out.println(fruits.get(1));
    
    // Updating
    fruits.set(1, "Orange");

    // Removing
    fruits.remove("Apple");
    
    // Size 
    System.out.println("Total Fruits : "+ fruits.size());

    //Traversing
    for(String fruit : fruits) {
      System.out.println(fruit);
    }
    }
      
    
}
```
---

## 🛠️ Common Methods of ArrayList

|Method|Description|
|---|---|
|`add(element)`|Adds to the end|
|`add(index, element)`|Inserts at a position|
|`get(index)`|Gets element at index|
|`set(index, element)`|Updates value at index|
|`remove(index)`|Removes by index|
|`remove(object)`|Removes by value|
|`contains(object)`|Checks if exists|
|`size()`|Returns size of list|
|`clear()`|Removes all elements|
|`isEmpty()`|Checks if list is empty|

---
## 🔍 How ArrayList Grows Internally?

- It starts with **default capacity 10**.
- When full, it **creates a new array** with size = `old capacity * 1.5` and **copies elements over**.
- That's why it's fast for **reading**, but a bit **slower for frequent inserts/removes** in middle.

---
## 🔍 Constructors of `ArrayList`

| Constructor               | Description                                 |
| ------------------------- | ------------------------------------------- |
| `ArrayList`               | Default capacity(10)                        |
| `ArrayList(int capacity)` | Creates with given capacity                 |
| `ArrayList(Collection c)` | Creates and copies from existing collection |

---

## 🧠 Time Complexity (Performance)

| Operation    | Time                          |
| ------------ | ----------------------------- |
| Add at end   | O(1) most of the time         |
| Add at index | O(n) because shifting happens |
| Remove       | O(n)                          |
| Get(Index)   | O(1)                          |
| Search       | O(n)                          |

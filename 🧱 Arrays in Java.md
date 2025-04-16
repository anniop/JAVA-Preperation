
----
## 🧠 What is an Array?
> An array is a **fixed-size container** that stores **multiple elements of the same data type** in contiguous memory.

----
## ✅ Why Use Arrays?
- To store multiple values in **one variable**.
- Easy to **traverse, sort,** and **manipulate** data.
- Arrays provide **constant-time access** with index.

----
## 🔹 Types of Arrays in Java
|Type|Description|
|---|---|
|**1D Array**|A linear collection of elements|
|**2D Array**|Array of arrays (rows × columns)|
|**Jagged Array**|2D array with rows of **different lengths**|

----
## 🧾 1️⃣ One-Dimensional Array
```java
int[] nums = new int[5]; // [0, 0, 0, 0, 0]
int[] scores = {90, 85, 75, 60}; // declared with values
```
### Access Elements
```java
System.out.println(scores[0]); // 90
scores[3] = 60; // update index 3
```
### Loop Through Array
```java
for(int i = 0;i < scores.length;i++){
	System.out.println(scores[i]);
}
```
Or use **enhanced for loop**:
```java
for(int  score : scores) {
	System.out.println(scores);
}
```
-------
## 🧾 2️⃣ Two-Dimensional Array (Matrix)
> 2D array = array of arrays(table-like structure)

### Deceleration:
```java
int[][] matrix = new int[4][5]; // 4 rows, 5 columns
```

### Initialization:
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```
### Accessing Elements:
```java
System.out.println(matrix[1][2]); // Output: 6
```
### Looping (Nested Loops):
```java
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```
------
## 🧾 3️⃣ Jagged Array (Irregular Rows)
> A **jagged array** is a 2D array where each row can have **different number of columns**.

### Declaration:
```java
int[][] jagged = new int[3][];
jagged[0] = new int[2]; // row 0 has 2 columns
jagged[1] = new int[4]; // row 1 has 4 columns
jagged[2] = new int[1]; // row 2 has 1 column
```
### Initialization:
```java
int[][] jagged = {
    {1, 2},
    {3, 4, 5, 6},
    {7}
};
```
### Traversing:
```java
for (int i = 0; i < jagged.length; i++) {
    for (int j = 0; j < jagged[i].length; j++) {
        System.out.print(jagged[i][j] + " ");
    }
    System.out.println();
}
```
----
## 🔧 Array Properties & Utilities

| Feature                | Description                                 |
| ---------------------- | ------------------------------------------- |
| `arr.length`           | Gives size of the array(number of elements) |
| `Arrays.sort(arr)`     | Sorts the array                             |
| `Arrays.toString(arr)` | Converts array to readable string           |
### ✨ Example:
```java
import java.util.Arrays;
int[] arr = {4, 1, 3, 2};
Arrays.sort(arr); // [1, 2, 3, 4]
System.out.println(Arrays.toString(arr));
```
----
## ⚠️ Common Mistakes

| Mistake                       | What Happens                            |
| ----------------------------- | --------------------------------------- |
| Accessing index out of bounds | Throws `ArrayIndexOutOfBoundsException` |
| Forgetting `.length`          | You'll get compile-time errors          |
| Using uninitialized arrays    | Can cause `NullPointerException`        |


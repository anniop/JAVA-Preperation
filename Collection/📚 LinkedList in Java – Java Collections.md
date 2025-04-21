
---
## 💡 What is `LinkedList`?
- `LinkedList` is a **data structure** that stores elements **in nodes**.
- Each node has:
	- The **data**
	- A link to the **next node**
	- And in Java's case, a link to the **previous node** too (so it's a **doubly linked list**)

---
## 📦 Where is it in Java?
- Comes from `java.util.LinkedList`
- Implements:
	- `List` (like ArrayList)
	- `Deque` (double-ended queue)
	- `Queue` and `Stack` behaviors too

---
## ⚙️ Internal Working

When you add an element in `LinkedList`, Java creates a node like this:

```java
class Node {
	E data;
	Node next;
	Node prev;
}
```
### Memory Structure:
```csharp
[ null ← A ↔ B ↔ C → null ]
```
So elements are **connected with pointers**, not stored in one array like `ArrayList`

----

## 🔥 Key Features

|Feature|LinkedList|
|---|---|
|Stores order?|✅ Yes (insertion order)|
|Allows duplicates?|✅ Yes|
|Index-based access?|✅ Yes, but slow|
|Internally uses|Nodes (not arrays)|
|Best for|Insert/remove in the middle|
|Not good for|Random access (like `.get(i)`)|
|Thread-safe?|❌ No|

---
## ⚖️ Comparison: `ArrayList` vs `LinkedList`

|Feature|ArrayList|LinkedList|
|---|---|---|
|Internal data|Array|Nodes|
|Add at end|Fast (O(1))|Fast (O(1))|
|Add in middle|Slow (O(n))|Fast (O(1))|
|Get by index|Fast (O(1))|Slow (O(n))|
|Remove in middle|Slow (O(n))|Fast (O(1))|
|Memory used|Less|More (due to pointers)|

---
## 🧠 Time Complexities

|Operation|Time|
|---|---|
|Add First|O(1)|
|Add Last|O(1)|
|Add at index|O(n)|
|Remove First|O(1)|
|Remove Last|O(1)|
|Get(index)|O(n)|
|Search|O(n)|
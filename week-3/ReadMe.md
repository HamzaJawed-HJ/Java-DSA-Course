# 🚀 DSA Lab – Class 3 : Linked List (Scratch Implementation)

🧑‍🏫 **Welcome back!**  
In this lab we’ll build our own Linked List from scratch — no built-in classes — to understand how nodes connect, how data is stored dynamically, and how insertion/deletion works in memory.

---

## 🎯 Lab Objectives
✅ Understand node structure & pointers  
✅ Implement Linked List operations manually  
✅ Learn traversal, insertion, deletion, and size tracking  
✅ Analyze time & space complexity of each operation  

---

# 🧩 1. Introduction to Linked Lists

💡 **Concept**

A **Linked List** is a collection of nodes connected using pointers or references.  
Each node stores **data** and a reference to the next node.

| Arrays | Linked Lists |
| ------- | ------------- |
| Fixed size | Dynamic size |
| Costly insert/delete | Easy insert/delete |
| Stored in contiguous memory | Nodes may exist anywhere in memory |

📘 **Real-Life Analogy**  
Think of a Linked List like a chain of train compartments — every bogie knows where the next one is but doesn’t know the previous one.

```

Head → [Data | Next] → [Data | Next] → null

```

---

# ⚙️ 2. Structure of a Node

💡 **Concept**

Each node holds two things: the data and a reference to the next node.

```java

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

```

🧠 Each `Node` object occupies space in memory and points to the next node’s address.

---

# 🧱 3. Creating a Linked List (Manually)

💡 **Concept**

Let’s create three nodes and link them manually.

```java

Node head = new Node(10);
Node second = new Node(20);
Node third = new Node(30);
head.next = second;
second.next = third;

```

📘 **Visualization**

```
Head → [10|•] → [20|•] → [30|null]
```

🧠 **Practice**
Create and print a 3-node linked list manually using System.out.print statements.

---

# 🧩 4. Scratch Implementation (Important for Beginners)

We’ll now build a custom `LL` class and implement each operation step by step.

---
```java
class LL {


   Node head;
   private int size;


   LL () {
       size = 0;
   }

//Node class with size  
   public class Node {
       String data;
       Node next;


       Node(String data) {
           this.data = data;
           this.next = null;
           size++;
       }
   }

}


```

## 🔹 4.1 addFirst() – Insert at Beginning

💡 Adds a new node at the start and updates `head`.

```java
public void addFirst(String data) {
    Node newNode = new Node(data);
    newNode.next = head;
    head = newNode;
}
```

🖥️ **Example**

```
List: null  
addFirst("this") → this → null  
addFirst("is") → is → this → null
```

⏱️ **Complexity:** Time O(1) | Space O(1)

🧠 **Practice:** Add three elements at the beginning and print the final list.

---

## 🔹 4.2 addLast() – Insert at End

💡 Traverse till the last node and attach the new node.

```java
public void addLast(String data) {
    Node newNode = new Node(data);
    if(head == null) {
        head = newNode;
        return;
    }
    Node lastNode = head;
    while(lastNode.next != null) {
        lastNode = lastNode.next;
    }
    lastNode.next = newNode;
}
```

🖥️ **Example**

```
List: null  
addLast("is") → is → null  
addLast("a") → is → a → null
```

⏱️ **Complexity:** Time O(n) | Space O(1)

🧠 **Practice:** Use `addFirst()` and `addLast()` to build `this → is → a → list`.

---

## 🔹 4.3 printList() – Traversal

💡 Start from `head` and move to `next` until `null`.

```java
public void printList() {
    Node currNode = head;
    while(currNode != null) {
        System.out.print(currNode.data + " -> ");
        currNode = currNode.next;
    }
    System.out.println("null");
}
```

🖥️ **Output**

```
this → is → a → list → null
```

⏱️ **Complexity:** Time O(n) | Space O(1)

---

## 🔹 4.4 removeFirst() – Delete at Beginning

💡 Move `head` to `head.next`. Handles empty list.

```java
public void removeFirst() {
    if(head == null) {
        System.out.println("Empty List, nothing to delete");
        return;
    }
    head = this.head.next;
    size--;
}
```

🖥️ **Example**

```
Before: this → is → a → list  
After: is → a → list
```

⏱️ **Complexity:** Time O(1) | Space O(1)

---

## 🔹 4.5 removeLast() – Delete at End

💡 Traverse to the second-last node and set its `next = null`.

```java
public void removeLast() {
    if(head == null) {
        System.out.println("Empty List, nothing to delete");
        return;
    }
    size--;
    if(head.next == null) {
        head = null;
        return;
    }
    Node currNode = head;
    Node lastNode = head.next;
    while(lastNode.next != null) {
        currNode = currNode.next;
        lastNode = lastNode.next;
    }
    currNode.next = null;
}
```

🖥️ **Example**

```
Before: this → is → a → list  
After: this → is → a
```

⏱️ **Complexity:** Time O(n) | Space O(1)

---

## 🔹 4.6 getSize() – Count Nodes

💡 `size` is maintained during node creation and deletion.

```java
public int getSize() {
    return size;
}
```

🖥️ **Output**

```
Current size: 3
```

⏱️ **Complexity:** Time O(1) | Space O(1)

---

## 🔹 4.7 main() – Demo of All Methods

💻 **Complete Code**

```java
public static void main(String args[]) {
    LL list = new LL();
    list.addLast("is");
    list.addLast("a");
    list.addLast("list");
    list.printList();

    list.addFirst("this");
    list.printList();
    System.out.println(list.getSize()); 

    list.removeFirst();
    list.printList();

    list.removeLast();
    list.printList();
}
```

🖥️ **Output**

```
is -> a -> list -> null
this -> is -> a -> list -> null
4
is -> a -> list -> null
is -> a -> null
```

✅ **Summary**

| Operation     | Time | Space |
| ------------- | ---- | ----- |
| addFirst()    | O(1) | O(1)  |
| addLast()     | O(n) | O(1)  |
| removeFirst() | O(1) | O(1)  |
| removeLast()  | O(n) | O(1)  |
| printList()   | O(n) | O(1)  |
| getSize()     | O(1) | O(1)  |

---

## 🧠 Practice Zone

1️⃣ Build a list → `this → is → a → simple → list`
2️⃣ Remove first & last elements.
3️⃣ Print final list and size.

Expected Output:

```
is → a → simple → null  
Size = 3
```

---

## 🎨 Visualization (Optional)

```
Head → [this|•] → [is|•] → [a|•] → null
```

---

# 🧩 5. Mini Challenge Section (Custom Functions – Your Own Linked List)

Now let’s power up your custom `LL` class with real challenges 🔥  
We’ll extend your Linked List to perform **search** and **conditional deletion** — manually, without using Java’s built-in `LinkedList`.

---

## 🔹 Challenge 1 – Search Element in Custom Linked List

💡 **Problem Statement**

Make a Linked List & add the following elements:  
`(1, 5, 7, 3, 8, 2, 3)`  
Then search for the number **7** and display its **index position** (starting from 0).

---

💻 **Code Implementation**

```java
public class LL {

    Node head;
    private int size;

    LL() { size = 0; }

    public class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
            size++;
        }
    }

    // Add at end
    public void addLast(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node curr = head;
        while (curr.next != null) {
            curr = curr.next;
        }
        curr.next = newNode;
    }

    // Print the list
    public void printList() {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " -> ");
            curr = curr.next;
        }
        System.out.println("null");
    }

    // 🔍 Custom Search Function
    public int searchElement(int value) {
        Node curr = head;
        int index = 0;
        while (curr != null) {
            if (curr.data == value)
                return index;
            curr = curr.next;
            index++;
        }
        return -1; // not found
    }

    public static void main(String[] args) {
        LL list = new LL();
        int[] arr = {1, 5, 7, 3, 8, 2, 3};

        for (int n : arr)
            list.addLast(n);

        System.out.print("Linked List: ");
        list.printList();

        int value = 7;
        int index = list.searchElement(value);

        if (index != -1)
            System.out.println("Element " + value + " found at index: " + index);
        else
            System.out.println("Element not found in list.");
    }
}
```

---

🖥️ **Output**

```
Linked List: 1 -> 5 -> 7 -> 3 -> 8 -> 2 -> 3 -> null
Element 7 found at index: 2
```

⏱️ **Complexity**

* Time Complexity: **O(n)** (traverses list once)
* Space Complexity: **O(1)**

🧠 **Practice**

* Modify to take input from user instead of hardcoding values.
* Try searching for a value that doesn’t exist (to test your return condition).

---

## 🔹 Challenge 2 – Delete Nodes Greater Than 25

💡 **Problem Statement**

Take integers as input in your Linked List.
Then delete all nodes that have values **greater than 25** using your own function.

---

💻 **Code Implementation**

```java
import java.util.*;

public class LL {

    Node head;
    private int size;

    LL() { size = 0; }

    public class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
            size++;
        }
    }

    // Add at end
    public void addLast(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node curr = head;
        while (curr.next != null) {
            curr = curr.next;
        }
        curr.next = newNode;
    }

    // Print list
    public void printList() {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " -> ");
            curr = curr.next;
        }
        System.out.println("null");
    }

    // 🧹 Custom Function: deleteGreaterThan(limit)
    public void deleteGreaterThan(int limit) {
        while (head != null && head.data > limit) {
            head = head.next;
            size--;
        }

        Node curr = head;
        while (curr != null && curr.next != null) {
            if (curr.next.data > limit) {
                curr.next = curr.next.next;
                size--;
            } else {
                curr = curr.next;
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        LL list = new LL();

        System.out.print("Enter size of list: ");
        int n = sc.nextInt();

        System.out.println("Enter " + n + " elements:");
        for (int i = 0; i < n; i++) {
            list.addLast(sc.nextInt());
        }

        System.out.print("\nOriginal List: ");
        list.printList();

        list.deleteGreaterThan(25);

        System.out.print("Updated List (after deleting >25): ");
        list.printList();
    }
}
```

---

🖥️ **Example Output**

```
Enter size of list: 6
Enter 6 elements:
10 45 7 30 22 5

Original List: 10 -> 45 -> 7 -> 30 -> 22 -> 5 -> null
Updated List (after deleting >25): 10 -> 7 -> 22 -> 5 -> null
```

⏱️ **Complexity**

* Time Complexity: **O(n)**
* Space Complexity: **O(1)**

🧠 **Practice**

* Change the condition to delete nodes **less than 10** instead.
* Try a limit of **even numbers only** (e.g., delete all even nodes).

---

## 🎯 Summary of Mini Challenges

| Operation                  | Description                     | Time | Space |
| -------------------------- | ------------------------------- | ---- | ----- |
| `searchElement(value)`     | Returns index of target         | O(n) | O(1)  |
| `deleteGreaterThan(limit)` | Deletes nodes with data > limit | O(n) | O(1)  |





---

# 🧩 5. Mini Challenge Section(builten Funtion)

Let’s put your Linked List knowledge into action with two hands-on problems 💪

---

## 🔹 Challenge 1 – Search an Element in Linked List

💡 **Problem Statement**

Create a Linked List and add the following elements:  
`(1, 5, 7, 3, 8, 2, 3)`  
Then search for the number **7** and display its **index position**.

💻 **Example Code**

```java
import java.util.*;

public class SearchLinkedList {
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();

        // Adding elements
        list.add(1);
        list.add(5);
        list.add(7);
        list.add(3);
        list.add(8);
        list.add(2);
        list.add(3);

        System.out.println("Linked List: " + list);

        int searchValue = 7;
        int index = list.indexOf(searchValue);

        if (index != -1) {
            System.out.println("Element " + searchValue + " found at index: " + index);
        } else {
            System.out.println("Element not found in the list.");
        }
    }
}
```

🖥️ **Output**

```
Linked List: [1, 5, 7, 3, 8, 2, 3]
Element 7 found at index: 2
```

⏱️ **Complexity**

* Time Complexity: **O(n)** (must traverse list to find element)
* Space Complexity: **O(1)** (no extra space used)

🧠 **Practice**
Try modifying the program to:

* Take the element to search from user input
* Return “Element not found” if it doesn’t exist

---

## 🔹 Challenge 2 – Delete Nodes Greater Than 25

💡 **Problem Statement**

Take elements (numbers in range 1–50) of a Linked List as input from the user.
Then delete all nodes which have **values greater than 25**.

💻 **Example Code**

```java
import java.util.*;

public class DeleteGreaterThan25 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        LinkedList<Integer> list = new LinkedList<>();

        System.out.print("Enter size of list: ");
        int size = sc.nextInt();

        System.out.println("Enter " + size + " elements (1–50):");
        for (int i = 0; i < size; i++) {
            int num = sc.nextInt();
            list.add(num);
        }

        System.out.println("\nOriginal List: " + list);

        // Remove numbers greater than 25
        list.removeIf(n -> n > 25);

        System.out.println("Updated List (after deleting >25): " + list);
    }
}
```

🖥️ **Sample Run**

```
Enter size of list: 6
Enter 6 elements (1–50):
10 45 7 30 22 5

Original List: [10, 45, 7, 30, 22, 5]
Updated List (after deleting >25): [10, 7, 22, 5]
```

⏱️ **Complexity**

* Time Complexity: **O(n)** (each node checked once)
* Space Complexity: **O(1)** (no additional structures used)


🧠 **Practice**

* Modify code to remove all **even numbers** instead.
* Try writing your own method `removeIfGreaterThan(list, 25)` using a loop instead of `removeIf()`.

---

## 🎓 Wrap-Up

✅ Understood internal working of Linked Lists
✅ Implemented insertion & deletion manually
✅ Learned traversal and size tracking
✅ Analyzed time & space complexity for every operation


---


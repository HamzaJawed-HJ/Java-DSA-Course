
# 🧱 **DSA Lab – Class 5 : Stack (Array + Linked List Implementation)**

---

## 🚀 Let’s Begin!

Welcome back, developers!
In this lab, we’re diving into one of the most powerful linear data structures — the **Stack** 🧠

Stacks follow the principle of **LIFO (Last In, First Out)** — just like a stack of plates 🍽️ — the last plate placed on top is the first one to be removed.

---

## 💡 Explanation

A **Stack** allows three main operations:

1. **Push** → Add an element to the top.
2. **Pop** → Remove the top element.
3. **Peek** → View the top element without removing it.

Think of it like:

* **Pushing** a new plate on the stack.
* **Popping** the top plate when you need it.
* **Peeking** to just check what’s on top.

---

## ⚙️ Time & Space Complexity

| Operation      | Time                    | Space |
| -------------- | ----------------------- | ----- |
| Push           | O(1)                    | O(n)  |
| Pop            | O(1)                    | O(n)  |
| Peek           | O(1)                    | O(1)  |
| Resize (Array) | O(n) but amortized O(1) | O(n)  |


---

## Visualization
![Array Stack](assets/1.webp)

---


# 🧱 **Part 1: Stack Using Dynamic Array**

---

## 💡 Idea

We’ll create a **Stack** using an **Array**.
Normally, arrays have a fixed size — but here, we’ll make it **dynamic**.
When the stack becomes full, we’ll **double its size automatically!** ⚡

---

## 🧩 Pseudocode (in Simple English)

```
function push(value)
    if stack is full
        call resize() to double the array length
    move top pointer ahead
    insert value at top position

function pop()
    if stack is empty
        show "Stack Underflow"
    else
        remove element from top
        move top pointer one step back

function peek()
    if stack is empty
        show "Stack is Empty"
    else
        display element at top

function resize()
    create new array with double size
    copy all old elements to new array
    assign new array as stack

function isEmpty()
    return true if top == -1

function printStack()
    print all elements from top to bottom
```

---

## 💻 Example Code (Java)

```java
class StackArray {
    private int[] stack;
    private int top;

    // constructor
    public StackArray(int size) {
        stack = new int[size];
        top = -1;
    }

    // push
    public void push(int value) {
        if (top == stack.length - 1) {
            resize();
        }
        top++;
        stack[top] = value;

        System.out.println(value + " pushed to stack");                           // stack[++top] =value;    
    }

    // pop
    public int pop(){

        if(isEmpty()){
           return -1;
        }
        int removed= stack[top];
        top--;
        return removed;
    }


    // peek
    public int peek() {
        if (isEmpty()) {
         return -1;
        }
        return stack[top];
    }

    // resize function
    private void resize() {
        int newSize = stack.length * 2;
        int[] newStack = new int[newSize];
        for (int i = 0; i < stack.length; i++) {
            newStack[i] = stack[i];
        }
        stack = newStack;
        System.out.println("Stack size doubled to " + newSize);
    }

    // check empty
    public boolean isEmpty() {
        return top == -1;
    }

    // print stack
    public void printStack() {
        System.out.print("Stack elements: ");
        for (int i = top; i >= 0; i--) {
            System.out.print(stack[i] + " ");
        }
        System.out.println();
    }
}
```

---

## 🧠 Dry Run Example

| Step | Operation                    | Stack Content                     | Top |
| ---- | ---------------------------- | --------------------------------- | --- |
| 1    | push(10)                     | [10]                              | 0   |
| 2    | push(20)                     | [10, 20]                          | 1   |
| 3    | push(30)                     | [10, 20, 30]                      | 2   |
| 4    | pop()                        | [10, 20]                          | 1   |
| 5    | push(40), push(50), push(60) | triggers resize() → doubles array | 5   |

---

## 🖥 Output

```
10 pushed to stack
20 pushed to stack
30 pushed to stack
30 popped from stack
40 pushed to stack
50 pushed to stack
60 pushed to stack
Stack size doubled to 6
Top element: 60
Stack elements: 60 50 40 20 10
```

---

---

## Visualization
![LinkList Stack](assets/2.png)

---


# 🌿 **Part 2: Stack Using Linked List**

---

## 💡 Idea

The **Linked List Stack** removes the limitation of fixed size.
Each new node is dynamically created and linked at the **top**.

---

## 🧩 Pseudocode (in Simple English)

```
function push(value)
    create new node
    new node.next = top
    top = new node

function pop()
    if stack is empty
        show "Underflow"
    else
        temp = top
        top = top.next
        delete temp

function peek()
    if stack is empty
        show "Empty"
    else
        display top.data

function isEmpty()
    return true if top == null

function printStack()
    start from top node
    print data till end
```

---

## 💻 Example Code (Java)

```java
class StackLinkedList {
    private Node top;

    public class Node {
        int data;
        Node next;

        Node(int data){
            this.data = data;
            this.next=null;
        }
    }

    // push
    public void push(int value) {
        
        Node newNode = new Node(value);
        
        newNode.next = top;
        top = newNode;
        System.out.println(value + " pushed to stack");
    }

    // pop
     public int pop() {
            if(isEmpty()) {
                return -1;
            }
            Node temp = top;
            top = top.next;

            return temp.data;
        }

    // peek
    public int peek(){
            if (isEmpty()) {
                return -1;
                }

            return top.data;
    }

    // check empty
    public boolean isEmpty() {
        return top == null;
    }

    // print stack
    public void printStack() {
        Node current = top;
        System.out.print("Stack elements: ");
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }

    //another print function 
    public void printStack2(){
        while(!isEmpty()) {

            System.out.println(peek());

            pop();
        }
    }

}

```

---

## 🧠 Dry Run Example

| Step | Operation | Stack (Top → Bottom) |
| ---- | --------- | -------------------- |
| 1    | push(10)  | 10                   |
| 2    | push(20)  | 20 → 10              |
| 3    | push(30)  | 30 → 20 → 10         |
| 4    | pop()     | 20 → 10              |
| 5    | push(40)  | 40 → 20 → 10         |

---

## 🖥 Output

```
10 pushed to stack
20 pushed to stack
30 pushed to stack
30 popped from stack
40 pushed to stack
Top element: 40
Stack elements: 40 20 10
```

---

# ⚖️ **Comparison Table**

| Feature        | Array Stack (Dynamic)     | Linked List Stack         |
| -------------- | ------------------------- | ------------------------- |
| Memory         | Fixed (resized when full) | Fully dynamic             |
| Speed          | Slightly faster           | Slightly slower           |
| Implementation | Easier                    | Uses extra pointer memory |
| Overflow       | Possible before resizing  | Never happens             |
| Underflow      | Possible                  | Possible                  |

---

# 💼 **Real-World Applications**

✅ Undo/Redo operations in text editors
✅ Browser back/forward functionality
✅ Function call stacks in recursion
✅ Expression evaluation (prefix/postfix)

---

# 🧩 **Mini Practice Challenge Zone**

Let’s add a few **hands-on exercises** to strengthen your stack logic and help you practice custom operations like traversal using `pop()` and `peek()`.

---

## 🧮 **1. Find Maximum Element in Stack**

### 💡 Idea:

We’ll pop all elements one by one, track the largest, and stop when the stack becomes empty.

### 💻 Code Snippet

```java
public int findMax() {
    if (isEmpty()) return -1;

    int max = peek();
    while (!isEmpty()) {
        int value = pop();
        if (value > max)
            max = value;
    }
    return max;
}
```

### 🧠 Example

```
Stack: [40, 20, 50, 10]
Output → Maximum = 50
```

---

## ➕ **2. Find Sum of All Elements**

### 💡 Idea:

Use `pop()` repeatedly to remove and sum all elements.

### 💻 Code Snippet

```java
public int findSum() {
    int sum = 0;
    while (!isEmpty()) {
        sum += pop();
    }
    return sum;
}
```

### 🧠 Example

```
Stack: [10, 20, 30]
Output → Sum = 60
```

---

## 📊 **3. Find Average of Stack Elements**

### 💡 Idea:

We’ll use both `sum` and `count` while popping elements.

### 💻 Code Snippet

```java
public double findAverage() {
    if (isEmpty()) return 0;

    int sum = 0, count = 0;
    while (!isEmpty()) {
        sum += pop();
        count++;
    }
    return (double) sum / count;
}
```

### 🧠 Example

```
Stack: [10, 20, 30]
Output → Average = 20.0
```

---

## 🔁 **4. Reverse Stack (Using Another Temporary Stack)**

### 💡 Idea:

Push all popped elements into another stack — the order reverses naturally.

### 💻 Code Snippet

```java
public StackLinkedList reverseStack() {
    StackLinkedList temp = new StackLinkedList();
    while (!isEmpty()) {
        temp.push(pop());
    }
    return temp;
}
```

### 🧠 Example

```
Stack: [10, 20, 30]
Reversed → [30, 20, 10]
```

---

## 💪 **5. Check if Stack is Palindrome**

### 💡 Idea:

Copy elements, then compare original order vs reversed order.

### 💻 Code Snippet

```java
public boolean isPalindrome() {
    StackLinkedList copy = new StackLinkedList();
    StackLinkedList temp = new StackLinkedList();

    Node current = top;
    while (current != null) {
        copy.push(current.data);
        temp.push(current.data);
        current = current.next;
    }

    StackLinkedList reversed = temp.reverseStack();

    while (!copy.isEmpty() && !reversed.isEmpty()) {
        if (copy.pop() != reversed.pop()) return false;
    }
    return true;
}
```

### 🧠 Example

```
Stack: [1, 2, 3, 2, 1]
Output → Palindrome = true
```

---
## 🧩 Summary Table

| Task             | Function Name    | Key Operation Used |
| ---------------- | ---------------- | ------------------ |
| Find Maximum     | `findMax()`      | pop + compare      |
| Find Sum         | `findSum()`      | pop + sum          |
| Find Average     | `findAverage()`  | pop + divide       |
| Reverse Stack    | `reverseStack()` | push + pop         |
| Check Palindrome | `isPalindrome()` | copy + reverse     |

---

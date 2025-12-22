Week 13 – BST
# 🌳 **DSA Lab – Week 13 : Trees & Binary Search Trees (BST)**

🧑‍🏫 **Instructor:** Hamza Jawed
📚 **Course:** Data Structures & Algorithms
🧪 **Lab Focus:** Understanding Trees, Binary Trees, and Binary Search Trees from scratch

---

## 🎯 **Lab Objectives**

✅ Understand tree terminology and structure
✅ Learn Binary Tree basics
✅ Implement and understand tree traversals
✅ Understand Binary Search Tree (BST) properties
✅ Perform BST operations: insert, search, delete
✅ Analyze time & space complexity

---

# 🧩 **1. Introduction to Trees**

💡 **Concept**

A **Tree** is a **non-linear data structure** used to represent hierarchical data.
It consists of **nodes** connected by **edges**.

Unlike arrays or linked lists, trees allow:

* Faster searching
* Hierarchical representation
* Efficient insertion and deletion

---

## 🌲 **Tree Terminology**

| Term     | Meaning                        |
| -------- | ------------------------------ |
| Root     | Top-most node                  |
| Parent   | Node that has children         |
| Child    | Node connected below a parent  |
| Leaf     | Node with no children          |
| Siblings | Nodes with same parent         |
| Height   | Longest path from root to leaf |
| Level    | Distance from root             |
| Subtree  | Tree inside a tree             |

---

### 📘 Example Diagram

```
        10
       /  \
      5    20
```

---

# 🌲 **2. Binary Tree**

💡 **Concept**

A **Binary Tree** is a tree where **each node has at most two children**:

* Left child
* Right child

---

## 🔹 Types of Binary Trees

1️⃣ **Full Binary Tree** – 0 or 2 children
2️⃣ **Complete Binary Tree** – Filled level-wise
3️⃣ **Perfect Binary Tree** – All levels completely filled

---

# ⚙️ **3. Node Structure (Java)**

```java
class Node {
    int data;
    Node left;
    Node right;

    Node(int data) {
        this.data = data;
        left = right = null;
    }
}
```

🧠 Each node stores:

* Data
* Reference to left child
* Reference to right child

---

# 🔄 **4. Tree Traversals (Very Important)**

Traversal means **visiting every node exactly once**.

---

## 🔹 4.1 Inorder Traversal (L → N → R)

💡 Used in BST to get **sorted output**.

```java
void inorder(Node root) {
    if(root == null) return;
    inorder(root.left);
    System.out.print(root.data + " ");
    inorder(root.right);
}
```

---

## 🔹 4.2 Preorder Traversal (N → L → R)

💡 Used to **copy or serialize a tree**.

```java
void preorder(Node root) {
    if(root == null) return;
    System.out.print(root.data + " ");
    preorder(root.left);
    preorder(root.right);
}
```

---

## 🔹 4.3 Postorder Traversal (L → R → N)

💡 Used for **deleting/freeing a tree**.

```java
void postorder(Node root) {
    if(root == null) return;
    postorder(root.left);
    postorder(root.right);
    System.out.print(root.data + " ");
}
```

---


# 🌳 **5. Binary Search Tree (BST)**

💡 **Concept**

A **BST** is a binary tree with a special rule:

```
Left Subtree  <  Root  <  Right Subtree
```

This property allows **fast searching**.

---

### 📘 Example BST

```
        50
       /  \
     30    70
    / \    / \
  20 40  60 80
```

---

# ✏️ **6. BST Operations**

---

## 🔹 6.1 Insert in BST

```java
Node insert(Node root, int val) {
    if(root == null) return new Node(val);

    if(val < root.data)
        root.left = insert(root.left, val);
    else
        root.right = insert(root.right, val);

    return root;
}
```

---

## 🔹 6.2 Search in BST

```java
boolean search(Node root, int key) {
    if(root == null) return false;
    if(root.data == key) return true;

    if(key < root.data)
        return search(root.left, key);
    else
        return search(root.right, key);
}
```

---

## 🔹 6.3 Find Minimum & Maximum

```java
int findMin(Node root) {
    while(root.left != null)
        root = root.left;
    return root.data;
}

int findMax(Node root) {
    while(root.right != null)
        root = root.right;
    return root.data;
}
```

---

## 🔹 6.4 Delete in BST (3 Cases)

💡 **Cases**
1️⃣ Leaf node
2️⃣ Node with one child
3️⃣ Node with two children

```java
Node delete(Node root, int key) {
    if(root == null) return null;

    if(key < root.data)
        root.left = delete(root.left, key);
    else if(key > root.data)
        root.right = delete(root.right, key);
    else {
        if(root.left == null) return root.right;
        if(root.right == null) return root.left;

        root.data = findMin(root.right);
        root.right = delete(root.right, root.data);
    }
    return root;
}
```

---

# 📊 **7. Time & Space Complexity**

| Operation | Average  | Worst |
| --------- | -------- | ----- |
| Insert    | O(log n) | O(n)  |
| Search    | O(log n) | O(n)  |
| Delete    | O(log n) | O(n)  |
| Traversal | O(n)     | O(n)  |


---

# 🧠 **8. Practice Questions**

1️⃣ Insert `{5,1,3,4,2}` and draw BST
2️⃣ Print inorder traversal
3️⃣ Search element recursively
4️⃣ Count leaf nodes
5️⃣ Find height of tree
6️⃣ Check if a tree is a valid BST
7️⃣ Find min & max
8️⃣ Delete a node and print tree

---

# 🧩 **9. Mini Challenge**

```
Insert: 50, 30, 70, 20, 40, 60, 80
```

### Tasks:

* Print inorder traversal
* Delete node `30`
* Search `60`
* Find height

Expected inorder:

```
20 40 50 60 70 80
```

---

# 🎓 **Wrap-Up**

✅ Learned tree structure & terminology
✅ Understood binary trees and types
✅ Implemented all tree traversals
✅ Built and operated Binary Search Tree
✅ Analyzed complexity and edge cases


---

### 🔹 **Complete Java Program**

```java
import java.util.*;

class Node {
    int data;
    Node left, right;

    Node(int data) {
        this.data = data;
        left = right = null;
    }
}

public class Main {

    // 🔹 Insert into BST
    static Node insert(Node root, int val) {
        if (root == null) {
            return new Node(val);
        }

        if (val < root.data)
            root.left = insert(root.left, val);
        else
            root.right = insert(root.right, val);

        return root;
    }

    // 🔹 Inorder Traversal
    static void inorder(Node root) {
        if (root == null) return;
        inorder(root.left);
        System.out.print(root.data + " ");
        inorder(root.right);
    }

    // 🔹 Preorder Traversal
    static void preorder(Node root) {
        if (root == null) return;
        System.out.print(root.data + " ");
        preorder(root.left);
        preorder(root.right);
    }

    // 🔹 Postorder Traversal
    static void postorder(Node root) {
        if (root == null) return;
        postorder(root.left);
        postorder(root.right);
        System.out.print(root.data + " ");
    }

    // 🔹 Search in BST
    static boolean search(Node root, int key) {
        if (root == null) return false;
        if (root.data == key) return true;

        if (key < root.data)
            return search(root.left, key);
        else
            return search(root.right, key);
    }

    // 🔹 Find Minimum
    static int findMin(Node root) {
        while (root.left != null)
            root = root.left;
        return root.data;
    }

    // 🔹 Height of Tree
    static int height(Node root) {
        if (root == null) return 0;
        return 1 + Math.max(height(root.left), height(root.right));
    }

    // 🔹 MAIN METHOD
    public static void main(String[] args) {

        Node root = null;

        // 📌 Insert elements
        int[] values = {50, 30, 70, 20, 40, 60, 80};

        for (int val : values) {
            root = insert(root, val);
        }

        // 📌 Traversals
        System.out.print("Inorder Traversal: ");
        inorder(root);
        System.out.println();

        System.out.print("Preorder Traversal: ");
        preorder(root);
        System.out.println();

        System.out.print("Postorder Traversal: ");
        postorder(root);
        System.out.println();

        // 📌 Search
        int key = 60;
        System.out.println("Search " + key + ": " + search(root, key));

        // 📌 Delete
        System.out.println("Deleting 30...");
        root = delete(root, 30);

        System.out.print("Inorder After Deletion: ");
        inorder(root);
        System.out.println();

        // 📌 Height
        System.out.println("Height of Tree: " + height(root));
    }
}
```

---

## 🧠 ** Lab Summary**

### 🔹 Step 1: Start with `Node`

* Each node stores **data, left, right**
* Constructor initializes children as `null`

### 🔹 Step 2: Insert Logic

* Smaller → left
* Greater → right
* Recursive insertion

### 🔹 Step 3: Traversals

* **Inorder** → Sorted output
* **Preorder** → Root first
* **Postorder** → Root last

### 🔹 Step 4: Search

* Uses BST property
* Eliminates half tree each time

---

## 🎯 **Lab Output Example**

```
Inorder Traversal: 20 30 40 50 60 70 80
Preorder Traversal: 50 30 20 40 70 60 80
Postorder Traversal: 20 40 30 60 80 70 50
Search 60: true
Deleting 30...
Inorder After Deletion: 20 40 50 60 70 80
Height of Tree: 3
```



# 🌳 Binary Search Tree (BST) – Iterative Implementation (All Functions)

---

## 🔹 Node Structure

```java
class Node {
    int value;
    Node leftChild;
    Node rightChild;

    Node(int value) {
        this.value = value;
        leftChild = null;
        rightChild = null;
    }
}
```

---

## 🔹 BST Class Skeleton

```java
class BST {
    private Node root;
```

---

## 1️⃣ INSERT (Iterative)

```java
public void insert(int value) {

    if (root == null) {          // Empty BST
        root = new Node(value);
        return;
    }

    Node current = root;

    while (true) {

        if (value < current.value) {
            if (current.leftChild == null) {
                current.leftChild = new Node(value);
                break;
            }
            current = current.leftChild;
        }

        else {
            if (current.rightChild == null) {
                current.rightChild = new Node(value);
                break;
            }
            current = current.rightChild;
        }
    }
}
```

⏱ **Time Complexity:**

* Average → `O(log n)`
* Worst → `O(n)`

---

## 2️⃣ SEARCH (Iterative)

```java
public boolean search(int value) {

    Node current = root;

    while (current != null) {

        if (value == current.value)
            return true;

        if (value < current.value)
            current = current.leftChild;
        else
            current = current.rightChild;
    }

    return false;
}
```

⏱ **Time Complexity:**

* Average → `O(log n)`
* Worst → `O(n)`

---

## 🧪 MAIN METHOD (Testing)

```java
public static void main(String[] args) {

    BST tree = new BST();

    tree.insert(50);
    tree.insert(30);
    tree.insert(70);
    tree.insert(20);
    tree.insert(40);
    tree.insert(60);
    tree.insert(90);

    System.out.print("Inorder: ");
    tree.inorder();

    System.out.print("\nPreorder: ");
    tree.preorder();

    System.out.print("\nPostorder: ");
    tree.postorder();

    System.out.println("\nSearch 40: " + tree.search(40));
    System.out.println("Min: " + tree.findMin());
    System.out.println("Max: " + tree.findMax());
    System.out.println("Height: " + tree.height());

    tree.delete(70);

    System.out.print("After Deletion (Inorder): ");
    tree.inorder();
}
```

---

## ✅ Summary Table

| Operation  | Approach  | Time     |
| ---------- | --------- | -------- |
| Insert     | Iterative | O(log n) |
| Search     | Iterative | O(log n) |
| Delete     | Iterative | O(log n) |
| Traversals | Iterative | O(n)     |
| Height     | Iterative | O(n)     |
| Min / Max  | Iterative | O(log n) |

---
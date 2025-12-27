Week 14 – HashMaps

# 🌳 DSA Lab – Week 14  
## Advanced Binary Search Tree (BST) – Recursive Approach

🧑‍🏫 **Instructor:** Hamza Jawed  
📘 **Focus:** Concept clarity, recursion mastery  

---

## 🚀 Why This Lab Is Important?

This lab tests **real understanding** of Binary Search Trees.

✔ Frequently asked in exams  
✔ Most common viva questions  
✔ Builds strong recursion logic  

---

## 🎯 Learning Outcomes

After this lab, students will be able to:

✅ Delete nodes from BST (ALL 3 cases)  
✅ Count total nodes and leaf nodes  
✅ Validate whether a tree is a BST  
✅ Perform Level Order Traversal  
✅ Think recursively like a pro  

---

# 🧱 1. BST Node Structure

Every BST is built using **nodes**.

```java
class Node {
    int value;
    Node left, right;

    Node(int value) {
        this.value = value;
        left = right = null;
    }
}
```


📌 Each node:

* Stores a value
* Has a left child (smaller values)
* Has a right child (greater values)

---

# 🌳 2. BST Class Skeleton

```java
class BST {
    private Node root;
}
```

The `root` node is the **entry point** of the tree.

---

# ➕ 3. Insert in BST (Recursive)

### 💡 Concept

* Smaller values → left subtree
* Greater values → right subtree
* Recursively move until a `null` spot is found

### 💻 Code

```java
public void insert(int value) {
    root = insertRec(root, value);
}

private Node insertRec(Node root, int value) {
    if (root == null)
        return new Node(value);

    if (value < root.value)
        root.left = insertRec(root.left, value);
    else
        root.right = insertRec(root.right, value);

    return root;
}
```

⏱ **Time Complexity:** O(h)
📦 **Space Complexity:** O(h) (recursion stack)

---

# 🔍 4. Search in BST (Recursive)

```java
public boolean search(int value) {
    return searchRec(root, value);
}

private boolean searchRec(Node root, int value) {
    if (root == null)
        return false;

    if (root.value == value)
        return true;

    if (value < root.value)
        return searchRec(root.left, value);
    else
        return searchRec(root.right, value);
}
```

📌 **Exam Tip:**
BST search is **faster than array search** when tree is balanced.

---

# ❌ 5. Delete in BST (MOST IMPORTANT)

### 📌 Why Deletion Is Hard?

Because we must **preserve BST property** after deletion.

---


## 🔥 BST Delete – Three Mandatory Cases

Whenever you delete a node in BST, it will fall into **ONE of these cases**:

---

## 🟢 **Case 1: Delete a Leaf Node**

📌 **Definition**
A node with **no children**.

### 💡 Idea

Just remove the node — no rearrangement needed.

### 📘 Visualization

```
      50
     /  \
   30    70
          \
           80   ← delete this
```

After deletion:

```
      50
     /  \
   30    70
```

📌 **Why easy?**

* No child to manage
* Parent simply points to `null`

---

## 🟡 **Case 2: Delete a Node with ONE Child**

📌 **Definition**
Node has **only left OR only right child**.

### 💡 Idea

Parent directly connects to the child.

### 📘 Visualization

```
      50
        \
         70
           \
            80   ← delete 70
```

After deletion:

```
      50
        \
         80
```

📌 **Key Concept**

* Node is bypassed
* Child replaces the deleted node

---

## 🔴 **Case 3: Delete a Node with TWO Children (MOST IMPORTANT)**

⚠️ **This is the hardest and most asked case**

### 💡 Idea

1. Find **Inorder Successor** (smallest in right subtree)
2. Copy its value to the node
3. Delete the successor

---

### 📘 Visualization

```
          50
         /  \
       30    70
            /  \
          60    80
```

Delete `50`

➡️ Inorder Successor = **60**

After replacement:

```
          60
         /  \
       30    70
               \
                80
```

📌 **Why not predecessor?**

* Successor is easier to find
* No BST rule violation

---

## 💻 BST Delete Code (Recursive – All 3 Cases)

```java
public void delete(int value) {
    root = deleteRec(root, value);
}

private Node deleteRec(Node root, int value) {
    if (root == null)
        return null;

    if (value < root.value) {
        root.left = deleteRec(root.left, value);
    }
    else if (value > root.value) {
        root.right = deleteRec(root.right, value);
    }
    else {
        // Case 1: No child
        if (root.left == null && root.right == null)
            return null;

        // Case 2: One child
        if (root.left == null)
            return root.right;
        if (root.right == null)
            return root.left;

        // Case 3: Two children
        int successorValue = findMin(root.right);
        root.value = successorValue;
        root.right = deleteRec(root.right, successorValue);
    }
    return root;
}
```

---

## 🔽 Inorder Successor (Minimum Value)

```java
private int findMin(Node root) {
    if (root.left == null)
        return root.value;
    return findMin(root.left);
}
```

---

# 🔢 6. Count Total Nodes (Recursive)

📌 **Why teach this?**

* Strengthens traversal logic
* Helps students understand recursive/iterative movement

### 💡 Logic

* Visit every node
* Increment counter

### 📘 Visualization

```
      10
     /  \
    5   20
```

➡️ Total Nodes = **3**

📌 **Time Complexity:** `O(n)`
📌 **Space Complexity:** `O(h)`

---

```java
public int countNodes() {
    return countNodesRec(root);
}

private int countNodesRec(Node root) {
    if (root == null)
        return 0;
    return 1 + countNodesRec(root.left) + countNodesRec(root.right);
}
```

📌 Every node contributes **1** to count.

---

# 🍃 7. Count Leaf Nodes

📌 **Why important?**

* Differentiates leaf vs internal nodes
* Common exam sub-question

### 💡 Leaf Condition

```
left == null AND right == null
```

### 📘 Visualization

```
      10
     /  \
    5   20
          \
           30
```

Leaf nodes = **5, 30**

📌 **Total Leaf Nodes = 2**

---


```java
public int countLeafNodes() {
    return countLeafRec(root);
}

private int countLeafRec(Node root) {
    if (root == null)
        return 0;

    if (root.left == null && root.right == null)
        return 1;

    return countLeafRec(root.left) + countLeafRec(root.right);
}
```

📌 Leaf node = no left AND no right child.

---

# ✅ 8. Check if Tree Is a Valid BST

📌 **Very common interview question**

---

## ❌ Wrong Thinking (Students Usually Do This)

> “Check only left < node < right”

🚫 This fails for deeper levels.

---

## ✅ Correct Thinking

Every node must lie in a **valid range**:

```
Left Subtree  < Node < Right Subtree
```

### 📘 Example of INVALID BST

```
      10
     /  \
    5   15
       /
      6   ❌ invalid (6 < 10 but in right subtree)
```

📌 **Why invalid?**

* Right subtree values must be **greater than root**

---

## 🧠 Viva Tip

> “BST validity is checked using range constraints, not just immediate children.”

---


### 💡 Logic

Each node must lie within a valid **range**.

```java
public boolean isValidBST() {
    return isValidBSTRec(root, Integer.MIN_VALUE, Integer.MAX_VALUE);
}

private boolean isValidBSTRec(Node root, int min, int max) {
    if (root == null)
        return true;

    if (root.value <= min || root.value >= max)
        return false;

    return isValidBSTRec(root.left, min, root.value) &&
           isValidBSTRec(root.right, root.value, max);
}
```

📌 **Very common interview question**

---

# 🌊 9. Level Order Traversal 

# 🌳 Example Tree (Keep this in mind)
  
``` 
        50
       /  \
     30    70
    / \    / \
  20  40  60  80

```

---

### 💡 Strategy

1. Find **height of tree**
2. Print nodes **level by level**

### 📘 Visualization

```
Level 1: 10
Level 2: 5 20
Level 3: 3 7 30
```

📌 **Time Complexity:** `O(n)`
📌 **Space Complexity:** `O(h)`

---


## 📏 Height of BST

```java
public int height() {
    return heightRec(root);
}

private int heightRec(Node root) {
    if (root == null)
        return 0;
    return 1 + Math.max(heightRec(root.left), heightRec(root.right));
}
```

---

## 🖨 Print Given Level

```java
private void printLevel(Node root, int remainingDepth) {
    if (root == null)
        return;

    if (remainingDepth == 1)
        System.out.print(root.value + " ");
    else {
        printLevel(root.left, remainingDepth - 1);
        printLevel(root.right, remainingDepth - 1);
    }
}
```

---

## 🌊 Level Order Traversal

```java
public void levelOrderTraversal() {
    int h = height();
    for (int i = 1; i <= h; i++) {
        printLevel(root, i);
        System.out.println();
    }
}
```

---

# 🧪 10. Main Method (Testing Everything)

```java
public static void main(String[] args) {
    BST tree = new BST();

    tree.insert(50);
    tree.insert(30);
    tree.insert(70);
    tree.insert(20);
    tree.insert(40);
    tree.insert(60);
    tree.insert(80);

    System.out.println("Total Nodes: " + tree.countNodes());
    System.out.println("Leaf Nodes: " + tree.countLeafNodes());
    System.out.println("Valid BST: " + tree.isValidBST());

    System.out.println("Level Order Traversal:");
    tree.levelOrderTraversal();

    tree.delete(50);
    System.out.println("After Deleting 50:");
    tree.levelOrderTraversal();
}
```

---

# 🧠 Exam & Viva Power Points

✔ “BST delete has **three cases**”
✔ “Two-child deletion uses **Inorder Successor**”
✔ “BST validation uses **range method**”
✔ “Level order  **height recursion**”

---

# 🏁 Wrap-Up

✅ Recursive thinking strengthened
✅ BST mastery achieved
✅ Interview-ready logic built


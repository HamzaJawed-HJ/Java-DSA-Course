Week 15 –  Final Project

# 🗺️ **DSA Lab – Week 15: HashMap in Java (Overview & Practical Usage)**

---
## 🚀 Let’s Begin!

Welcome back, developers! 👋
This week, we’re exploring a **very powerful and widely used data structure** in Java — **HashMap** 🧠

HashMap is everywhere:

* Login systems
* Counting frequency
* Fast searching
* Real-world applications like databases & caches

📌 **Goal of this lecture:**
👉 Understand **what a HashMap is**,
👉 Learn **how to use it in Java**,
👉 Build a **clear mental model** for future DSA topics.
✅ Clear concepts
✅ Practical usage

---

## 🔹 1. What is a Map?

A **Map** stores data in **Key → Value** pairs.

Think of it like:

| Key (Unique) | Value        |
| ------------ | ------------ |
| Roll No      | Student Name |
| CNIC         | Person       |
| Username     | Password     |
| Word         | Meaning      |

📌 **Important rules:**

* Keys are **unique**
* Values **can repeat**
* Each key maps to **only one value**

---

## 🔹 2. Why Do We Need HashMap?

Let’s think practically:

* **Array** → Access by index only
* **List** → Searching is slow
* **Map** → Access directly using key ⚡

Example:

> “Find marks of roll no 101”

With HashMap:

```
marks.get(101) → O(1) (fast!)

```
---

## Visualization
![Hash Map](assets/2.png)

---


---

## Visualization
![Hash Map](assets/hashmap.jpg)

---


## 🔹 3. What is HashMap?

**HashMap** is a class in Java that implements the **Map interface**.

💡 In one line:

> “HashMap stores key–value pairs and allows very fast access using hashing.”

Internally:

* Uses an **array**
* Converts key → index
* Stores value at that index

(Details handled by Java — don’t worry 😉)

---

## 🔹 4. How HashMap Works (Conceptual Only)

Let’s understand this **step by step**:

1️⃣ You give a **key**
2️⃣ Hash function converts key → number
3️⃣ That number becomes an **array index**
4️⃣ Value is stored at that index
5️⃣ If two keys go to same index → **collision**
6️⃣ Java handles collisions internally

📌 You just need to **use HashMap**, not build it.

---


## 🔹 6. Map Interface in Java

We usually write:

```java
Map<Integer, String> map = new HashMap<>();
```

Why?

* `Map` → interface (flexibility)
* `HashMap` → implementation

📌 This is **good coding practice**.

---

## 🔹 7. Core HashMap Operations (Must Know)

### ➕ Insert Data

```java
map.put(1, "Ali");
map.put(2, "Hamza");
```

* If key already exists → value is updated

---

### 🔍 Access Data

```java
map.get(1);   // returns "Ali"
```

* Returns `null` if key not found

---

### ❌ Remove Data

```java
map.remove(2);
```

---

### ✅ Check Key

```java
map.containsKey(1); // true or false
```

---

### 📏 Size & Empty Check

```java
map.size();
map.isEmpty();
```

---

## 🔹 8. Iterating Through HashMap (Very Important)

### 🔑 Using keySet()

```java
for (Integer key : map.keySet()) {
    System.out.println(key);
}
```

---

### 📦 Using values()

```java
for (String value : map.values()) {
    System.out.println(value);
}
```

---

### 🔗 Using entrySet() (Best Way)

```java
for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " → " + entry.getValue());
}
```

📌 Most commonly used in real projects.

---

## 🔹 10. HashMap Properties (Quick View)

| Feature          | HashMap          |
| ---------------- | ---------------- |
| Order            | Not guaranteed   |
| Duplicate Keys   | ❌                |
| Duplicate Values | ✅                |
| Null Key         | 1 allowed        |
| Null Values      | Multiple allowed |
| Speed            | Very fast        |

---

## 🔹 11. HashMap vs Array vs List

| Feature        | Array   | List        | HashMap   |
| -------------- | ------- | ----------- | --------- |
| Access         | Index   | Slow search | Key-based |
| Flexibility    | Low     | Medium      | High      |
| Searching      | ❌       | ❌           | ✅         |
| Real-world use | Limited | Medium      | Very High |

---

## 🔹 12. When Should You Use HashMap?

✅ Fast lookup required
✅ Key-value relationship
✅ Frequency counting
✅ Caching data
✅ Avoid duplicate keys

---

## 🎯 Summary

* HashMap stores **key → value**
* Very fast data access
* Easy to use
* Widely used in industry
* No need to worry about internals now

---

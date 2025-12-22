# 🚀 DSA Lab – Class 11 : Searching Algorithms with Recursion  

# 🔍 **Linear Search – Recursive Approach**

## 💡 **Explanation**

Instead of using a loop, we use **recursion** to check elements one by one.

Each recursive call checks:

```
arr[index] == target ?
```

If not found → move to the next index:

```
linearSearchRec(arr, target, index + 1)
```

Stops when:

* Element is found → return index
* Index reaches array length → return -1

---

# 🧩 **Java Code – Recursive Linear Search**

```java
public class LinearSearchRecursive {

    // Recursive function
    public static int linearSearchRec(int[] arr, int target, int index) {

        // base case: index out of range
        if(index == arr.length) {
            return -1;   // not found
        }

        // check current element
        if(arr[index] == target) {
            return index;
        }

        // recursive call for next index
        return linearSearchRec(arr, target, index + 1);
    }

    // Main function
    public static void main(String[] args) {

        int[] arr = {5, 12, 7, 25, 3};
        int target = 25;

        int result = linearSearchRec(arr, target, 0);

        if(result == -1)
            System.out.println("Element not found");
        else
            System.out.println("Found at index: " + result);
    }
}
```

---

# 📊 **Complexity**

| Case    | Time | Space               |
| ------- | ---- | ------------------- |
| Best    | O(1) | O(n) (stack height) |
| Worst   | O(n) | O(n)                |
| Average | O(n) | O(n)                |

**Note:** Space is O(n) because each recursive call remains in call stack.

---



# 🔹 1.2.2 Binary Search (Recursive)

## 💻 Code

```java
public static int binarySearchRecursive(int[] arr, int low, int high, int target) {

    if(low > high) return -1;

    int mid = (low + high) / 2;

    if(arr[mid] == target) return mid;

    if(target < arr[mid])
        return binarySearchRecursive(arr, low, mid - 1, target);

    return binarySearchRecursive(arr, mid + 1, high, target);
}
```

---

# 🎓 Wrap-Up

🎉 Today you learned:

✔ Linear Search
✔ Binary Search ( Recursive)
✔ When to use which search
✔ What recursion is
✔ How call stack works
✔ Classic recursion problems
✔ Complete practice set

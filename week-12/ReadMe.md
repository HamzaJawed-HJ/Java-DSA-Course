## Week 12 – Quik sort & merge Sort

## ⚡ 6️⃣ Merge Sort

**🧠 Concept + When to Use:**
Merge Sort uses **Divide and Conquer** — divides the array into halves, sorts them, and merges back.
✅ Efficient & Stable
✅ Used by big techs like **Java’s Arrays.sort() for Objects**

**📈 Time Complexity:** O(n log n)
**📦 Space Complexity:** O(n)

---

## Visualization
![Merge Sort](assets/1.jpg)

---

---

## Visualization
![Merge Sort](assets/Merge-sort-example.gif)

---

### ✍️ Pseudocode (in English)

* Divide array into two halves
* Recursively sort each half
* Merge sorted halves into one

---

### 💻 Java Example

```java
import java.util.Arrays;

public class MergeSort {
   
    // This function divides the array into smaller subarrays
    // using the Divide & Conquer approach (Merge Sort)
    public static void divide(int arr[], int si, int ei) {

        // Base case:
        // If the starting index is greater than or equal to ending index,
        // it means the array has 0 or 1 element, which is already sorted
        if (si >= ei) {
            return;
        }

        // Find the middle index to divide the array into two halves
        // This formula avoids integer overflow
        int mid = si + (ei - si) / 2;

        // Recursively divide the left half
        divide(arr, si, mid);

        // Recursively divide the right half
        divide(arr, mid + 1, ei);

        // Merge the two sorted halves
        conquer(arr, si, mid, ei);
    }


    // This function merges two sorted subarrays into one sorted array
    public static void conquer(int arr[], int si, int mid, int ei) {

        // Create a temporary array to store merged elements
        int merged[] = new int[ei - si + 1];

        // idx1 points to the start of the left subarray
        int idx1 = si;

        // idx2 points to the start of the right subarray
        int idx2 = mid + 1;

        // x is the index for the merged array
        int x = 0; 

        // Compare elements from both subarrays
        // and store the smaller one into merged array
        while (idx1 <= mid && idx2 <= ei) {

            if (arr[idx1] <= arr[idx2]) {
                merged[x++] = arr[idx1++];
            } else {
                merged[x++] = arr[idx2++];
            }
        }

        // Copy remaining elements of left subarray (if any)
        while (idx1 <= mid) {
            merged[x++] = arr[idx1++];
        }

        // Copy remaining elements of right subarray (if any)
        while (idx2 <= ei) {
            merged[x++] = arr[idx2++];
        }

        // Copy the merged sorted elements back into the original array
        for (int i = 0, j = si; i < merged.length; i++, j++) {
            arr[j] = merged[i];
        }
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 4, 1};
        mergeSort(arr, 0, arr.length - 1);
        System.out.println("Sorted Array: " + Arrays.toString(arr));
    }
}
```

**🖥️ Output:**
`Sorted Array: [1, 3, 4, 5]`

---

## ⚡ 7️⃣ Quick Sort

**🧠 Concept + When to Use:**
Quick Sort picks a **pivot** and partitions the array around it.
💼 **Used by** Google, Facebook, Amazon — highly efficient for in-memory sorting!
❌ Not stable but very efficient for large datasets

These big tech companies (like Google, Facebook, Amazon) use these sorting algorithms 
**(especially Quick Sort and Merge Sort)** or their optimized variants inside their real-world systems

* In databases
* In search engines
* In large-scale data pipelines
* In built-in sorting libraries (like Java’s Arrays.sort() or Python’s sorted())


**📈 Time Complexity:** O(n log n)
**📦 Space Complexity:** O(log n)

---

---

## Visualization
![Quick Sort](assets/Quick_Sort.png)

---


### ✍️ Pseudocode (in English)

* Choose a pivot element
* Place smaller elements on the left
* Place larger ones on the right
* Recursively apply to left and right parts

---

### 💻 Java Example

```java
import java.util.Arrays;

public class QuickSort {
    static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
           
            int pi = partition(arr, low, high);
            
            // Left half
            quickSort(arr, low, pi - 1);
            
            // Right half
            quickSort(arr, pi + 1, high);
        }
    }

    static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int idx = (low - 1);
       
         // Traverse elements and place smaller elements on left side
        for (int j = low; j < high; j++) {
            if (arr[j] < pivot) {
                idx++;
          
                swap(arr, j, idx);
            }
        }

        // Place pivot at its correct position
        idx++;
        swap(arr, end, idx);

        return idx;
    }

     // Swap function
    public static void swap(int arr[], int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 4, 1};
        quickSort(arr, 0, arr.length - 1);
        System.out.println("Sorted Array: " + Arrays.toString(arr));
    }
}
```

**🖥️ Output:**
`Sorted Array: [1, 3, 4, 5]`

---



    
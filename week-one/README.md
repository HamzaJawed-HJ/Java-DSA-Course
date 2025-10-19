
# 🚀 DSA Lab – Class 1: Java Revision

### 🧑‍🏫 Welcome to Your First DSA Lab!
Hey everyone 👋 Welcome to the very first **Data Structures & Algorithms (DSA)** lab session!  
Before we dive into complex structures like stacks, queues, and trees — we’ll first **refresh your core Java skills**.  

By the end of today’s class, you’ll feel confident writing and running clean Java programs 💪  

---

## 🎯 Lab Objectives
✅ Revise essential Java concepts from previous semester  
✅ Practice programming logic through examples  
✅ Get comfortable with IntelliJ and Java I/O  
✅ Build a strong base for DSA topics  

---

## ⚙️ Setting Up
Make sure you’ve:
- Installed **IntelliJ IDEA**
- Configured the **JDK (Java 21 or above)**
- Created a simple project named `DSA_Lab1`

Now create a file: `Main.java`

---

## 🔹 1. Variables & Data Types

### 💡 Explanation
Variables are containers that store data.  
Every variable has:
1. **Type** – defines what kind of data it stores  
2. **Name** – how you refer to it  
3. **Value** – the data inside it  

Java’s **primitive data types** are:
| Type | Size | Example |
|------|------|----------|
| int | 4 bytes | 10 |
| double | 8 bytes | 45.6 |
| char | 2 bytes | 'A' |
| boolean | 1 bit | true/false |
| String | (non-primitive) | "Hamza" |

---

### 💻 Example
```java
public class Main {
    public static void main(String[] args) {
        int age = 21;
        double gpa = 3.75;
        char grade = 'A';
        boolean passed = true;
        String name = "Hamza";

        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("GPA: " + gpa);
        System.out.println("Grade: " + grade);
        System.out.println("Passed: " + passed);
    }
}
````

### 🖥️ Output

```
Name: Hamza
Age: 21
GPA: 3.75
Grade: A
Passed: true
```

---

### 🧠 Practice

1. Declare variables for your name, rollNo, and department. Print them together in one line.
2. Create a variable for Celsius temperature and convert it to Fahrenheit.

---

### ✅ Solution (Q2)

```java
public class Main {
    public static void main(String[] args) {
        double celsius = 25.0;
        double fahrenheit = (celsius * 9/5) + 32;
        System.out.println("Temperature in Fahrenheit: " + fahrenheit);
    }
}
```

---

## 🔹 2. Basic Input / Output

### 💡 Explanation

To take user input in Java, we use the **Scanner** class.

```java
import java.util.Scanner;
```

This allows us to read from the console.

---

### 💻 Example

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = sc.nextLine();

        System.out.print("Enter your age: ");
        int age = sc.nextInt();

        System.out.println("Welcome " + name + "! You are " + age + " years old.");
    }
}
```

### 🖥️ Output

```
Enter your name: Hamza
Enter your age: 21
Welcome Hamza! You are 21 years old.
```

---

### 🧠 Practice

1. Take two integers as input and print their sum.
2. Take a name and marks as input, then print: `"Hello <name>, your marks are <marks>"`.

---

### ✅ Solution (Q1)

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter first number: ");
        int a = sc.nextInt();
        System.out.print("Enter second number: ");
        int b = sc.nextInt();
        System.out.println("Sum = " + (a + b));
    }
}
```

---

## 🔹 3. Conditional Statements

### 💡 Explanation

Conditional statements let programs **decide** what to do.

#### Syntax:

```java
if (condition) {
    // code
} else if (condition2) {
    // code
} else {
    // code
}
```

---

### 💻 Example

```java
public class Main {
    public static void main(String[] args) {
        int num = 7;

        if (num > 0) {
            System.out.println("Positive");
        } else if (num < 0) {
            System.out.println("Negative");
        } else {
            System.out.println("Zero");
        }
    }
}
```

### 🖥️ Output

```
Positive
```

---

### 🧠 Practice

1. Check if a number is even or odd.
2. Take three numbers and print the largest one.

---

### ✅ Solution (Q1)

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int n = sc.nextInt();

        if (n % 2 == 0)
            System.out.println("Even");
        else
            System.out.println("Odd");
    }
}
```

---

## 🔹 4. Loops

### 💡 Explanation

Loops repeat a block of code multiple times.

#### Types:

1. `for` loop → known number of iterations
2. `while` loop → runs while condition is true
3. `do-while` loop → runs at least once

---

### 💻 Example – For Loop

```java
public class Main {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println("Count: " + i);
        }
    }
}
```

### 🖥️ Output

```
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
```

---

### Examples
```java
// for
for (int i = 1; i <= 10; i++) { System.out.println(i); }

// while
int i = 1;
while (i <= 10) { System.out.println(i); i++; }

// do-while
int j = 1;
do { System.out.println(j); j++; } while (j <= 10);
```
---

### 🧠 Practice

1. Print all numbers from 1 to 10.
2. Print the multiplication table of any number (user input).

---

### ✅ Solution (Q2)

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number: ");
        int num = sc.nextInt();

        for (int i = 1; i <= 10; i++) {
            System.out.println(num + " x " + i + " = " + (num * i));
        }
    }
}
```

---

## 🔹 5. Arrays

### 💡 Explanation

Arrays store **multiple values of the same type** in one variable.

#### Syntax:

```java
int[] numbers = {10, 20, 30, 40};
```

---

### 💻 Example

```java
public class Main {
    public static void main(String[] args) {
        int[] marks = {85, 90, 78, 92, 88};

        int sum = 0;
        for (int i = 0; i < marks.length; i++) {
            sum += marks[i];
        }

        double average = (double) sum / marks.length;
        System.out.println("Average Marks = " + average);
    }
}
```

### 🖥️ Output

```
Average Marks = 86.6
```

---

### 🧠 Practice

1. Store 5 integers and find their maximum.
2. Print array elements in reverse order.

---

### ✅ Solution (Q1)

```java
public class Main {
    public static void main(String[] args) {
        int[] arr = {10, 22, 5, 40, 18};
        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > max)
                max = arr[i];
        }
        System.out.println("Maximum = " + max);
    }
}
```

---

## 🔹 6. Functions (Methods)

### 💡 Explanation

Functions (methods) let us reuse code and make programs organized.

#### Syntax:

```java
returnType functionName(parameters) {
    // body
    return value;
}
```

---

### 💻 Example

```java
public class Main {
    public static void main(String[] args) {
        int result = addNumbers(5, 10);
        System.out.println("Sum = " + result);
    }

    public static int addNumbers(int a, int b) {
        return a + b;
    }
}
```

### 🖥️ Output

```
Sum = 15
```

---

### 🧠 Practice

1. Write a method to find factorial of a number.
2. Write a method to check if a number is prime.

---

### ✅ Solution (Q1)

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Factorial = " + factorial(5));
    }

    public static int factorial(int n) {
        int fact = 1;
        for (int i = 1; i <= n; i++) {
            fact *= i;
        }
        return fact;
    }
}
```

---

## 🔹 7. Basics of OOP

### 💡 Explanation

Java is **Object-Oriented** — everything revolves around **classes** and **objects**.

* **Class:** Blueprint
* **Object:** Real-world instance of class
* **Constructor:** Initializes object values
* **Method:** Defines behavior

---

### 💻 Example

```java
class Student {
    String name;
    int rollNo;

    Student(String n, int r) {
        name = n;
        rollNo = r;
    }

    void displayInfo() {
        System.out.println("Name: " + name + ", Roll No: " + rollNo);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Ali", 101);
        s1.displayInfo();
    }
}
```

### 🖥️ Output

```
Name: Ali, Roll No: 101
```

---

### 🧠 Practice

Create a `Car` class with:

* brand, model, and price
* `displayDetails()` method
  Then create two car objects and print their details.

---

### ✅ Solution

```java
class Car {
    String brand;
    String model;
    double price;

    Car(String b, String m, double p) {
        brand = b;
        model = m;
        price = p;
    }

    void displayDetails() {
        System.out.println("Brand: " + brand + ", Model: " + model + ", Price: $" + price);
    }
}

public class Main {
    public static void main(String[] args) {
        Car c1 = new Car("Toyota", "Corolla", 28000);
        Car c2 = new Car("Honda", "Civic", 31000);
        c1.displayDetails();
        c2.displayDetails();
    }
}
```

---

## 🏁 Final Mini Challenge

Write a program that:

1. Takes marks of 5 subjects as input.
2. Calculates total, average, and grade using if-else.

**Hint:** Use arrays + loops + conditionals.



## 🎓 Wrap-Up

✅ You revised:

* Variables & Data Types
* Input / Output
* Conditionals
* Loops
* Arrays
* Functions
* OOP Basics

Next class → **Arrays & Functions in DSA** 🚀

Keep coding and experimenting 💻✨

```

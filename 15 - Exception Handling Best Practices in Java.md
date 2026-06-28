# 15 - Exception Handling Best Practices in Java

## 1. Introduction

Exception handling is not only about catching errors.
It is also about writing code that is clear, safe, and maintainable.
Following best practices helps developers avoid common mistakes.

## 2. Best Practices

1. Catch specific exceptions instead of using a generic one.
2. Do not ignore exceptions.
3. Always close resources using finally or try-with-resources.
4. Use meaningful exception messages.
5. Avoid catching exceptions just to print them.
6. Do not use exceptions for normal control flow.
7. Handle exceptions at the right level.
8. Log exceptions properly.
9. Keep try blocks small.
10. Prefer checked exceptions for recoverable problems.

## 3. Example of Good Practice

### Program:

> **Error Correction:** The resource assignment `BufferedReader reader  new BufferedReader(...)` and string assignment `String line  reader.readLine();` were missing the assignment operator (`=`). This has been corrected below.

```java
import java.io.*;

public class BestPracticeExample {
    public static void main(String[] args) {
        try (BufferedReader reader = new BufferedReader(new FileReader("data.txt"))) {
            String line = reader.readLine();
            System.out.println(line);
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
    }
}

```

### Explanation:

* The try-with-resources statement automatically closes the file using the assignment operator (`=`).
* The catch block handles only the relevant exception.
* The code is cleaner and safer.

## 4. Example of Bad Practice

### Program:

> **Error Correction:** The variable initialization line `int x  10 / 0;` was missing the assignment operator (`=`). This has been corrected below.

```java
try {
    int x = 10 / 0;
} catch (Exception e) {
    System.out.println(e);
}

```

### Why this is bad:

* It catches too broad an exception (`Exception` class instead of `ArithmeticException`).
* It hides the real issue.
* It is less clear and less professional.

## 5. Summary

Good exception handling means being specific, clear, and responsible.
It helps preserve program stability and makes debugging easier.

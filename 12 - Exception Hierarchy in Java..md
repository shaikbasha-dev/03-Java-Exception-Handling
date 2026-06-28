# 12 - Exception Hierarchy in Java

## 1. Introduction

Java exceptions are organized in a hierarchy.
At the top is the `Throwable` class.
All exception and error classes inherit from it.

## 2. Main Hierarchy

```
Throwable
├── Error
│   ├── OutOfMemoryError
│   └── StackOverflowError
└── Exception
    ├── Checked Exceptions
    │   ├── IOException
    │   ├── SQLException
    │   └── FileNotFoundException
    └── Unchecked Exceptions (RuntimeException)
        ├── ArithmeticException
        ├── NullPointerException
        ├── ArrayIndexOutOfBoundsException
        └── IllegalArgumentException

```

## 3. Explanation of the Hierarchy

* **Throwable** is the root class for all exceptions and errors.
* **Error** represents serious problems that are usually not handled by the application.
* **Exception** represents conditions that a program can catch and handle.
* **RuntimeException** is a subclass of Exception and represents unchecked exceptions.

## 4. Difference Between Error and Exception

### Error:

* Serious system-level problem
* Usually not recoverable
* Example: `OutOfMemoryError`

### Exception:

* Problem that can often be handled by the program
* Example: `IOException`, `ArithmeticException`

## 5. Example Program

### Program:

> **Error Correction:** The variable initialization line `int result  10 / 0;` was missing the assignment operator (`=`). This has been corrected below.

```java
public class ExceptionHierarchyExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;
            System.out.println(result);
        } catch (ArithmeticException e) {
            System.out.println("Caught ArithmeticException");
        }
    }
}

```

### Explanation:

* `ArithmeticException` is a subclass of `RuntimeException`.
* `RuntimeException` is a subclass of `Exception`.
* `Exception` is a subclass of `Throwable`.

### Output:

```
Caught ArithmeticException

```

## 6. Important Points

* All exceptions inherit from `Throwable`.
* Errors are generally not meant for normal handling.
* `RuntimeException` and its subclasses are unchecked exceptions.
* Checked exceptions are subclasses of `Exception` but not `RuntimeException`.

## 7. Conclusion

The Java exception hierarchy helps in understanding how different errors are related.
It shows why some exceptions are checked, some are unchecked, and why some problems are serious enough to be treated as errors.

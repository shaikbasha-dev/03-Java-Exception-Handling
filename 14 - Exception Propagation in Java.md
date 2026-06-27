14 - Exception Propagation in Java


1. Introduction

Exception propagation means that when an exception occurs in one method, it is passed to the calling method if it is not handled there.
This process continues upward through the call stack until the exception is handled or the program stops.

------------------------------------------------------------
2. Concept of Propagation
------------------------------------------------------------
If a method throws an exception and does not catch it, the exception moves to the method that called it.
That caller can either handle the exception or pass it further up.

Example flow:
main() -> method1() -> method2()

If method2 throws an exception:
- method2 tries to handle it
- if not handled, it goes to method1
- if method1 also does not handle it, it goes to main
- if main does not handle it, the program terminates

------------------------------------------------------------
3. Example Program

Program:
public class ExceptionPropagationExample {
    static void method1() {
        method2();
    }

    static void method2() {
        int result  10 / 0;
        System.out.println(result);
    }

    public static void main(String[] args) {
        try {
            method1();
        } catch (ArithmeticException e) {
            System.out.println("Exception handled in main.");
        }
    }
}

Explanation:
- method2() throws ArithmeticException.
- method2() does not catch it, so it is propagated to method1().
- method1() also does not catch it, so it reaches main().
- main() catches the exception and handles it.

Output:
Exception handled in main.

------------------------------------------------------------
4. Important Points
------------------------------------------------------------
- Exception propagation happens automatically for unchecked exceptions.
- For checked exceptions, the method must either catch them or declare them with throws.
- Propagation continues until the exception is handled.
- If not handled, the program terminates.

------------------------------------------------------------
5. Conclusion

Exception propagation is the process of passing an exception upward through the call stack.
Understanding propagation helps developers know where to place try-catch blocks and how exceptions flow in a program.

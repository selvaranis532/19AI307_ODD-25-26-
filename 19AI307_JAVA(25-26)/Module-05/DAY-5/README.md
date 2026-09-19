# Ex.No:5(E) MULTITHREADING -SYNCHRONIZATION

## QUESTION:
Maintain two int variables a and b, read their initial values from user. Use synchronized block to swap them and print swapped values.

## AIM:
To write a Java program that reads two integers from the user and swaps their values using a synchronized block to ensure thread-safe operations.

## ALGORITHM :
1. Read two integer values a and b from the user.

2. Create a lock object to use inside the synchronized block.

3. Enter the synchronized block using the lock object.

4. Swap the values of a and b using a temporary variable.

5. Exit the synchronized block once the swap is complete.

6. Print the swapped values of a and b.

7. Close the scanner.





## PROGRAM:
 ```
/*
Program to implement a Synchronization concept using Java
Developed by: SELVARANI S
RegisterNumber: 212224040301
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class SwapUsingSynchronized {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        Object lock = new Object();

        synchronized (lock) {
            int temp = a;
            a = b;
            b = temp;
        }

        System.out.println("a = " + a);
        System.out.println("b = " + b);
        sc.close();
    }
}
```


## OUTPUT:
<img width="457" height="390" alt="image" src="https://github.com/user-attachments/assets/2fb44153-47e4-4ac3-8872-e321e221fc56" />



## RESULT:
Therefore the program successfully swaps two integers within a synchronized block, ensuring safe and controlled access.






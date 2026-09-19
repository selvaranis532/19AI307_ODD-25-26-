Ex.No:5(A) INPUTSTREAMREADER
QUESTION:
Write a program to demonstrate chaining of streams (BufferedReader on top of InputStreamReader on top of System.in)

AIM:
To write a Java program that demonstrates stream chaining by placing a BufferedReader on top of an InputStreamReader, which in turn wraps System.in, and then reading user input using this chained stream.

ALGORITHM :
Create a BufferedReader object by chaining:

System.in → InputStreamReader → BufferedReader.

Inside a try block Use readLine() to read the user's name.

Use readLine() again to read the user's age.

Print the collected details.

Catch any IOException and display an appropriate error message.

PROGRAM:
/*
Program to implement a InputStreamReader using Java
Developed by: SELVARANI S
RegisterNumber: 212224040301
*/
SOURCE CODE:
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class ChainingStreamsExample {
    public static void main(String[] args) {
        // Chaining: System.in -> InputStreamReader -> BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        try {
            String name = br.readLine();
            String age = br.readLine();
            System.out.println("--- User Details ---");
            System.out.println("Name: " + name);
            System.out.println("Age: " + age);
        } catch (IOException e) {
            System.out.println("An error occurred: " + e.getMessage());
        }
    }
}
OUTPUT:
image
RESULT:
Therefore the program successfully demonstrates chaining of input streams by reading user data through a BufferedReader wrapped over an InputStreamReader.

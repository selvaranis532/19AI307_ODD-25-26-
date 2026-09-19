Ex.No:5(B) SERIALIZATION AND DESERIALIZATION
QUESTION:
Write a Java program to serialize a collection of objects (like ArrayList) into a file.

AIM:
To write a Java program that serializes a collection of Student objects (ArrayList) into a file and deserializes it back, demonstrating object persistence using Java Serialization.

ALGORITHM :
Create a Student class and implement the Serializable interface.

Store id, name, and marks as attributes and override toString() for readable output.

Read the number of students from the user.

For each student, read id, name, and marks and add them to an ArrayList.

Implement serializeStudents() to create an ObjectOutputStream over a FileOutputStream.

Write the list of students into the file.

Implement deserializeStudents() to create an ObjectInputStream over a FileInputStream, read the list back into memory.

Print the deserialized student objects to verify successful serialization and deserialization.

Close the scanner.

PROGRAM:
/*
Program to implement a Serialization and Deserialization using Java
Developed by: SELVARANI S
RegisterNumber: 212224040301
*/
SOURCE CODE:
import java.io.*;
import java.util.*;

// Student class must implement Serializable
class Student implements Serializable {
    private static final long serialVersionUID = 1L;

    private int id;
    private String name;
    private double marks;

    public Student(int id, String name, double marks) {
        this.id = id;
        this.name = name;
        this.marks = marks;
    }

    @Override
    public String toString() {
        return "Student{id=" + id + ", name='" + name + "', marks=" + marks + "}";
    }
}

public class StudentSerializationUserInput {

    // Serialize list of students
    public static void serializeStudents(List<Student> students, String fileName) {
        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(fileName))) {
            oos.writeObject(students);
            System.out.println("Students serialized successfully into: " + fileName);
        } catch (IOException e) {
            System.out.println("Error during serialization: " + e.getMessage());
        }
    }

    // Deserialize list of students
    @SuppressWarnings("unchecked")
    public static List<Student> deserializeStudents(String fileName) {
        List<Student> students = null;
        try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream(fileName))) {
            students = (List<Student>) ois.readObject();
            System.out.println("Students deserialized successfully from: " + fileName);
        } catch (IOException | ClassNotFoundException e) {
            System.out.println("Error during deserialization: " + e.getMessage());
        }
        return students;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<Student> students = new ArrayList<>();

        int n = scanner.nextInt();
        scanner.nextLine(); // consume newline

        for (int i = 0; i < n; i++) {
            int id = scanner.nextInt();
            scanner.nextLine();
            String name = scanner.nextLine();
            double marks = scanner.nextDouble();
            if (i < n - 1) scanner.nextLine(); // consume newline
            students.add(new Student(id, name, marks));
        }

        String fileName = "students.dat";
        serializeStudents(students, fileName);

        List<Student> deserializedStudents = deserializeStudents(fileName);

        if (deserializedStudents != null) {
            System.out.println("\nDeserialized Students:");
            for (Student s : deserializedStudents) {
                System.out.println(s);
            }
        }

        scanner.close();
    }
}
OUTPUT:
image
RESULT:
Therfor the program successfully serializes an ArrayList of Student objects into a file and restores them through deserialization.
